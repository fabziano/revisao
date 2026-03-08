## [https://fabziano.github.io/revisao/](https://fabziano.github.io/revisao/)

## Revisão

**O QUE É BI?**
* Business Intelligence não é apenas um software (como Power BI ou Tableau).
* É um processo estratégico que utiliza tecnologia para coletar, organizar, analisar e compartilhar dados.
* O objetivo final é um só: suportar a tomada de decisão baseada em fatos, e não em intuições.
* **BI (O Olhar Estruturado):** Foca em dados estruturados (tabelas), relatórios e no "que aconteceu". Exemplo: Seleção alemã analisando desempenho passado para ganhar a Copa.
* **Data Science (O Olhar Preditivo):** Lida com dados não estruturados (textos, vídeos, áudios) e usa Machine Learning para prever o futuro e descobrir padrões ocultos.

---

**OLTP vs. OLAP**
* **OLTP (Processamento Transacional Online):** Sistema operacional "ao vivo" que registra as transações no momento em que acontecem.
    * Foco: Velocidade de gravação e integridade. Não pode haver erro no estoque ou no caixa.
    * Estrutura: Tabelas Normalizadas. Dados quebrados em tabelas pequenas para evitar redundância.
    * Exemplo: Registro de venda via código de barras.
* **OLAP (Processamento Analítico Online):** Sistema de análise que consulta milhões de vendas passadas.
    * Foco: Velocidade de leitura e resposta a perguntas complexas.
    * Estrutura: Tabelas Desnormalizadas (Multidimensionais).
    * Exemplo: Painel de lucro líquido por estado e período.

---

**O FLUXO ETL (A FÁBRICA DE DADOS)**
* Os dados no OLTP estão "sujos" para análise e passam pelo processo ETL para ir ao Data Warehouse (DW).
* **1) Extract (Extração):** Copia dados de várias fontes (SQL, Excel, CSV, redes sociais).
* **2) Transform (Transformação):** Etapa mais importante.
    * Limpeza: Remove registros duplicados ou incompletos.
    * Padronização: Converte formatos distintos (ex: "1" e "M" para "Masculino").
    * Cálculos: Calcula margens ou impostos não prontos na origem.
* **3) Load (Carga):** Dados limpos são despejados no Data Warehouse.

---

**MODELAGEM DIMENSIONAL (STAR SCHEMA)**
* No BI, utiliza-se o Star Schema (Esquema Estrela).
* **1) Tabela Fato (Centro):** Contém métricas como quantidade vendida, valor pago e tempo de espera.
    * **Granularidade:** Nível de detalhe. Alta (detalhada) ou baixa (agregada). Prefira sempre a granularidade mais detalhada possível.
* **2) Tabelas Dimensão (Pontas):** Contêm características descritivas para filtros (ex: dim_produto, dim_tempo, dim_cliente).
* **Snowflake Schema:** Variação do modelo dimensional com dimensões normalizadas.

---

**NAVEGANDO NO CUBO (OPERAÇÕES OLAP)**
1. **Slice (Fatiar):** Seleciona uma fatia (ex: apenas o ano de 2024).
2. **Dice (Dados):** Seleciona um sub-cubo (ex: Notebooks em Foz do Iguaçu em Janeiro).
3. **Drill-Down:** Aumenta o detalhe (ex: de Ano para Mês, depois para Dia).
4. **Roll-Up:** Diminuir o detalhe/agrupar (ex: de Cidades para Estado).
5. **Pivot:** Gira o relatório (muda linhas por colunas).

---

**MATURIDADE ANALÍTICA E IA**
1. **Análise Descritiva:** "O que aconteceu?".
2. **Análise Diagnóstica:** "Por que aconteceu?" (causa raiz).
3. **Análise Preditiva:** "O que vai acontecer?" (IA e estatística).
4. **Análise Prescritiva:** "O que devemos fazer?" (sugestão de ação).
* A IA automatiza o repetitivo; o humano entra com julgamento crítico, criatividade e contexto.

---

**REGRAS DE OURO DE KIMBALL**
1) Sempre inclua uma dimensão de Tempo.
2) Toda medida na Tabela Fato deve ter a mesma granularidade.
3) Dados detalhados (alta granularidade) são melhores para consultas flexíveis.

---

**DICAS**
* **Surrogate Key (SK):** Chave própria do BI (1, 2, 3...). Nunca use apenas a chave do sistema original.
* **SCD (Slowly Changing Dimension):** Tratamento de mudanças. SCD Tipo 2 mantém histórico criando uma nova linha.
* **Governança:** Garante que definições (ex: "Lucro") sejam iguais para todos os departamentos.
* **MOLAP vs ROLAP:** MOLAP é mais rápido porque já guarda os dados em um "Cubo" pronto.
* **Análise de Diagnóstico:** Associada à operação de Drill-down para achar a causa raiz.
* **KDD (Descoberta de Conhecimento):** Tem como núcleo a Mineração de Dados (Data Mining).
* **Churn:** Nome técnico para cancelamento de clientes.
* **Dashboard de Transparência:** Uso de BI para dados públicos (Governo).
* **Viés (Bias):** Erro da IA por dados incompletos ou viciados.

