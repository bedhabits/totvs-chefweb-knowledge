# Visão Geral — TOTVS Food Service (Linha Chef) e Chef Web

## O que é o produto

O **TOTVS Food Service – Linha Chef** é a solução integrada da TOTVS para
gestão de estabelecimentos de food service no Brasil: frente de caixa, salão,
cozinha, delivery e retaguarda administrativa. Atende restaurantes, bares,
fast food, lanchonetes, cafeterias, casas noturnas, franquias e redes de
qualquer tamanho.

O **TOTVS Chef Web** (também chamado de **Gestão Web** ou **retaguarda web**)
é a camada de back-office do produto: 100% web, acessada por navegador, onde
se administra financeiro, estoque, fiscal, cadastros e indicadores.

- **URL de acesso da retaguarda**: https://chefwebcloud.chef.totvs.com.br/
- **Servidor de APIs**: `chefweb.chef.totvs.com.br/chefwebapi`

## Componentes da Linha Chef

| Componente | Função |
|---|---|
| **Chef PDV** | Frente de caixa: vendas, mesas, comandas, emissão fiscal (NFC-e/SAT), pagamentos TEF/POS |
| **Chef Web (retaguarda/Gestão Web)** | Back-office web: financeiro, estoque, fiscal, cadastros, relatórios, DRE, CMV |
| **Comanda eletrônica (Android)** | App para garçons: abre mesa/comanda, registra pedidos, envia à cozinha |
| **KDS (cozinha eletrônica)** | Tela de produção na cozinha (alternativa: impressoras de produção) |
| **Delivery / PDV-Entrega** | Gestão de entregas; integrações iFood, Anota Aí, Uber Eats, Rappi etc. |
| **Cardápio digital / QR code** | Pedido online pelo celular do cliente (mesa, balcão, delivery) |
| **Totem de autoatendimento** | Cliente pede e paga no quiosque; pedido vai direto à produção |
| **SmartOrder** | Solução TOTVS de pedidos online / site integrado |

## Fluxo de operação ponta a ponta

1. **Atendimento** — pedido registrado no PDV, comanda eletrônica, totem,
   cardápio digital ou plataforma de delivery.
2. **Produção** — pedido enviado automaticamente ao KDS ou impressora de
   cozinha.
3. **Fechamento** — conta fechada no PDV/comanda, pagamento (TEF/POS/PIX),
   emissão de documento fiscal (NFC-e/SAT).
4. **Retaguarda** — vendas sincronizam com o Chef Web: baixa de estoque pela
   ficha técnica, lançamentos financeiros, relatórios e indicadores.

## Arquitetura e modelo de contratação

- **Retaguarda em nuvem (SaaS)**: Chef Web roda em datacenter TOTVS, acessível
  por navegador, com backups e atualizações automáticas.
- **PDV local (Windows)**: a frente de caixa roda localmente (Windows,
  .NET Framework, SQL Server) e sincroniza com a nuvem — modelo híbrido que
  mantém a loja operando mesmo com oscilação de internet.
- Contratação por assinatura (subscription).

## Multi-loja (redes e franquias)

- Gestão centralizada de cadastros com **replicação** de produtos, cardápio e
  preços para as lojas/franquias (inclusive replicação seletiva de novos
  produtos).
- Visão consolidada: dashboards da rede, ranking de lojas, relatórios
  consolidados ou por loja.
- Controle de acesso multi-loja: usuário pode ter acesso a uma ou várias
  lojas; gerentes locais veem só a própria unidade.
- Transferência de estoque entre lojas.

## Público-alvo

- Restaurantes à la carte e self-service
- Fast food, hamburguerias, pizzarias
- Bares, pubs, cervejarias e casas noturnas
- Cafeterias e lanchonetes
- Franquias e redes (de poucas unidades a centenas)

## Segurança e conformidade

- Conformidade com a **LGPD** (auditoria de acessos, controle de dados).
- Perfis de acesso granulares por módulo, função e loja.
- Conformidade fiscal brasileira: NFC-e, SAT/CF-e, NF-e, SPED.

## Canais oficiais

- **Documentação técnica (TDN, espaço TChef)**: https://tdn.totvs.com/display/public/TChef
- **Central de Atendimento** (artigos `TC - CW - ...` para Chef Web):
  https://centraldeatendimento.totvs.com/hc/pt-br/sections/1500000596861-Food-Service-Linha-Chef
- **Página do produto**: https://www.totvs.com/varejo/food-service/
- **Ficha técnica**: https://produtos.totvs.com/ficha-tecnica/tudo-sobre-o-totvs-food-service-linha-chef/
- **Suporte telefônico**: (11) 4003-0015
