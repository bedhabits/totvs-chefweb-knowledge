# Requisitos Técnicos, Instalação e Infraestrutura

## Arquitetura híbrida

- **Chef Web (retaguarda)**: 100% nuvem (SaaS), acessada por navegador —
  nada a instalar.
- **PDV / servidor da loja**: roda local em Windows e sincroniza com a
  nuvem; a loja continua vendendo mesmo com queda de internet.
- Sincronização periódica loja ↔ nuvem (rotinas a cada ~30 min para
  integrações como fidelidade; vendas e cadastros sincronizam
  automaticamente).

## Requisitos do servidor/PDV local

- **SO**: Windows.
- **.NET Framework 4.8.1 ou superior**.
- **Banco de dados**: SQL Server (recomendação típica: SQL Server 2019,
  collation Latin1_General_CI_AS). Versões exatas: TDN "Requisitos de
  Infraestrutura Hardware/Software" (pageId=464975155).
- **RAM**: ~4–8 GB no servidor, ~2 GB por estação; SSD recomendado.
- **Rede local (LAN) estável** obrigatória para sincronização entre PDVs,
  comandas e impressoras.

### Cenários de instalação
1. **Quiosque/loja pequena**: uma máquina concentra banco + estação + PDV.
2. **Rede multiestação**: servidor central com vários PDVs em rede.

### Passos básicos de instalação
1. Verificar requisitos mínimos (TDN).
2. Instalar SQL Server e .NET Framework.
3. Executar o instalador do TOTVS Chef (Central de Atendimento: "TC - PDV -
   Instalação do TOTVS Food Service - Parte 1").
4. Configurar o módulo fiscal (NFC-e: Fiscal Manager + certificado digital;
   SAT: ativação pelo app do fabricante + código de ativação).
5. Configurar periféricos (impressoras, leitores, gaveta, balança).
6. Testar emissão fiscal e sincronização antes de operar.

## Comanda eletrônica (dispositivos)

- Android 5.0+ (recomendado 9.0+), RAM 1,5–2 GB.
- Licenças: servidor de caixa, pagamento móvel (TEF CE), emissão fiscal.
- APIs locais: Mobile, Pagamento e Finaliza Venda (v2.28.03+).

## Periféricos homologados

- Impressora térmica (cupom e produção/cozinha) e impressora de etiquetas.
- Leitor de código de barras (USB teclado ou RS232/USB COM com buffer).
- Monitores touch screen, dual display (tela do cliente).
- Gaveta de dinheiro, balança, catraca.
- SmartPOS (Cielo LIO, PagSeguro).
- Telas para KDS (TV, monitor, tablet); homologação Logic Controls.

## Versionamento

- Esquema de versões da retaguarda: `CW <ano/mês>.<build>` — ex.:
  **Inovação CW 3.2310.0001** (out/2023), **Manutenção CW 3.2407.0001**
  (jul/2024); linha anterior 2.x (ex.: CW 2.49.00).
- PDV/operação com versionamento próprio (ex.: 2.28.03 introduziu as três
  APIs de operação).
- Acompanhar: TDN — "Novidades do Release TOTVS Food Services (Linha Chef)
  Retaguarda".
