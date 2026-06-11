# Produto: Menu Namorados 3 Etapas (12/06)

Procedimento de cadastro no TOTVS Chef Web (retaguarda) do menu fechado de
Dia dos Namorados, usando o recurso **Kit com Categorias**.

## O produto

- **Menu 3 Etapas — R$ 210 por pessoa**, vendido apenas para casais.
- Modelagem recomendada: **kit por casal, R$ 420** (a entrada é única e
  compartilhada; um kit por pessoa não comporta "meia entrada").

| Etapa | Itens | Regra |
|---|---|---|
| Entrada | Tábua Virtuosa | 1 por casal (compartilhada) |
| Prato principal | Pupunha, Bisque & Camarão / Ravioli de Cogumelos | 1 por pessoa (2 no kit) |
| Sobremesa | Doce Desejo / Delícia com você | 1 por pessoa (2 no kit) |

Os produtos já existem no cadastro com preços individuais — dentro do kit
esses preços são ignorados: vale o preço do produto principal do kit.

## Passo a passo

### 1. Produto principal do kit — Cadastros > Produtos

1. Novo produto: **"Menu Namorados 3 Etapas (Casal)"**, preço de venda **R$ 420,00**.
2. Aba **Produção**: marcar **"Produto Kit"** e salvar.
3. Configurar dados fiscais (NCM/CFOP/CST) como nos demais produtos de venda.

### 2. Categorias — Cadastros > Categorias

Criar 3 categorias do tipo **padrão** (NÃO marcar "Pré-definir quantidade de
produtos" — o sistema não permite misturar categoria padrão com
quantidade pré-definida no mesmo kit):

| Categoria | Produtos vinculados (aba Produtos) |
|---|---|
| 1-Entrada | Tábua Virtuosa |
| 2-Prato Principal | Pupunha, Bisque & Camarão; Ravioli de Cogumelos |
| 3-Sobremesa | Doce Desejo; Delícia com você |

### 3. Montagem do kit — Cadastros > Kits

1. Editar o kit "Menu Namorados 3 Etapas (Casal)".
2. **Vincular categoria(s)** e definir mínimo/máximo:
   - 1-Entrada: mín **1** / máx **1**
   - 2-Prato Principal: mín **2** / máx **2** (o casal pode repetir o mesmo prato)
   - 3-Sobremesa: mín **2** / máx **2**
3. Ordenar com **Mover para cima/baixo**: Entrada → Principal → Sobremesa.
   Essa ordem organiza os itens na comanda/impressão de produção.

### 4. Teste obrigatório antes do serviço

- A sincronização retaguarda ↔ PDV não é instantânea (~30 min em algumas
  rotinas). Cadastrar com antecedência.
- Fazer venda teste no PDV: lançar o kit, escolher os pratos, conferir a
  impressão na cozinha (ordem das etapas) e a emissão fiscal.

## Limitação conhecida — disparo por etapa

O "fire" por etapa (cozinha só inicia a sobremesa quando o casal termina o
principal) **não é recurso documentado do kit**. O kit imprime os itens na
ordem das categorias; o controle de tempo é operacional:

- Garçom avisa/marca a cada etapa na comanda eletrônica; ou
- Usar **observações de pedido** (ex.: "AGUARDAR CHAMADA") nos itens de
  principal e sobremesa.

Para confirmar se existe recurso nativo de etapas/tempos, abrir chamado na
Central de Atendimento TOTVS.

## Fontes

- TDN — Cadastro de Kits: https://tdn.totvs.com/display/public/TChef/Cadastro+de+Kits
- Base interna: docs/02-modulos-retaguarda.md (seção Kits e combos)