---

**CASO PRÁTICO: REDE DE ACADEMIAS**
* **Cenário:** Perda de alunos (Churn). Dados divididos entre OLTP e planilhas.
* **KPI 1: Taxa de Evasão (Churn Rate):** (Alunos que cancelaram / Total ativos) * 100.
* **KPI 2: Índice de Frequência:** (Total acessos catraca / Alunos matriculados).
* **Modelagem:** Fato Presenca (granularidade por acesso) e Dimensões Aluno, Unidade, Tempo e Modalidade.
* **ETL:** Extração (SQL e CSV), Transformação (Padronizar idades e limpar CPFs) e Carga (DW).
* **Operações OLAP:** Slice (ano 2024), Dice (Mulheres/Curitiba/Yoga), Drill-down (meses com mais faltas), Pivot (Cidades nas colunas).
* **Evolução IA:**
    * Descritiva: Mostra que 20% saíram.
    * Preditiva: Identifica 80% de chance de cancelamento após 15 dias de ausência.
    * Prescritiva: Envia automaticamente cupom ou mensagem de incentivo. 
---
        
## Questões

### 1 - Explique a diferença fundamental entre sistemas OLTP e OLAP e justifique por que não devemos realizar análises complexas diretamente no banco de dados OLTP.

> **OLTP (Processamento Transacional)** foca na operação em tempo real, com alta velocidade de gravação e tabelas normalizadas para garantir integridade.
>
> **OLAP (Processamento Analítico)** foca na consulta de dados históricos e velocidade de leitura para análise. 
>
> Não se deve realizar análises complexas no OLTP porque isso consome recursos do sistema "ao vivo", podendo causar lentidão ou travamentos nas transações diárias (como vendas e registros).

<audio src="https://raw.githubusercontent.com/fabziano/revisao/main/audio/1.wav" controls></audio>

---

### 2 - No caso das Drogarias XPTO, os preços eram definidos de forma descentralizada. Como o Business Intelligence centralizou esse processo e quais foram as principais variáveis utilizadas para a nova estratégia?

> O BI centralizou o processo ao consolidar dados de diversas fontes descentralizadas. As principais variáveis utilizadas incluem preços da concorrência, margens de lucro, custos de aquisição e sazonalidade para definir uma estratégia de preço única e baseada em fatos.

<audio src="https://raw.githubusercontent.com/fabziano/revisao/main/audio/2.wav" controls></audio>

---

### 3 - Descreva as três etapas do processo ETL e identifique qual delas é a mais crítica quando as fontes de dados possuem formatos diferentes (ex: Sexo como "1" e "M").

> As etapas são: **Extract (Extração)**, **Transform (Transformação)** e **Load (Carga)**. A etapa mais crítica é a Transformação, pois é nela que ocorre a limpeza e padronização (ex: converter "1" e "M" para "Masculino"), garantindo que dados de fontes diferentes falem a mesma língua.

<audio src="https://raw.githubusercontent.com/fabziano/revisao/main/audio/3.wav" controls></audio>

---

### 4 - O que é "Granularidade" em uma tabela fato e por que o ENADE afirma que uma granularidade detalhada é essencial para o sucesso da Inteligência Artificial?

> Granularidade é o nível de detalhe de um registro na tabela fato. Uma granularidade detalhada (alta) é essencial para a IA porque permite que os algoritmos identifiquem padrões ocultos e comportamentos específicos que seriam perdidos em dados agregados (médias ou totais).

<audio src="https://raw.githubusercontent.com/fabziano/revisao/main/audio/4.wav" controls></audio>

---

### 5 - Diferencie o Esquema Estrela (Star Schema) do Esquema Floco de Neve (Snowflake) em termos de normalização e performance de consulta.

> O **Star Schema** é desnormalizado, possuindo uma estrutura simples onde a fato se liga diretamente às dimensões, o que resulta em maior performance de consulta. O **Snowflake** é normalizado (as dimensões são quebradas em subtabelas), o que economiza espaço em disco, mas reduz a performance devido à necessidade de múltiplos joins.

<audio src="https://raw.githubusercontent.com/fabziano/revisao/main/audio/5.wav" controls></audio>

---

### 6 - Imagine que um gestor está vendo o faturamento anual e quer ver o faturamento por meses e, depois, por dias. Quais operações OLAP ele está realizando? Explique o conceito.

> O gestor está realizando operações de **Drill-Down**. O conceito consiste em "mergulhar" nos dados, aumentando o nível de detalhe dentro de uma hierarquia dimensional (ex: tempo).

