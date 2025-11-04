# 📊 Análise do Funil de Vendas com Teste A/B

## Contexto do Projeto
Este projeto realiza uma **Análise Exploratória de Dados (EDA)** e um **Teste A/B** para avaliar o impacto da alteração de fonte no aplicativo de uma startup de produtos alimentícios.  

O objetivo é identificar se a mudança visual influenciou o comportamento dos usuários ao longo do funil de conversão, desde o acesso à tela principal até a finalização do pagamento.

## 🎯 Objetivos da análise
1. Analisar o comportamento dos usuários no app antes e depois da alteração de fonte.  
2. Avaliar a taxa de conversão entre as etapas do funil de vendas.  
3. Realizar um teste A/B para determinar se a nova fonte gerou diferença estatisticamente significativa na conversão.  

## 🧩 Estrutura do Funil de Eventos
Os eventos registrados no aplicativo correspondem às principais etapas do funil de vendas:

| Evento (original) | Descrição |
|--------------------|-----------|
| `MainScreenAppear` | Aparecimento na tela principal |
| `OffersScreenAppear` | Visualização de ofertas |
| `CartScreenAppear` | Visualização do carrinho |
| `PaymentScreenSuccessful` | Pagamento concluído |
| `Tutorial` | Tela de tutorial (não considerada no funil principal) |

As etapas consideradas no funil principal são da tela principal até o pagamento concluído.

## ⚙️ Metodologia

### 1. **Preparação dos Dados**
- Leitura e consolidação de logs de eventos.  
- Verificação de valores ausentes e duplicados.  
- Criação de colunas derivadas (data/hora, dia da semana).  
- Padronização de nomes e formatação de datas.  

### 2. **Análise Exploratória**
- Contagem e distribuição de eventos por tipo e por usuário.  
- Identificação de períodos representativos do experimento (7 dias).  
- Visualização de padrões de acesso por dia e hora.  

### 3. **Análise do Funil**
- Contagem de usuários que completam cada etapa.  
- Cálculo de taxas de conversão e perdas cumulativas.  
- Visualização gráfica do funil.

### 4. **Teste A/B**
- Grupos:
  - 246 e 247 → grupos de controle  
  - 248 → grupo de teste  
- Hipóteses:
  - H₀: não há diferença na taxa de conversão entre os grupos.  
  - H₁: há diferença na taxa de conversão entre os grupos.  
- Teste estatístico: `proportions_ztest` com nível de significância de 5%.  
- Intervalos de confiança calculados com `proportion_confint`.

## 📈 Principais Resultados e Insights

- Os eventos mais frequentes foram “MainScreenAppear”, “OffersScreenAppear” e “CartScreenAppear”.  
- A maior perda de usuários ocorreu entre as telas de ofertas e carrinho, indicando um ponto de fricção no processo de compra.  
- O teste A/B mostrou diferença não significativa entre os grupos, ou seja, a mudança de fonte não impactou de forma relevante a taxa de conversão.  
- O funil se comporta de maneira estável entre os grupos, sugerindo que a experiência visual teve impacto neutro sobre o comportamento do usuário.

## 🛠️ Tecnologias e Bibliotecas Utilizadas

O projeto foi desenvolvido em **Python**, utilizando as seguintes bibliotecas:
- **Pandas** → manipulação de dados  
- **NumPy** → operações numéricas  
- **Matplotlib**, **Seaborn** e **Plotly** → visualizações estáticas e interativas  
- **SciPy** e **StatsModels** → testes estatísticos e inferência  
- **Jupyter Notebook** → ambiente de análise  
