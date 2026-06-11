# Chef PDV e Frente de Loja

Componentes de atendimento da Linha Chef: PDV (frente de caixa), comanda
eletrônica Android, autoatendimento, cardápio digital e KDS.

## 1. Chef PDV — Frente de Caixa

O **TOTVS Chef PDV** é a solução de ponto de venda para food service (bares,
restaurantes, lanchonetes, cafeterias), combinando agilidade operacional com
conformidade fiscal.

### Funcionalidades principais

- **Venda com integração fiscal**: emissão de NFC-e e SAT integrada.
- **Comanda eletrônica**: abertura, acompanhamento e fechamento de comandas.
- **PDV móvel (touch screen)**: dispositivos POS Smart permitem venda na mesa
  ou em pontos do salão, reduzindo filas no caixa.
- **Dual display**: tela secundária para o cliente com totais/subtotais no
  checkout.
- **Controle de estoque integrado**: entradas, saídas e desperdícios.
- **Gestão de produtos**: pratos, ingredientes, combos, com cálculo de custos
  e formação de preços.
- **Relatórios gerenciais**: vendas, consumo por cliente, desempenho de
  produtos.

### Modos de atendimento

| Modo | Descrição |
|---|---|
| Balcão | Atendimento touch screen com venda imediata |
| Mesa | Comanda por mesa, via tablet ou tela de caixa |
| Comanda eletrônica | App Android para o garçom: abre mesa, registra pedido, envia à cozinha |
| Comanda por número | Identificação numérica individual (ficha) |
| Totem de autoatendimento | Cliente escolhe, pede e paga no equipamento; pedido vai direto à cozinha |
| Drive-thru | Atendimento de veículos em fila |
| Delivery central | Gerenciamento integrado de entregas (PDV-Entrega) |

### Fechamento e operações de caixa

- **Fechamento de Caixa por Operador**: Retaguarda > Relatório e Consultas >
  Vendas > Fechamento de Caixa por Operador — recebimentos por operador e
  forma de pagamento.
- **Relatório 1 (Venda de Produtos)**: filtros por grupo, subgrupo,
  fornecedor, período, loja e número de caixa.
- **Relatório 65 (Cupons)**: documentos fiscais emitidos em todos os modelos
  (ECF / PED / CNFM / NF-e / NFC-e / SAT).
- **Relatório 144 (Caixas Conciliados)**: status de conciliação.
- **Conciliação de Caixa**: menu Financeiro > Conciliação de Caixa — concilia
  fechamentos com as formas de pagamento registradas.

### Pagamentos (TEF/POS)

- **TOTVS Pagamento TEF** — transferência eletrônica de fundos integrada.
- **TOTVS Pagamento Instantâneo** — carteiras digitais e meios eletrônicos.
- **SiTef Local** — operação Chip&Pin; requer SiTef instalado/configurado na
  máquina do PDV; suporta multi-IP para failover.
- **POS digitais**: Cielo LIO e PagSeguro (SmartPOS), conforme homologação no
  TDN.

A partir da versão **2.28.03**, a operação usa três APIs:

1. **TOTVS Food Service Mobile API** — operação das comandas eletrônicas.
2. **TOTVS Food Service Pagamento API** — processamento de pagamentos.
3. **TOTVS Food Service Finaliza Venda API** — emissão e cancelamento de
   cupons NFC-e e SAT.

## 2. Comanda eletrônica Android

Elimina comandas em papel; roda em smartphone/tablet Android.

**Requisitos**: Android 5.0+ (recomendado 9.0+), RAM 1,5 GB (recomendado
2 GB); servidor Windows com .NET Framework 4.8.1+, SQL Server; licenças de
servidor de caixa, pagamento móvel (TEF CE) e emissão fiscal.

**Fluxo de operação**:
1. Garçom abre comanda no app TOTVS Food Service Mobile.
2. Registra os pedidos do cliente.
3. Sistema envia automaticamente para impressora de produção ou KDS.
4. Alterações/cancelamentos sincronizam em tempo real.
5. Pagamento na própria comanda (TEF integrado).
6. Cupom fiscal emitido (NFC-e ou SAT).

Manual: TDN — "Manual de configuração e instalação da comanda eletrônica
Android" (pageId=561055985).

## 3. Cardápio digital e QR code

- Geração de QR code que direciona ao site com o cardápio completo.
- Cliente pede online (mesa, balcão ou delivery); transações entram
  automaticamente no PDV e na Gestão Web.
- Benefícios: redução de filas, menos aglomeração, aumento do fluxo de vendas.
- Configuração: artigo "TOTVS FOOD SERVICE - CONFIG - Configuração do Cardápio
  Digital" na Central de Atendimento.

## 4. Totem de autoatendimento

- Cliente escolhe o prato, faz o pedido e paga no próprio equipamento.
- Pedido vai direto para a cozinha (impressora de produção ou KDS).
- Dados sincronizam automaticamente com PDV e Gestão Web.

## 5. KDS — Kitchen Display System

- Envia automaticamente os pedidos para tela na cozinha (celular, tablet,
  desktop ou TV).
- Sem KDS, os pedidos saem em impressora térmica de produção.
- Configuração: no cadastro de produtos, ativar **"Imprimir Monitor"**
  (no Chef Web, configurar na retaguarda).
- Integração homologada com **Logic Controls** (artigo "TC - CONFIG - COMO
  CONFIGURAR KDS LOGIC CONTROLS").