<audio src="https://raw.githubusercontent.com/fabziano/revisao/main/audio/6.wav" controls></audio>

---

### 7 - No exemplo da Seleção Alemã na Copa de 2014, como o Business Intelligence contribuiu para a tomada de decisão técnica?

> O BI contribuiu através da análise de desempenho estruturado, coletando dados de partidas passadas e métricas de jogadores para otimizar o posicionamento técnico e tático baseado em evidências estatísticas de sucesso.

<audio src="https://raw.githubusercontent.com/fabziano/revisao/main/audio/7.wav" controls></audio>

---

### 8 - Por que um Data Warehouse (DW) é considerado um repositório "orientado por assunto" e "não volátil"?

> **Orientado por assunto:** Organizado em torno de temas principais da empresa (Vendas, Produtos, Clientes), ignorando dados que não são úteis para o processo de decisão.
**Não volátil:** Uma vez que o dado entra no DW, ele não é alterado ou excluído; ele serve como um registro histórico permanente.

<audio src="https://raw.githubusercontent.com/fabziano/revisao/main/audio/8.wav" controls></audio>

---

### 9 - Explique o conceito de "Sistemas Especialistas" e discuta por que a probabilidade em uma regra "Se-Então" aplica-se ao indivíduo e não necessariamente ao grupo.

> Sistemas Especialistas emulam o raciocínio humano através de regras lógicas. A probabilidade aplica-se ao indivíduo porque, embora um grupo tenha uma tendência média, cada indivíduo possui variáveis específicas que determinam sua probabilidade única de ocorrência em uma regra de negócio.

<audio src="https://raw.githubusercontent.com/fabziano/revisao/main/audio/9.wav" controls></audio>

---

### 10 - Uma empresa de telecomunicações quer prever o Churn (cancelamento). Qual a diferença entre usar Análise Descritiva e Análise Preditiva para este problema?

> A **Análise Descritiva** informa quantos clientes cancelaram no passado e quais as características deles. A **Análise Preditiva** utiliza esses dados históricos para identificar quais dos clientes atuais têm maior probabilidade de cancelar no futuro próximo.

<audio src="https://raw.githubusercontent.com/fabziano/revisao/main/audio/10.wav" controls></audio>

---

### 11 - O que é "Data Storytelling" e por que conhecer o público-alvo é a regra mais importante desta prática?

> Data Storytelling é a arte de construir uma narrativa em torno dos dados para facilitar a compreensão. Conhecer o público-alvo é a regra mais importante porque o nível de detalhe técnico e o tipo de visualização devem ser adaptados para quem vai consumir a informação.

<audio src="https://raw.githubusercontent.com/fabziano/revisao/main/audio/11.wav" controls></audio>

---

### 12 - Em um projeto de IA, os analistas notaram que o modelo estava "viciado" (com viés) para certas regiões. Como a qualidade e a representatividade dos dados no Data Warehouse influenciam este resultado?

> Se os dados no DW forem incompletos, viciados ou não representarem todas as regiões, a IA aprenderá esses mesmos preconceitos. A qualidade e representatividade dos dados são o alicerce; dados "sujos" ou parciais resultam em modelos de IA injustos ou errôneos.

<audio src="https://raw.githubusercontent.com/fabziano/revisao/main/audio/12.wav" controls></audio>

---

### 13 - Discuta a afirmação: "A Inteligência Artificial vai substituir completamente os analistas de dados". Utilize os conceitos de julgamento crítico e contexto.

> A IA não substituirá completamente os analistas porque, embora seja superior em processamento e cálculos, ela carece de julgamento crítico e contexto. O analista humano é necessário para interpretar os resultados dentro da realidade do negócio e tomar decisões éticas e criativas.

<audio src="https://raw.githubusercontent.com/fabziano/revisao/main/audio/13.wav" controls></audio>

---

### 14 - Qual a função das "Surrogate Keys" (Chaves Artificiais) na modelagem dimensional e por que não devemos usar apenas as chaves originais do sistema transacional?

> A função da SK é criar uma chave primária interna para o BI (independente do sistema de origem). Não se deve usar a chave original porque, se o sistema transacional mudar ou for substituído, o histórico e as ligações entre as tabelas no DW seriam perdidos.

<audio src="https://raw.githubusercontent.com/fabziano/revisao/main/audio/14.wav" controls></audio>

---

### 15 - Explique como a análise "Prescritiva" vai um passo além da análise "Preditiva". Dê um exemplo prático baseado em logística ou varejo.

> A **Preditiva** indica o que vai acontecer (ex: "A demanda aumentará 30%").
>
> A **Prescritiva** sugere a ação (ex: "Aumente o estoque em 30% e contrate dois entregadores extras"). No varejo, isso pode significar ajustar preços dinamicamente com base na previsão de estoque e concorrência.

<audio src="https://raw.githubusercontent.com/fabziano/revisao/main/audio/15.wav" controls></audio>



