# Módulos da Retaguarda (TOTVS Chef Web / Gestão Web)

Detalhamento funcional do back-office web. Nomenclatura segue a documentação
oficial (TDN, espaço TChef, e artigos "TC - CW - ..." da Central de
Atendimento).

## 1. Cadastros

### Produtos
- Cadastro com código, nome/descrição, grupo e subgrupo, unidade de medida,
  código de barras, custo e preço de venda.
- **Código auxiliar**: múltiplos códigos por produto para facilitar
  lançamento no PDV.
- **Inativação de produto**: produto inativo deixa de aparecer em Inventário,
  Saída de Almoxarifado, Transferência entre Estoques e Entrada de
  Mercadorias.
- Alteração de preços com vigência por data; campos "Preço Venda" e
  "Preço Venda 2".
- **Importação por planilha Excel** para cadastro em massa de produtos.
- Geração de etiquetas de código de barras.
- Replicação de produtos para franquias (com seleção apenas de novos itens).

### Grupos e subgrupos
- Estrutura hierárquica de categorização usada em relatórios, filtros e kits.

### Ficha técnica / Composição (engenharia de cardápio)
- Composição detalhada de produtos compostos: insumos e quantidades por
  unidade do produto final.
- Base do **CMV teórico** e da baixa automática de estoque na venda.
- Manutenção individual ("Consultar/Adicionar/Remover Composição do
  Produto") ou em massa via **importação de planilha de composições**.
- Replicação de receitas entre lojas.

### Kits e combos
- Conjuntos pré-definidos de produtos com quantidades específicas e preço
  único (preço do produto principal).
- Venda em balcão, cartão e delivery; categorias para agrupamento.
- Sincronizam com plataformas de pedidos online.

### Complementos e observações
- **Complementos/adicionais**: produtos vendidos junto a outro (ex.: borda
  recheada, queijo extra), com preço próprio; expostos na API ObterCardapio.
- **Observações de pedido**: instruções de preparo capturadas no atendimento
  e no delivery.

### Tabelas de preço e cardápios
- Precificação múltipla (ex.: salão x delivery) e por período.
- Sincronização de cardápio com plataformas de delivery (iFood, Uber Eats).

### Clientes, fornecedores, funcionários
- **Clientes**: dados para fidelidade, histórico de consumo e delivery.
- **Fornecedores** ("TC - CW - Cadastro de Fornecedor"): razão social,
  CNPJ/CPF, contato, condições de pagamento, histórico de compras.
- **Funcionários e usuários multi-loja** ("TC - CW - Cadastro de Funcionário
  e usuário MultiLoja"): dados, cargo, status e lojas de acesso.

### Perfis e direitos de acesso
- "TC - CW - DIREITOS DE ACESSO": permissões granulares por módulo e
  operação (leitura/inclusão/alteração/exclusão).
- Permissões operacionais específicas: **Realizar Sangria**, **Realizar
  Suprimento**, **NF-e Manifestar**, **Autorizar Download XML NFe/NFCe**.
- Perfis típicos: administrador, gerente, supervisor, operador, contador.

## 2. Estoque

### Movimentações
- **Entrada de mercadorias**: manual ou por **importação de XML de NF-e**
  ("TC - CW - ENTRADA DE MERCADORIAS COM IMPORTAÇÃO DE ARQUIVO XML");
  suporta fator de conversão entre unidade de compra e de venda; gera
  lançamentos em contas a pagar.
- **Saída de almoxarifado**: retirada para produção/consumo interno.
- **Transferência entre lojas/estoques** (produtos inativos são bloqueados).
- **Perdas e desperdícios**: movimentação específica, com impacto no CMV.
- Produção de produtos compostos com baixa automática de insumos.
- Controle de lote/validade na entrada de mercadorias (novidade 2024).

### Inventário (contagem física)
- Fichas de inventário, digitação de contagens e situação das fichas.
- **Importação de planilha Excel** para contagem ("TC - CW - Inventário com
  Importação de Planilha Excel").
- Divergências teórico x físico, com ajuste de estoque após aprovação.

### Manifestação do destinatário (MD-e)
- Busca notas emitidas contra o CNPJ direto no servidor da SEFAZ.
- Eventos: Confirmação da Operação, Ciência da Operação, Desconhecimento,
  Operação não Realizada (justificativa obrigatória de 15–225 caracteres).
- Faz a entrada da mercadoria e o lançamento financeiro em contas a pagar a
  partir do XML.

### CMV — Custo de Mercadoria Vendida
- **CMV teórico**: somatório (quantidade vendida × custo dos insumos da ficha
  técnica). Referência: "TC - CW - COMO FUNCIONA O CMV".
- Comparação teórico x real revela perdas, desvios e falhas de ficha técnica.
- Devoluções reduzem o custo apurado.

## 3. Financeiro

### Plano de contas
- Menu: **Retaguarda > Financeiro > Plano de Contas**.
- Dois níveis: **contas sintéticas** (consolidação, sem lançamentos) e
  **contas analíticas** (recebem lançamentos).
- Base da classificação do DRE (grupos DRE).

### Contas a pagar
- Lançamento automático a partir das entradas de mercadoria/compras.
- **Calendário de contas a pagar** com vencimentos e alertas.
- Entrada manual de contas ("TC - CW - Entrada Manual de conta no Livro
  Caixa e Contas a pagar").

### Contas a receber
- Lançamento automático a partir das vendas; **Calendário de Recebimentos**.

### Fluxo de caixa e livro caixa
- Entradas e saídas consolidadas, projeções e saldos por período.
- Livro caixa com histórico completo e lançamentos manuais.

### Fechamento, sangria e suprimento
- **Sangria** (retirada de dinheiro do caixa) e **suprimento** (entrada para
  troco) controlados por permissão e considerados no fechamento.
- **Conciliação de Caixa** (menu Financeiro > Conciliação de Caixa): confronta
  o fechamento dos caixas com as formas de pagamento registradas.
- Relatório 144 lista caixas conciliados.

### Conciliação de cartões e bancária
- Conciliação de recebíveis de cartão (débito/crédito) com extratos das
  operadoras; controle de tarifas cobradas x contratadas.
- **Conciliação bancária via importação de arquivo OFX**.
- Cadastro de cartões/operadoras com taxas e prazos.

### DRE — Demonstrativo de Resultado do Exercício
- Receita bruta → deduções → receita líquida → CMV → lucro bruto → despesas
  operacionais/administrativas → resultado líquido.
- Customizável (grupos DRE ligados ao plano de contas), comparativo entre
  períodos e entre lojas; exportação Excel/PDF.

### Painel do contador
- Visão das informações financeiras/fiscais para a contabilidade; opção de
  autorizar download de XML de NF-e/NFC-e pelo contabilista.

## 4. Fiscal

| Documento | Uso |
|---|---|
| **NFC-e** | Venda ao consumidor; emissão automática no PDV; contingência com série/numeração específica |
| **SAT / CF-e (modelo 59)** | Estados que adotam SAT (ex.: SP, CE); equipamento autenticador local, sem conexão direta com a SEFAZ no momento da venda |
| **NF-e** | Operações B2B e recepção de notas de fornecedores (entrada via XML) |
| **SPED** | Escrituração digital — bloco C inclui documentos modelo 59; SPED Contribuições (leiaute 019 obrigatório desde jan/2025) |

- Classificação fiscal por produto: **NCM**, **CFOP**, **CST** (cadastro de
  dados fiscais de venda — artigo "TC - CW - CADASTRO/ALTERAÇÃO DE DADOS
  FISCAIS DE VENDA").
- Para NFC-e: requer **Fiscal Manager** e certificado digital instalados;
  XMLs guardados em pasta de custódia.
- Para SAT: ativação prévia via aplicativo do fabricante; código de ativação
  do cliente.
- Cancelamento/estorno de cupons, controle de série e numeração.
- Envio de cupom fiscal por e-mail ao cliente (SAT — SP e CE).

## 5. Relatórios e indicadores

Relatórios numerados do Chef Web (referência usada pelo suporte):

| Nº | Relatório | Conteúdo |
|---|---|---|
| 1 | Venda de Produtos | Vendas com filtros por grupo, subgrupo, fornecedor, período, loja, caixa |
| 35 | PIVOT — Análise de Vendas | Análise cruzada customizável (produto, categoria, período, operação) |
| 63 | Dashboard Vendas por Tipo de Operação | Pré-pago, pós-pago, encomenda, tablet na mesa, delivery |
| 65 | Cupons | Documentos fiscais emitidos (ECF/PED/CNFM/NF-e/NFC-e/SAT) |
| 144 | Caixas Conciliados | Status de conciliação dos caixas |
| 175 | Vendas Diárias de Produtos | Movimento diário por produto, com coluna de ticket médio |

Outros indicadores e análises:
- **Ticket médio** (geral e por setor), vendas por garçom, por forma de
  pagamento, histórico de clientes.
- **Curva ABC** de vendas, compras e fornecedores (filtros por período e
  corte percentual).
- Fechamento de Caixa por Operador (Retaguarda > Relatório e Consultas >
  Vendas).
- Dashboards em tempo real (faturamento diário/semanal/mensal, ranking de
  lojas) com acesso mobile (app Gestão de Vendas by Retail).

## 6. Promoções e fidelidade

- **Promoções**: redução de preço, desconto em valor ou percentual,
  "compre e ganhe"; vigência por período e aplicação seletiva a produtos.
- **Fidelidade**: cadastros de bônus/pontos, grupos de clientes, modelos de
  voucher e produtos elegíveis.
- Integração nativa com **Fidelimax** (pontuação automática das vendas pagas,
  sincronização a cada ~30 minutos, cadastro automático de clientes).

## 7. Modelos de atendimento configuráveis (visão retaguarda)

- Pré-pago, pós-pago, encomenda, tablet na mesa.
- Gestão de reserva de mesa e fila de espera; venda de ingresso.
- Parâmetro "Não permitir lançamento manual de itens pesáveis" (balcão/mesa/
  cartão touch).
