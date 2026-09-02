# Releases e Novidades (evolução do produto)

Consolidado a partir dos posts "Novidades" (produtos.totvs.com) e dos
release notes do TDN (espaço TChef). Última revisão: **setembro/2026**.

## Como a TOTVS publica as novidades da Linha Chef

- **TDN — "Novidades do Release TOTVS Food Services (Linha Chef) Retaguarda"**:
  fonte principal e mais completa; releases agrupados por **Expedição**
  (há páginas "Expedição 2025" e "Expedição 2026 Food Retaguarda").
- **produtos.totvs.com** — série de posts "Novidades do TOTVS Food Service –
  Linha Chef": publicação esporádica (2–3 posts/ano); o último post
  identificado é de **novembro/2024** — depois disso as novidades
  concentram-se no TDN.

### Esquema de versões da retaguarda (Chef Web)

- Linha antiga: `CW 2.xx.00` (ex.: 2.36.00, 2.43.00, 2.49.00).
- Linha atual: **`CW 3.AAMM.NNNN`** — o número embute ano e mês:
  `3.2310.0001` = out/2023, `3.2407.0001` = jul/2024,
  `3.2410.0002` = out/2024.
- Releases marcados como **Inovação** (novas funcionalidades) ou
  **Manutenção** (correções).
- Rastreabilidade no TDN: documentos técnicos ("DT") com prefixo
  **DVARHAN-** (antigos) e **DFOODCHEF-** (a partir do ciclo 3.23xx/3.24xx).
- PDV tem versionamento próprio (ex.: 2.28.03 introduziu as APIs Mobile/
  Pagamento/Finaliza Venda; integrações citam mínimos como 2.28.09 e
  2.28.11).

## 2023

### Janeiro/2023
- Envio do cupom fiscal por e-mail ao cliente no modelo **SAT** (SP e CE).
- iFood: descrição de **descontos e taxas adicionais** no cupom; tratamento
  de **motivos de cancelamento** no padrão da plataforma.
- Contingência fiscal (CE): roteamento para **impressora SAT** em falha de
  emissão da NFC-e, sem parar as vendas.
- **SiTef multi-IP**: mais de um IP no servidor TEF para failover.
- Configuração da apresentação das **formas de pagamento** na tela de
  recebimento.

### Agosto/2023
- **PDV com duas telas** (tela do cliente com totais/subtotais no checkout).
- Relatório de Movimentação Financeira com visão por **data de depósito**
  (facilita conciliação).
- **API de consulta ao cadastro de produtos** para integração com sistemas
  externos (validações fiscais/contábeis).
- Homologação de impressoras via **spooler do Windows** com protocolo
  **ESC-POS**.
- Atualização de **código de benefício fiscal (GO)**.
- Novo **guia de usuário** do módulo de Retaguarda.

### Outubro/2023
- Release **Inovação CW 3.2310.0001** — estreia da linha 3.x da retaguarda.
  Entre os temas do ciclo: **conciliação bancária via importação de OFX**.

## 2024

### Março/2024
- Integração com **Anota Aí** (iFood) — novo canal de pedidos.
- Integração com **Entrega Fácil** (logística iFood).
- Múltiplas lojas na plataforma de delivery com o **mesmo CNPJ**.

### Julho/2024
- Release **Manutenção CW 3.2407.0001** (correções — inclui ajustes na
  importação de OFX).

### Outubro–Novembro/2024
- Release **Manutenção CW 3.2410.0002**.
- Entrada de mercadorias com **data de validade, lote e data de
  fabricação**.
- Novo **Relatório de Controle de Vencimento de Produtos** (itens próximos
  do vencimento).
- iFood 4.0: agendamento de entrega, código de coleta na conferência,
  autenticação via plataforma.

## 2025–2026

- O produto segue ativo com releases publicados nas páginas de **Expedição
  2025** e **Expedição 2026 Food Retaguarda** no TDN — a série de posts
  mensais em produtos.totvs.com foi descontinuada, então **a consulta de
  novidades recentes deve ser feita direto no TDN**:
  https://tdn.totvs.com/display/public/TChef/Novidades+do+Release+TOTVS+Food+Services+(Linha+Chef)+Retaguarda
- **SPED Contribuições leiaute 019** obrigatório desde jan/2025.
- **Reforma Tributária (IBS/CBS)**: 2026 é ano de transição — NF-e/NFC-e
  ganham campos de IBS/CBS/Imposto Seletivo (NT 2025.002). A documentação
  encontrada é dos produtos de backoffice TOTVS (Protheus/Datasul); o
  tratamento específico na Linha Chef deve ser **confirmado no TDN/suporte**
  antes de qualquer planejamento fiscal.
- Correções recentes documentadas no TDN incluem, por exemplo, recebimento
  via **PIX com QR Code** no PDV (DFOODCHEF-1195).

## ⚠️ Não confundir: "TOTVS Food Service" (sem "Linha Chef")

Existe um produto distinto chamado apenas **TOTVS Food Service**, com série
de novidades própria, que foi **descontinuado em 01/01/2026** (uso permitido
até 31/12/2025). Isso **não** afeta o TOTVS Food Service **– Linha Chef**
(Chef Web/Chef PDV), que continua ativo. Fonte: Central de Atendimento,
artigo "Descontinuação do TOTVS Food Service".

## Manutenção desta página

1. Consultar o TDN (Novidades do Release Retaguarda → Expedição do ano).
2. Registrar aqui: versão, data, tipo (inovação/manutenção) e destaques.
3. Adicionar novas fontes em `docs/99-fontes.md`.

> **Nota de confiabilidade**: os itens de 2023–2024 vêm dos posts oficiais;
> o mapa de versões vem dos títulos das páginas do TDN. Detalhes internos de
> cada release (lista completa de correções) devem ser confirmados na página
> do release no TDN.
