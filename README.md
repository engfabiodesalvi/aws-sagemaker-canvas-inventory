# 📊 Previsão de Estoque Inteligente na AWS com SageMaker Canvas
### 👤 Autor

### Fabio Toledo Bonemer De Salvi

Projeto desenvolvido como parte do desafio *“Previsão de Estoque Inteligente na AWS com SageMaker Canvas”*, com foco não apenas na execução do modelo no-code, mas também na **análise crítica dos dados, interpretação dos resultados e aplicação de regras de negócio** para cenários reais de gestão de estoque.

---

## 📌 Visão Geral do Projeto

Este projeto demonstra como utilizar o **Amazon SageMaker Canvas** para criar um modelo de **previsão de estoque baseada em Machine Learning**, partindo de dados históricos simples e evoluindo até uma análise interpretável e aplicável ao contexto de negócio.

O diferencial deste trabalho está em:

- Análise exploratória dos dados de entrada

- Interpretação correta das previsões probabilísticas (P10, P50, P90)

- Tratamento e explicação de **previsões negativas**

- Comunicação visual dos resultados com **tabelas e gráficos**

---

## 🎯 Objetivo

Prever a **quantidade de unidades em estoque para o próximo dia**, por produto, utilizando um modelo de séries temporais treinado no SageMaker Canvas, considerando também a **incerteza associada às previsões**.

---

## 📋 Dataset Utilizado

O dataset de treino possui a seguinte estrutura:

| Campo | Descrição |
| --- | --- |
| ID_PRODUTO | Identificador do produto |
| DIA |	Data do registro |
| FLAG_PROMOCAO | Indicador de promoção (0 = não, 1 = sim) |
| QUANTIDADE_ESTOQUE | Quantidade de unidades em estoque |

Exemplo de registros:

| ID_PRODUTO | DIA	| FLAG_PROMOCAO	| QUANTIDADE_ESTOQUE |
| :---: | :---: | :---: | :---: |
| 1 | 2023-12-31 | 0 | 91 |
| 2 | 2023-12-31 | 0 | 64 |
| 3 | 2023-12-31 | 0 | 66 |

📌 **Observação importante**

O modelo foi treinado para prever o nível absoluto de estoque, o que exige cuidados adicionais na interpretação das saídas.

---

## 🚀 Metodologia

1️⃣ Seleção e Upload do Dataset

O dataset foi carregado no SageMaker Canvas sem necessidade de código, utilizando a interface visual da ferramenta.

2️⃣ Treinamento do Modelo

- Tipo de problema: **Previsão temporal**

- Variável alvo: `QUANTIDADE_ESTOQUE`

- Horizonte de previsão: **1 dia**

- Saídas geradas:

    - P10 (cenário pessimista)

    - P50 (mediana – previsão central)

    - P90 (cenário otimista)

    - Mean (média)

---

## 📊 Resultados da Previsão

### Tabela de Previsões

O *dataset* utilizado para treinar o modelo de predição de estoque contempla os dados do número de itens de estoque de 25 produtos de 20 dias consecutivos, entre s dia x e x.

A previsão de estoque obtida do modelo de predição se refere ao dia **20/01/2024**, próximo dia na série temporal.

