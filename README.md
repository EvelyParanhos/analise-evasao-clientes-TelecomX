# Análise de Churn de Clientes na Telecom X

## 📊 Visão Geral do Projeto

Este projeto consiste em uma Análise Exploratória de Dados (EDA) aprofundada para entender os fatores que levam à evasão de clientes (churn) em uma empresa de telecomunicações fictícia, a Telecom X. O objetivo principal é identificar padrões e características de clientes que cancelam seus serviços, fornecendo insights valiosos que possam subsidiar a criação de estratégias de retenção mais eficazes e o desenvolvimento de modelos preditivos.

## 🎯 Objetivo

Analisar os dados de clientes da Telecom X para:
* Compreender a distribuição e a taxa geral de churn.
* Identificar variáveis categóricas e numéricas que possuem forte correlação com a decisão de churn.
* Extrair insights acionáveis para a tomada de decisão estratégica e para a fase de modelagem preditiva.

## ⚙️ Metodologia

O projeto seguiu as principais etapas de um pipeline de Data Science:

1.  **Extração de Dados (E do ETL):** Os dados foram obtidos de uma API no formato JSON, representando informações de clientes, seus serviços e status de churn.
2.  **Transformação e Limpeza de Dados (T e L do ETL):**
    * Normalização de dados aninhados presentes no JSON para um formato tabular.
    * Tratamento de valores ausentes e inconsistências (ex: valores em branco em colunas numéricas ou booleanas).
    * Padronização de tipos de dados (ex: strings 'Yes'/'No' para booleanos `True`/`False`, conversão de `TotalCharges` para numérico).
    * Tratamento de categorias específicas como 'No internet service' ou 'No phone service' para consistência.
3.  **Análise Exploratória de Dados (EDA):**
    * Cálculo da taxa de churn geral.
    * Análise da distribuição de churn em relação a diversas variáveis categóricas (gênero, tipo de contrato, método de pagamento, serviços adicionais, etc.) utilizando gráficos de barras agrupadas.
    * Análise da distribuição de churn em relação a variáveis numéricas (tempo de cliente, cobranças mensais, cobranças totais) utilizando histogramas e KDE plots interativos com Plotly Express.

## 📈 Principais Descobertas e Insights

A análise revelou diversos fatores que influenciam significativamente o churn:

* **Contrato:** Clientes com **contrato Mês a Mês** (`Month-to-month`) são o grupo de **maior risco de churn**, apresentando uma taxa drasticamente mais alta (aprox. 42.7%) em comparação com contratos anuais ou bienais.
    ![Distribuição de Churn por Contract](images/Distribuição de Churn por Contract.png)
    *(Caminho da imagem sugerido: `images/Distribuição de Churn por Contract.png`. Altere conforme a localização real da sua imagem no repositório.)*

* **Tempo de Cliente (`tenure`):** A maioria dos clientes que churnam está na faixa de **poucos meses de serviço**. Os primeiros meses são críticos para a retenção.
    ![Distribuição de Churn por tenure](images/Distribuição de Churn por tenure.png)
    *(Caminho da imagem sugerido: `images/Distribuição de Churn por tenure.png`)*

* **Método de Pagamento:** Clientes que utilizam **"Electronic check"** como método de pagamento possuem uma taxa de churn significativamente mais elevada (aprox. 45.3%).
    ![Distribuição de Churn por PaymentMethod](images/Distribuição de Churn por PaymentMethod.png)
    *(Caminho da imagem sugerido: `images/Distribuição de Churn por PaymentMethod.png`)*

* **Serviço de Internet (Fibra Óptica) e Cobranças Mensais Elevadas:** Clientes com serviço de **Fibra Óptica** e aqueles com **altas cobranças mensais** (geralmente associadas a este serviço) apresentam taxas de churn preocupantes (aprox. 41.9% para Fibra Óptica). Isso pode indicar problemas de qualidade ou valor percebido.
    ![Distribuição de Churn por InternetService](images/Distribuição de Churn por InternetService.png)
    *(Caminho da imagem sugerido: `images/Distribuição de Churn por InternetService.png`)*
    ![Distribuição de Churn por Charges.Monthly](images/Distribuição de Churn por Charges.Monthly.png)
    *(Caminho da imagem sugerido: `images/Distribuição de Churn por Charges.Monthly.png`)*

