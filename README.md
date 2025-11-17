# Análise de Roubos de Veículos em São Paulo (2012–2022)

Este projeto analisa a evolução dos **roubos de veículos no Estado de São Paulo** entre **2012 e 2022**, utilizando dados oficiais da **Secretaria de Segurança Pública (SSP-SP)**.

O foco é:

* Entender **padrões e tendências** ao longo do tempo
* Avaliar o uso de **modelos de séries temporais (ARIMA/SARIMA)**
* Discutir **limitações reais** desses modelos para apoiar decisões em **segurança pública e planejamento de recursos**

---

## 🎯 Objetivos

* Mapear a **tendência histórica** dos roubos de veículos em SP (2012–2022)
* Identificar **sazonalidades e períodos críticos** (anos/meses com maior incidência)
* Construir e avaliar modelos de **séries temporais** (ARIMA/SARIMA) para previsão
* Discutir **como (e se)** essas previsões podem apoiar decisões de políticas públicas

---

## 🧩 Contexto de Negócio

Roubos de veículos impactam:

* **Segurança da população**
* **Custo do seguro e do crédito**
* **Planejamento de policiamento ostensivo e investigação**

Mesmo com limitações, um modelo preditivo pode ajudar a:

* Planejar ações em **períodos de maior risco**
* **Priorizar regiões e épocas do ano** em estratégias operacionais
* Monitorar se **intervenções** (operações policiais, políticas públicas) estão surtindo efeito ao longo do tempo

> Este projeto foi originalmente desenvolvido como **Trabalho de Conclusão**, e aqui foi reorganizado como **case de portfólio de Data Science**.

---

## 📊 Dados

* **Fonte:** Secretaria de Segurança Pública do Estado de São Paulo (SSP-SP)
* **Período:** janeiro de 2012 a dezembro de 2022
* **Granularidade:** dados mensais de **roubos de veículos**, agregados

### Principais desafios de dados

* Presença de **duplicatas** em cerca de metade dos registros (≈ 51%)
* Diferenças de layout entre arquivos de anos distintos
* Necessidade de **padronizar colunas** para construir uma série temporal contínua
* Tratamento de **valores ausentes** e variáveis pouco informativas

> 🔎 **Ponto forte do projeto:** mostra capacidade de trabalhar com **dados reais, sujos e despadronizados**, desde a coleta até a validação para uso em modelos.

---

## 🧠 Metodologia

1. **Coleta e organização**

   * Download dos dados de roubos de veículos no portal da SSP-SP
   * Organização dos arquivos anuais em estrutura única para análise

2. **Limpeza e pré-processamento**

   * Remoção de **registros duplicados**
   * Exclusão de colunas irrelevantes ou com excesso de valores ausentes
   * Padronização de nomes e tipos de variáveis
   * Agregação dos dados em **série temporal mensal** (2012–2022)

3. **Análise Exploratória (EDA)**

   * Visualização da série ao longo do tempo
   * Identificação de **tendências** (aumento/queda ao longo dos anos)
   * Análise de **sazonalidade** (variação por meses e anos)
   * Discussão de possíveis fatores externos (políticas, operações, contexto macroeconômico)

4. **Modelagem de Séries Temporais**

   * Separação em **conjunto de treino e teste**
   * Teste de estacionariedade e transformações, quando necessário
   * Ajuste de modelos **ARIMA** e **SARIMA** com diferentes combinações de parâmetros
   * Comparação com **baselines simples** (ex.: últimos valores / médias sazonais)

5. **Avaliação**

   * Avaliação dos modelos em métricas como **MAPE, MAE, RMSE** e **R²**
   * Comparação entre ARIMA, SARIMA e baselines
   * Análise visual das previsões vs. valores observados em período de teste
   * Discussão honesta sobre **limitações de precisão** e riscos de uso operacional

6. **Discussão e implicações**

   * Interpretação dos resultados do ponto de vista de **segurança pública**
   * O que o modelo ajuda a enxergar, mesmo com erro relativamente alto
   * Ideias de **próximos passos** para aumentar valor de negócio

---

## 📈 Principais Insights