| ID do Produto | P10 | P50 | P90 | Média |
| :---: | :---: | ---: | ---: | ---: |
| 1 | 2024-01-20 | 11.870 | 15.396 | 17.470 | 14.905 |  |  |  |  |  |  |  |  | 
| 2 | 2024-01-20 | -22.645 | -15.637 | -10.207 | -16.021 |  |  |  |  |  |  |  |  | 
| 3 | 2024-01-20 | -26.289 | -17.811 | -11.696 | -18.653 |  |  |  |  |  |  |  |  | 
| 4 | 2024-01-20 | -15.521 | -11.788 | -8.119 | -11.978 |  |  |  |  |  |  |  |  | 
| 5 | 2024-01-20 | 19.872 | 21.875 | 23.157 | 21.716 |  |  |  |  |  |  |  |  | 
| 6 | 2024-01-20 | -17.603 | -11.391 | -4.632 | -11.475 |  |  |  |  |  |  |  |  | 
| 7 | 2024-01-20 | -11.331 | -9.628 | -7.959 | -9.595 |  |  |  |  |  |  |  |  | 
| 8 | 2024-01-20 | -10.143 | -7.222 | -4.218 | -7.063 |  |  |  |  |  |  |  |  | 
| 9 | 2024-01-20 | -5.230 | -2.964 | -0.656 | -2.960 |  |  |  |  |  |  |  |  | 
| 10 | 2024-01-20 | -22.092 | -17.558 | -12.021 | -17.328 |  |  |  |  |  |  |  |  | 
| 11 | 2024-01-20 | -20.606 | -13.481 | -5.727 | -13.430 |  |  |  |  |  |  |  |  | 
| 12 | 2024-01-20 | -25.398 | -20.235 | -15.500 | -20.331 |  |  |  |  |  |  |  |  | 
| 13 | 2024-01-20 | -25.557 | -21.183 | -16.350 | -21.201 |  |  |  |  |  |  |  |  | 
| 14 | 2024-01-20 | -19.472 | -16.209 | -12.630 | -16.214 |  |  |  |  |  |  |  |  | 
| 15 | 2024-01-20 | 17.321 | 18.991 | 21.452 | 19.181 |  |  |  |  |  |  |  |  | 
| 16 | 2024-01-20 | 24.706 | 26.695 | 28.861 | 26.761 |  |  |  |  |  |  |  |  | 
| 17 | 2024-01-20 | -5.087 | -2.536 | -0.722 | -2.813 |  |  |  |  |  |  |  |  | 
| 18 | 2024-01-20 | -16.792 | -13.222 | -8.862 | -13.109 |  |  |  |  |  |  |  |  | 
| 19 | 2024-01-20 | -15.893 | -12.506 | -8.569 | -12.306 |  |  |  |  |  |  |  |  | 
| 20 | 2024-01-20 | -9.655 | -7.185 | -4.257 | -7.179 |  |  |  |  |  |  |  |  | 
| 21 | 2024-01-20 | 5.185 | 8.192 | 10.307 | 7.997 |  |  |  |  |  |  |  |  | 
| 22 | 2024-01-20 | -22.914 | -16.121 | -8.317 | -15.460 |  |  |  |  |  |  |  |  | 
| 23 | 2024-01-20 | -3.548 | -2.912 | -2.359 | -2.941 |  |  |  |  |  |  |  |  | 
| 24 | 2024-01-20 | -16.842 | -11.717 | -7.665 | -12.278 |  |  |  |  |  |  |  |  | 
| 25 | 2024-01-20 | -17.309 | -13.440 | -9.650 | -13.411 |  |  |  |  |  |  |  |  | 

📌 **Interpretação correta**

Valores negativos **não representam estoque físico negativo**, mas sim:

- Forte tendência de queda
- Alto risco de **ruptura total de estoque**

---

## 📈 Visualização dos Resultados
### Gráfico Principal

#### Previsão de Estoque para o Próximo Dia (P10–P90 com Mediana P50)

- Linha central: P50
- Faixa sombreada: Intervalo de incerteza (P10–P90)
- Eixo Y com referência em zero
- Produtos ordenados por risco

📷 Figura 1 – Previsão de estoque com intervalo de incerteza
(Inserir imagem do gráfico aqui)

---

### Tabela de Risco de Ruptura

| Produto | Estoque Previsto (P50) | Risco de Ruptura |
| :---: | :---: | :---: |
| 2 | 0 | 🔴 Alto |
| 3 | 0 | 🔴 Alto |
| 5 | 22 | 🟢 Baixo |


📷 Tabela x – Tabela de risco por produto

---

## 📌 Conclusões

- O SageMaker Canvas permite criar modelos robustos de previsão sem código

- A interpretação correta das saídas probabilísticas é essencial

- Valores negativos são **indicadores de risco**, não erros

- A combinação de ML + regras de negócio torna o modelo aplicável ao mundo real

---

## 🔮 Próximos Passos

- Prever **demanda diária** em vez de estoque absoluto

- Incorporar mais variáveis:
    - sazonalidade
    - vendas
    - lead time (tempo total decorrido entre o início de um processo e a sua conclusão final)

- Automatizar o pipeline com AWS Lambda e S3

- Criar dashboard no QuickSight

---

## 🤔 Dúvidas ou Sugestões?

Sinta-se à vontade para abrir uma issue neste repositório ou entrar em contato.