* **Serviços de Valor Agregado:** A **ausência** de serviços como **Segurança Online**, **Suporte Técnico**, **Backup Online** e **Proteção de Dispositivo** aumenta a propensão ao churn. Estes serviços parecem criar maior "aderência" do cliente à empresa.
    ![Distribuição de Churn por OnlineSecurity](images/Distribuição de Churn por OnlineSecurity.png)
    *(Caminho da imagem sugerido: `images/Distribuição de Churn por OnlineSecurity.png`)*
    ![Distribuição de Churn por TechSupport](images/Distribuição de Churn por TechSupport.png)
    *(Caminho da imagem sugerido: `images/Distribuição de Churn por TechSupport.png`)*

* **Perfil Demográfico:** Clientes **seniores**, **sem parceiro** e **sem dependentes** mostraram maior tendência ao churn.
    ![Distribuição de Churn por SeniorCitizen](images/Distribuição de Churn por SeniorCitizen.png)
    *(Caminho da imagem sugerido: `images/Distribuição de Churn por SeniorCitizen.png`)*

* **Fatura Sem Papel (`PaperlessBilling`):** Curiosamente, clientes que optam pela fatura sem papel têm uma taxa de churn maior, um ponto a ser investigado.
    ![Distribuição de Churn por PaperlessBilling](images/Distribuição de Churn por PaperlessBilling.png)
    *(Caminho da imagem sugerido: `images/Distribuição de Churn por PaperlessBilling.png`)*

## 💡 Recomendações Estratégicas

Com base nos insights obtidos, as seguintes recomendações são propostas para a Telecom X:

1.  **Programas de Onboarding e Engajamento para Novos Clientes:** Implementar um acompanhamento proativo nos primeiros 6 meses de serviço, oferecendo suporte personalizado e garantindo a satisfação.
2.  **Incentivo a Contratos de Longo Prazo:** Criar ofertas e descontos atraentes para que clientes com contrato mês a mês migrem para planos de 1 ou 2 anos.
3.  **Avaliação e Melhoria da Experiência da Fibra Óptica:** Investigar profundamente as causas de insatisfação entre clientes de fibra, focando em qualidade de serviço, estabilidade e suporte.
4.  **Revisão do Método de Pagamento "Electronic Check":** Analisar o processo de pagamento via cheque eletrônico em busca de pontos de atrito ou insatisfação, e considerar incentivos para migração para métodos de pagamento automáticos mais estáveis.
5.  **Promoção Ativa de Serviços Agregados:** Comunicar de forma eficaz os benefícios da Segurança Online, Suporte Técnico, Backup e Proteção de Dispositivo, incentivando sua adesão para aumentar a lealdade.
6.  **Estratégias de Retenção Segmentadas:** Desenvolver abordagens específicas para perfis de alto risco, como clientes seniores, solteiros e sem dependentes, buscando atender às suas necessidades específicas.
7.  **Estudo sobre Fatura Sem Papel:** Investigar o motivo da maior taxa de churn entre esses clientes. Pode ser que sejam mais sensíveis a ofertas digitais de concorrentes ou que a experiência digital precise ser aprimorada.

## 🛠️ Tecnologias Utilizadas

* **Python:** Linguagem de programação principal.
* **Pandas:** Manipulação e análise de dados.
* **Requests:** Requisições a APIs para coleta de dados.
* **Matplotlib:** Geração de gráficos estáticos (para referência em relatórios).
* **Seaborn:** Geração de gráficos estatísticos estáticos com visual mais atraente.
* **Plotly Express:** Geração de gráficos interativos para uma análise exploratória mais dinâmica.

## 🚀 Próximos Passos (Sugestões para o Futuro)

* **Modelagem Preditiva:** Utilizar os insights e as features mais relevantes para construir e treinar modelos de Machine Learning (e.g., Regressão Logística, Random Forest, XGBoost) para prever o churn de clientes.
* **Testes A/B:** Implementar as recomendações como Testes A/B para medir seu impacto real na redução do churn.
