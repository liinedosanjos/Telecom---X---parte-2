# Projeto Telecom X – Parte 2

## 📌 Propósito da Análise
O objetivo deste projeto é **prever a evasão de clientes (churn)** em uma empresa de telecomunicações utilizando **modelos de machine learning**, além de identificar os **fatores que mais influenciam a decisão de cancelamento**.  
A análise permite **estruturar estratégias de retenção** e otimizar serviços e ofertas.

---

## 🗂 Estrutura do Projeto

- `notebook.ipynb` – notebook principal contendo toda a análise exploratória, pré-processamento, modelagem e visualizações.  
- `telecom_tratado.csv` – dataset tratado, pronto para análise e modelagem.   

---

## 🔄 Preparação dos Dados

### Classificação das Variáveis
- **Numéricas:** `tenure`, `MonthlyCharges`, `TotalCharges`, `Contas_Diarias`, `num_servicos`  
- **Categóricas:** `customer_gender`, `customer_SeniorCitizen`, `customer_Partner`, `customer_Dependents`, `PhoneService`, `MultipleLines`, `InternetService`, `OnlineSecurity`, `OnlineBackup`, `DeviceProtection`, `TechSupport`, `StreamingTV`, `StreamingMovies`, `account_Contract`, `account_PaperlessBilling`, `account_PaymentMethod`

### Etapas de Pré-processamento
1. **One-Hot Encoding** das variáveis categóricas para utilização em modelos que não lidam com strings.  
2. **Padronização** das variáveis numéricas para modelos sensíveis à escala (ex.: Regressão Logística, KNN).  
3. **Separação em treino e teste**: 70% treino, 30% teste, com estratificação pela variável alvo `Churn_num`.

---
## ⚙ Modelagem

### Modelos Utilizados
1. **Regressão Logística**
   - Necessita de normalização para escalas homogêneas.
   - Interpretação fácil dos coeficientes, permitindo entender o impacto de cada variável no churn.  
2. **Random Forest**
   - Não necessita de normalização.
   - Captura relações não lineares e interações complexas entre variáveis.
   - Permite análise de importância das variáveis baseada na redução da impureza.

### Justificativas
- Combinação de modelos lineares e baseados em árvores para comparar desempenho.  
- Normalização aplicada apenas onde necessário.  
- Random Forest escolhido por sua robustez e capacidade de lidar com dados mistos.

---
### Boxplots
- Tenure vs Churn: clientes fiéis permanecem mais tempo.
- TotalCharges vs Churn: clientes que gastam mais tendem a permanecer.
- MonthlyCharges vs Churn: mensalidades altas associadas a maior risco de evasão.

### Heatmap de Correlação
- Identificação de variáveis mais correlacionadas com o churn, como tenure, TotalCharges, MonthlyCharges, tipo de contrato e serviços adicionais.

---

### ✅Resultados da Modelagem

**Regressão Logística**
- Acurácia: 0.798
- Precisão (classe 1): 0.64
- Recall (classe 1): 0.55
- F1-score (classe 1): 0.59

**Random Forest**
- Acurácia: 0.786
- Precisão (classe 1): 0.62
- Recall (classe 1): 0.49
- F1-score (classe 1): 0.55

**Interpretação das Variáveis**
Maior risco de evasão:
- Mensalidade elevada
- Contrato mensal
- Fatura digital (Paperless Billing = Sim)
- Pagamento via cheque eletrônico (Electronic Check)
- Ausência de OnlineSecurity e TechSupport
  
Menor risco de evasão:
- Maior tempo de permanência (Tenure)
- Maior TotalCharges acumulado
- Contratos de 1 ou 2 anos

---

### 🎯 Conclusões e Estratégias de Retenção
- Incentivar contratos anuais ou bienais para aumentar fidelização.
- Criar descontos ou pacotes customizados para clientes com mensalidade elevada.
- Oferecer serviços adicionais como segurança online e suporte técnico para reduzir churn.
- Melhorar a experiência de pagamento, principalmente para faturas digitais e cheque eletrônico.
- Implementar programas de engajamento e benefícios para clientes de longo tempo de casa.

---

### ⚙ Como Executar o Notebook
1)Instale as bibliotecas necessárias:

pip install pandas matplotlib seaborn scikit-learn

2)Carregue os dados tratados:

import pandas as pd

df = pd.read_csv("telecom_tratado.csv")

3)Execute o notebook na ordem apresentada para reproduzir análise, visualizações e modelos.

---

Autor: Aline dos Anjos
Data: 2025

