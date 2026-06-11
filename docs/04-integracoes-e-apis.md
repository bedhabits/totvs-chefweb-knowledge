# Integrações e APIs

Pontos de integração da Linha Chef / Chef Web com plataformas externas e
APIs públicas documentadas no TDN (espaço TChef).

## 1. Delivery e pedidos online

### iFood
- Integração nativa (versão atual: **iFood 4.0**), com autenticação via
  plataforma iFood.
- Pedidos entram automaticamente no **PDV-Entrega** e são impressos nos
  pontos de produção.
- Sincronização de cardápio: cada item do cardápio delivery (inclusive
  extras/complementos) precisa do **código do produto no Chef**.
- **Notificar Retirada** (menu Operações): avisa o app do iFood quando o
  pedido está pronto.
- Suporte a **pedidos agendados**, exibição do código de coleta na
  conferência de entrega e impressão do nome da loja nos impressos.
- **Entrega Fácil / Easy Delivery**: loja recebe o pedido, iFood faz a
  entrega.
- Suporta mais de uma loja na plataforma com o mesmo CNPJ.
- **Anota Aí** (iFood): canal adicional de recebimento de pedidos (desde
  março/2024).

### Outras plataformas
- **Uber Eats**: pedidos e sincronização de cardápio (página própria no TDN).
- **Rappi CPG**: integração para varejo/CPG (não cobre o segmento
  restaurante do Rappi).
- **99Food** e demais: ver "Lista de Integrações Pedidos Online" no TDN
  (pageId=458775104).
- **SmartOrder**: solução TOTVS de pedidos online/site próprio integrado ao
  PDV (Setup - Smart Order - Delivery no TDN).
- **Cardápio digital QR code** e **totem**: canais próprios que entram
  direto no PDV/produção.

## 2. Pagamentos (TEF/POS)

- **TOTVS Pagamento TEF** e **TOTVS Pagamento Instantâneo** (carteiras
  digitais/PIX).
- **SiTef local** (Chip&Pin), com configuração multi-IP para failover.
- **POS digitais homologados**: Cielo LIO, PagSeguro (SmartPOS).
- TEF na comanda eletrônica (licença "TEF CE").

## 3. Fiscal
- **TOTVS Processos Fiscais / Plataforma Fiscal**: emissão NFC-e, manifesto
  do destinatário, custódia de XML.
- Fiscal Manager + certificado digital para NFC-e; ativação de equipamento
  SAT pelo aplicativo do fabricante.

## 4. Fidelidade
- **Fidelimax** (integração nativa): a cada ~30 min o sistema busca pedidos
  com status "pago" e pontua automaticamente; cadastro automático de
  clientes. Requer usuário ADMIN com acesso a todas as lojas.

## 5. APIs públicas do Chef Web

**Servidor**: `https://chefweb.chef.totvs.com.br/chefwebapi`
(ou `http://{servidor}/Chefwebapi` em instalações dedicadas)

**Autenticação**: login com **usuário, senha e número de série (licença) da
loja**; retorna **token com validade de ~2 minutos**, usado nas demais
chamadas. Recomenda-se usuário tipo ADMIN com acesso a todas as lojas.

| API | Função |
|---|---|
| **API Pedidos Online — Delivery** | Injetar/consultar pedidos de delivery (base das integrações de marketplace) |
| **API Pedidos Online — Balcão** | Pedidos presenciais/retirada |
| **ObterCardapio** | Exporta cardápio com produtos, preços e complementos |
| **API Capa Venda** (`ListPorDataIntegracaoChefweb`) | Vendas por loja/data de integração (janela máx. de 1 dia por chamada) |
| **API Fechamento de Caixa** (`/api/FechamentoCaixa/ObterFechamentoCaixa`) | Fechamentos com naturezas financeiras e formas de pagamento (período máx. 30 dias) |

APIs internas da operação (v2.28.03+): TOTVS Food Service **Mobile**
(comanda), **Pagamento** e **Finaliza Venda** (emissão/cancelamento
NFC-e/SAT) — instaladas junto ao servidor local.

Guia geral: TDN "Guia de implementação das APIs TOTVS" e portal
https://api.totvs.com.br/.

## 6. Importação/exportação de dados

- **XML NF-e** (entrada de mercadorias, manifestação do destinatário).
- **OFX** (conciliação bancária).
- **Planilhas Excel**: cadastro de produtos, inventário, composições/fichas
  técnicas.
- Exportação de relatórios (Excel/PDF).

## 7. Parceiros homologados

Lista oficial: TDN — "Parceiros FOOD SERVICES (Linha Chef)"
(pageId=725272601). Inclui soluções complementares como **Pedido Digital by
Videosoft** (totem), **Autopagamento by Videosoft** e **Gestão de Vendas by
Retail App** (dashboards mobile).

## 8. Pontos de atenção ao planejar integrações

1. Toda integração de pedido exige cardápio sincronizado com os códigos de
   produto do Chef (incluindo complementos).
2. Tokens de API expiram rápido (~2 min) — implementar renovação automática.
3. APIs de consulta têm janelas máximas (1 dia na Capa Venda, 30 dias no
   Fechamento de Caixa) — paginar por data.
4. Integrações que pontuam/exportam vendas dependem do status "pago" e da
   sincronização periódica (~30 min) da loja com a nuvem.
5. Homologar em ambiente de teste antes de ativar (exigência da própria
   TOTVS para iFood).