* A série de roubos de veículos apresenta **tendências claras ao longo dos anos**, com períodos de alta e posterior redução em determinados intervalos.
* Existe **sazonalidade**: alguns meses/anos mostram picos recorrentes, o que é relevante para planejamento operacional.
* **Modelos ARIMA/SARIMA conseguem capturar parte do comportamento da série**, mas com erros que ainda limitam o uso para decisões finas (como alocação precisa de viaturas em nível muito granular).
* Mesmo com limitações, o modelo pode ser útil como **ferramenta de apoio** em:

  * Monitorar mudança de tendência
  * Fazer cenários (otimista, base, pessimista)
  * Apoiar discussões de políticas públicas com base em dados

> 💡 Este projeto reforça mais a **capacidade analítica e estatística aplicada** do que a ideia de “modelo perfeito de previsão”.

---

## 🤖 Modelos Utilizados

* **ARIMA (AutoRegressive Integrated Moving Average)**
* **SARIMA (Seasonal ARIMA)**

**Pontos fortes:**

* Adequados para **séries temporais univariadas**
* Permitem incorporar **tendência e sazonalidade**

**Limitações observadas no projeto:**

* **Sensibilidade à escolha de parâmetros (p, d, q, P, D, Q, s)**
* Desempenho limitado em alguns períodos de teste
* Falta de variáveis explicativas externas (mudanças de política, fatores econômicos, etc.)

---

## ✅ O que este projeto demonstra sobre meu perfil

* Capacidade de trabalhar com **dados públicos reais**, com problemas de qualidade (duplicatas, NA, formatos diferentes)
* **Formação forte em análise quantitativa**, com:

  * Graduação em **Gestão Financeira**
  * Pós-graduação em **Estatística Aplicada** (Anhanguera)
  * Pós-graduação em **Ciência de Dados** (USP)
* Atuação em **projetos autorais de portfólio** focados em análise e ciência de dados
* Habilidade de **conectar análise de dados a contexto de negócio**, discutindo implicações para segurança pública, risco e finanças
* Postura **honesta e crítica** com relação aos modelos:

  * não inflar resultados
  * explicitar limitações
  * propor próximos passos realistas

---

## ⚠️ Limitações

* Modelo univariado (somente contagem de roubos de veículos ao longo do tempo)
* Não considera variáveis externas (ex.: operações policiais específicas, mudanças legais, eventos econômicos)
* Nível de erro ainda **alto para uso operacional direto** em decisões finas
* Não há, neste repositório, foco em **deploy em produção** (API, MLOps, etc.) – o foco é **análise e modelagem exploratória**

---

## 🚀 Próximos Passos

* Incluir **variáveis externas** (indicadores econômicos, demográficos, políticas de segurança)
* Testar modelos adicionais de previsão:

  * Regressão com componentes sazonais
  * Modelos baseados em árvores (Gradient Boosting)
  * Outras abordagens específicas para séries temporais
* Explorar recortes mais granulares:

  * Por região/bairro
  * Por tipo de veículo
* Construir um **dashboard interativo** (ex.: Power BI ou web app) para visualização de tendências e cenários

---

## 🗂 Estrutura Sugerida do Repositório

**data/**

* **planilhas_mensais** – arquivos originais da SSP-SP
* **agrupando_dados.ipynb** – Notebook utilizado para ler todas as 132 planilhas, tratar e unificar em um único dataset consolidado

**notebooks/**

* **Analise_Roubos_Carros.ipynb** – Análise exploratória / Modelagem e avaliação

**README.md** – Este arquivo, com a documentação do projeto, contexto de negócio, metodologia e principais insights

---

## 🧑‍💻 Sobre mim

Estou em **transição de carreira para a área de Dados (Análise e Ciência de Dados)**.
Sou **formado em Gestão Financeira** e tenho pós-graduação em **Estatística Aplicada** (Anhanguera) e **Ciência de Dados** (USP).

Tenho interesse especial em:

* **Segurança pública, risco e finanças**
* **Modelagem preditiva, séries temporais e análise de dados em contexto real**

Este projeto faz parte do meu **portfólio** e representa meu jeito de trabalhar:
**dados reais, método estatístico aplicado, transparência sobre limitações e foco em apoiar decisões.**
