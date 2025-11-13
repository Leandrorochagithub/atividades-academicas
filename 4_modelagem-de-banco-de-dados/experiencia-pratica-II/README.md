# 📊 Minimundo: Sistema de Rastreamento de Criptomoedas

**Disciplina:** Modelagem de Banco de Dados  
**Aluno:** Leandro da Rocha Ferreira  
**Data:** Novembro/2025

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

## 🎯 2. Entidades Identificadas

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

## Diagrama Entidade-Relacionamento (DER)

<img width="900" height="300" alt="Captura de tela 2025-11-13 112023" src="https://github.com/user-attachments/assets/ebd7b850-909e-4322-9efc-1554e0b91ba3" />

---

## 📚 Referências

- CoinGecko API - Fonte de dados de criptomoedas
- CoinMarketCap - Inspiração para o sistema
- Material didático da disciplina
