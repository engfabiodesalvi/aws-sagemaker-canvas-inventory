### 📊 Previsão de Estoque com Amazon SageMaker Canvas (ML No-Code)

Este projeto apresenta a construção de um modelo de **previsão de estoque baseado em séries temporais** utilizando o **Amazon SageMaker Canvas**, explorando recursos de Machine Learning no-code para geração de previsões probabilísticas e análise de risco de ruptura.

O objetivo foi aplicar o fluxo completo de criação de modelo — da preparação dos dados até a interpretação das previsões — com foco em **boas práticas analíticas e comunicação de incerteza**.

---

### 🎯 Objetivo

Desenvolver um modelo de previsão de estoque por produto para o próximo período, utilizando dados históricos e variáveis explicativas, gerando:

- previsão mediana

- intervalo de incerteza

- classificação de risco

- visualização temporal com valores previstos

---

### 🗂 Dataset

Base histórica contendo:

- ID do produto

- data (série temporal)

- flag de promoção

- quantidade em estoque

O dataset foi importado no SageMaker Canvas via CSV (UTF-8) e validado no ambiente antes do treinamento.

---

### ⚙️ Modelagem no SageMaker Canvas

Foi utilizado o tipo de modelo:

**Time Series Forecasting**

Configurações principais:

- Target: quantidade em estoque

- Coluna temporal: data

- Identificador: produto

- Variável adicional: flag de promoção

Foram executados treinamentos em modo rápido e completo para comparação de resultados.

---

### 🔮 Saída do Modelo

O Canvas gerou previsões probabilísticas:

- **P10** → cenário pessimista

- **P50** → valor mediano (mais provável)

- **P90** → cenário otimista

- **Mean** → média prevista

Esses percentis foram mantidos para preservar a incerteza do modelo.

---

### ⚠️ Interpretação de Valores Negativos

Previsões negativas foram interpretadas como **sinal de risco de ruptura de estoque**, e não como erro do modelo.

Foi adotada a separação entre:

- saída estatística do modelo

- regra de negócio aplicada após a previsão

Exemplo de regra aplicada na análise:

`Estoque final = MAX(0, P50)`

---

### 🚦 Classificação de Risco

Foi criada uma regra de risco baseada nos percentis:

- 🟢 Seguro → P10 ≥ 0

- 🟡 Atenção → P10 < 0 e P50 ≥ 0

- 🔴 Ruptura provável → P50 < 0

Os indicadores foram incluídos nas tabelas e exportados em CSV com emojis Unicode.

---

### 📈 Visualizações Produzidas

Foram gerados gráficos no Excel para comunicação dos resultados:

- série temporal de estoque real + previsto

- linha P50 com ponto de previsão

- marcadores P10 e P90 no horizonte previsto

- gráfico comparativo por produto

- faixa de incerteza (intervalo P10–P90)

Essas visualizações facilitam a interpretação por público técnico e de negócio.

---

### 🧠 Boas Práticas Aplicadas

- preservação de percentis do modelo

- não truncamento das previsões negativas

- separação entre modelo e regra de negócio

- uso de previsões probabilísticas

- documentação reprodutível

- gráficos com incerteza explícita

---

### 🛠 Tecnologias Utilizadas

- Amazon SageMaker Canvas

- AWS

- Excel (análise e gráficos)

- Markdown

- GitHub

---

### ✅ Resultado

O projeto demonstra a aplicação prática de ***Machine Learning no-code para previsão de estoque**, com interpretação correta de incerteza, análise de risco e comunicação visual dos resultados, alinhado às boas práticas de modelagem e tomada de decisão baseada em dados.
