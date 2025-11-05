# 📊 Minimundo: Sistema de Rastreamento de Criptomoedas

**Disciplina:** Modelagem de Banco de Dados  
**Aluno:** Leandro da Rocha Ferreira  
**Data:** Janeiro/2025

---

## 📖 1. Descrição do Minimundo

### Contexto

O mercado de criptomoedas movimenta bilhões de dólares diariamente, com milhares de moedas digitais sendo negociadas 24 horas por dia, 7 dias por semana. Os preços variam constantemente, e investidores, aplicativos e sites precisam acompanhar essas mudanças em tempo real.

### O Sistema Proposto

Um **sistema de rastreamento de preços de criptomoedas** que:

- Armazena informações básicas sobre diferentes criptomoedas (Bitcoin, Ethereum, Cardano, etc.)
- Registra o histórico de preços ao longo do tempo
- Permite consultar preços atuais e passados
- Calcula variações e tendências de mercado

### Principais Entidades

**1. Criptomoedas**
- Cada moeda tem um identificador único, símbolo (ex: BTC) e nome (ex: Bitcoin)
- Informações como capitalização de mercado

**2. Histórico de Preços**
- Registros periódicos do preço de cada moeda
- Inclui data/hora, preço em dólar, volume de negociação

### Processos Básicos

- **Cadastrar** novas criptomoedas no sistema
- **Coletar** preços periodicamente (ex: a cada 30 minutos)
- **Consultar** preço atual de uma moeda
- **Listar** histórico de preços de um período
- **Calcular** variações percentuais

---

## 🔍 2. Conceitos Fundamentais

### 2.1 Dado vs. Informação

| Conceito | Definição | Exemplo no Minimundo |
|----------|-----------|---------------------|
| **Dado** | Valor bruto, sem contexto | • `42350.87`<br>• `BTC`<br>• `2025-01-15` |
| **Informação** | Dado processado que gera significado | • "O Bitcoin está cotado a **$42.350,87 USD** em 15/01/2025"<br>• "O **BTC** subiu **7,9%** nas últimas 24 horas" |

**Explicação:**

Um número como `42350.87` sozinho não significa nada. Mas quando contextualizamos:
- É um **preço** (não uma quantidade ou peso)
- Em **dólares** (não reais ou euros)
- Do **Bitcoin** (não de outra moeda)
- Em **15/01/2025** (não ontem ou amanhã)

Isso se transforma em **informação útil** para tomar decisões (comprar, vender, aguardar).

### 2.2 Dados Estruturados vs. Não Estruturados

| Tipo | Definição | Exemplo no Minimundo |
|------|-----------|---------------------|
| **Estruturados** | Organizados em formato fixo (tabelas com colunas definidas) | **Tabela de Preços:**<br>• ID: número único<br>• Moeda: texto (máx 50 caracteres)<br>• Data: formato data/hora<br>• Preço: número decimal<br>• Volume: número inteiro grande |
| **Não Estruturados** | Sem formato fixo, difícil de organizar em tabelas | • **Notícias** sobre as moedas (texto livre)<br>• **Comentários** de usuários (opinião)<br>• **Gráficos** de preços (imagens)<br>• **Whitepapers** (documentos técnicos em PDF) |

**Explicação:**

**Dados estruturados** cabem perfeitamente em planilhas/tabelas:
```
+--------+--------+---------------------+-----------+
| ID     | Moeda  | Data                | Preço     |
+--------+--------+---------------------+-----------+
| 1      | BTC    | 2025-01-15 14:30    | 42350.87  |
| 2      | ETH    | 2025-01-15 14:30    | 3150.23   |
+--------+--------+---------------------+-----------+
```

**Dados não estruturados** não têm formato padrão:
```
"Bitcoin atingiu novo recorde hoje! Muitos analistas 
acreditam que a tendência de alta vai continuar nas 
próximas semanas. 🚀"

[Este texto não cabe em uma coluna "Preço" ou "Data"]
```

---

## 📊 3. Quadro-Resumo

### Dado x Informação

| Tipo | Exemplo 1 | Exemplo 2 | Exemplo 3 |
|------|-----------|-----------|-----------|
| **Dado** | `42350.87` | `BTC` | `28000000000` |
| **Informação** | "Bitcoin custa $42.350,87" | "BTC é o símbolo do Bitcoin" | "Volume de $28 bilhões negociados" |

### Estruturado x Não Estruturado

| Tipo | Armazenado em Tabela? | Exemplos |
|------|-----------------------|----------|
| **Estruturado** | ✅ Sim | Preço, Data, Volume, Nome da moeda, Símbolo |
| **Não Estruturado** | ❌ Não (ou com dificuldade) | Descrição da moeda, Notícias, Comentários, Gráficos, Whitepapers |

---

## 🎯 4. Entidades Identificadas

### Entidade 1: CRIPTOMOEDA

**Atributos:**
- Identificador (ex: bitcoin)
- Símbolo (ex: BTC)
- Nome completo (ex: Bitcoin)
- Capitalização de mercado

**Exemplo:**
```
Identificador: bitcoin
Símbolo: BTC
Nome: Bitcoin
Market Cap: $830 bilhões
```

### Entidade 2: HISTÓRICO DE PREÇOS

**Atributos:**
- Identificador único do registro
- Moeda (referência à criptomoeda)
- Data e hora
- Preço em USD
- Volume de negociação 24h

**Exemplo:**
```
ID: 1
Moeda: bitcoin
Data/Hora: 2025-01-15 14:30:00
Preço: $42.350,87
Volume: $28 bilhões
```

---

## 🔗 5. Relacionamento Básico
```
Uma CRIPTOMOEDA possui VÁRIOS registros de HISTÓRICO DE PREÇOS

Exemplo:
Bitcoin ─┬─ Preço em 15/01/2025 às 14:30
         ├─ Preço em 15/01/2025 às 15:00
         ├─ Preço em 15/01/2025 às 15:30
         └─ ... (milhares de registros)
```

**Tipo de relacionamento:** 1 para N (um para muitos)
- 1 criptomoeda → N registros de preço
- 1 registro de preço → 1 criptomoeda

---

## 📝 6. Justificativa da Escolha

Escolhi este minimundo porque:

1. **Relevância:** Mercado de criptomoedas está em crescimento
2. **Dados reais:** Existem APIs públicas para coletar dados
3. **Complexidade adequada:** Não é nem muito simples, nem muito complexo
4. **Interesse pessoal:** Tenho curiosidade sobre o mercado cripto
5. **Aplicabilidade:** Sistema similar ao usado por sites como CoinMarketCap

---

## 📚 Referências

- CoinGecko API - Fonte de dados de criptomoedas
- CoinMarketCap - Inspiração para o sistema
- Material didático da disciplina
