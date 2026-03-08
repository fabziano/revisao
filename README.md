## Revisão 

1 - Explique a diferença fundamental entre sistemas OLTP e OLAP e justifique por que não devemos realizar análises complexas diretamente no banco de dados
OLTP.
```
OLTP (Processamento Transacional) foca na operação em tempo real, com alta velocidade de gravação e tabelas normalizadas para garantir integridade. 

OLAP (Processamento Analítico) foca na consulta de dados históricos e velocidade de leitura para análise. 

Não se deve realizar análises complexas no OLTP porque isso consome recursos do sistema "ao vivo", podendo causar lentidão ou travamentos nas transações diárias (como vendas e registros).
```
<audio controls>
  <source src="./audio/1.wav" type="audio/wav">
</audio>

2 - No caso das Drogarias XPTO, os preços eram definidos de forma descentralizada. Como o Business Intelligence centralizou esse processo e quais foram as
principais variáveis utilizadas para a nova estratégia?
```
O BI centralizou o processo ao consolidar dados de diversas fontes descentralizadas. As principais variáveis utilizadas incluem preços da concorrência, margens de lucro, custos de aquisição e sazonalidade para definir uma estratégia de preço única e baseada em fatos.
```
<audio controls>
  <source src="./audio/2.wav" type="audio/wav">
</audio>

3 - Descreva as três etapas do processo ETL e identifique qual delas é a mais crítica quando as fontes de dados possuem formatos diferentes (ex: Sexo como "1" e
"M").
```
As etapas são: Extract (Extração), Transform (Transformação) e Load (Carga). A etapa mais crítica é a Transformação, pois é nela que ocorre a limpeza e padronização (ex: converter "1" e "M" para "Masculino"), garantindo que dados de fontes diferentes falem a mesma língua.
```
<audio controls>
  <source src="./audio/3.wav" type="audio/wav">
</audio>

4 - O que é "Granularidade" em uma tabela fato e por que o ENADE afirma que uma granularidade detalhada é essencial para o sucesso da Inteligência Artificial?
```
Granularidade é o nível de detalhe de um registro na tabela fato. Uma granularidade detalhada (alta) é essencial para a IA porque permite que os algoritmos identifiquem padrões ocultos e comportamentos específicos que seriam perdidos em dados agregados (médias ou totais).
```
<audio controls>
  <source src="./audio/4.wav" type="audio/wav">
</audio>

5 - Diferencie o Esquema Estrela (Star Schema) do Esquema Floco de Neve (Snowflake) em termos de normalização e performance de consulta.
```
O Star Schema é desnormalizado, possuindo uma estrutura simples onde a fato se liga diretamente às dimensões, o que resulta em maior performance de consulta. O Snowflake é normalizado (as dimensões são quebradas em subtabelas), o que economiza espaço em disco, mas reduz a performance devido à necessidade de múltiplos joins.
```
<audio controls>
  <source src="./audio/5.wav" type="audio/wav">
</audio>

6 - Imagine que um gestor está vendo o faturamento anual e quer ver o faturamento por meses e, depois, por dias. Quais operações OLAP ele está realizando?
Explique o conceito.
```
O gestor está realizando operações de Drill-Down. O conceito consiste em "mergulhar" nos dados, aumentando o nível de detalhe dentro de uma hierarquia dimensional (ex: tempo).
```
<audio controls>
  <source src="./audio/6.wav" type="audio/wav">
</audio>

7 - No exemplo da Seleção Alemã na Copa de 2014, como o Business Intelligence contribuiu para a tomada de decisão técnica?
```
O BI contribuiu através da análise de desempenho estruturado, coletando dados de partidas passadas e métricas de jogadores para otimizar o posicionamento técnico e tático baseado em evidências estatísticas de sucesso.
```
<audio controls>
  <source src="./audio/7.wav" type="audio/wav">
</audio>

8 - Por que um Data Warehouse (DW) é considerado um repositório "orientado por assunto" e "não volátil"?
```
Orientado por assunto: Organizado em torno de temas principais da empresa (Vendas, Produtos, Clientes), ignorando dados que não são úteis para o processo de decisão.
Não volátil: Uma vez que o dado entra no DW, ele não é alterado ou excluído; ele serve como um registro histórico permanente.
```
<audio controls>
  <source src="./audio/8.wav" type="audio/wav">
</audio>

9 - Explique o conceito de "Sistemas Especialistas" e discuta por que a probabilidade em uma regra "Se-Então" aplica-se ao indivíduo e não necessariamente ao
grupo.
```
Sistemas Especialistas emulam o raciocínio humano através de regras lógicas. A probabilidade aplica-se ao indivíduo porque, embora um grupo tenha uma tendência média, cada indivíduo possui variáveis específicas que determinam sua probabilidade única de ocorrência em uma regra de negócio.
```
<audio controls>
  <source src="./audio/9.wav" type="audio/wav">
</audio>

10 - Uma empresa de telecomunicações quer prever o Churn (cancelamento). Qual a diferença entre usar Análise Descritiva e Análise Preditiva para este problema?
```
A Análise Descritiva informa quantos clientes cancelaram no passado e quais as características deles. A Análise Preditiva utiliza esses dados históricos para identificar quais dos clientes atuais têm maior probabilidade de cancelar no futuro próximo.
```
<audio controls>
  <source src="./audio/10.wav" type="audio/wav">
</audio>

11 - O que é "Data Storytelling" e por que conhecer o público-alvo é a regra mais importante desta prática?
```
Data Storytelling é a arte de construir uma narrativa em torno dos dados para facilitar a compreensão. Conhecer o público-alvo é a regra mais importante porque o nível de detalhe técnico e o tipo de visualização devem ser adaptados para quem vai consumir a informação (ex: um CEO precisa de visões diferentes de um analista técnico).
```
<audio controls>
  <source src="./audio/11.wav" type="audio/wav">
</audio>

12 - Em um projeto de IA, os analistas notaram que o modelo estava "viciado" (com viés) para certas regiões. Como a qualidade e a representatividade dos dados no Data Warehouse influenciam este resultado?
```
Se os dados no DW forem incompletos, viciados ou não representarem todas as regiões, a IA aprenderá esses mesmos preconceitos. A qualidade e representatividade dos dados são o alicerce; dados "sujos" ou parciais resultam em modelos de IA injustos ou errôneos.
```
<audio controls>
  <source src="./audio/12.wav" type="audio/wav">
</audio>

13 - Discuta a afirmação: "A Inteligência Artificial vai substituir completamente os analistas de dados". Utilize os conceitos de julgamento crítico e contexto.
```
A IA não substituirá completamente os analistas porque, embora seja superior em processamento e cálculos, ela carece de julgamento crítico e contexto. O analista humano é necessário para interpretar os resultados dentro da realidade do negócio e tomar decisões éticas e criativas.
```
<audio controls>
  <source src="./audio/13.wav" type="audio/wav">
</audio>

14 - Qual a função das "Surrogate Keys" (Chaves Artificiais) na modelagem dimensional e por que não devemos usar apenas as chaves originais do sistema
transacional?
```
A função da SK é criar uma chave primária interna para o BI (independente do sistema de origem). Não se deve usar a chave original porque, se o sistema transacional mudar ou for substituído, o histórico e as ligações entre as tabelas no DW seriam perdidos.
```
<audio controls>
  <source src="./audio/14.wav" type="audio/wav">
</audio>

15 - Explique como a análise "Prescritiva" vai um passo além da análise "Preditiva". Dê um exemplo prático baseado em logística ou varejo
```
A Preditiva indica o que vai acontecer (ex: "A demanda por este produto aumentará 30%"). 

A Prescritiva sugere a ação (ex: "Aumente o estoque em 30% e contrate dois entregadores extras"). No varejo, isso pode significar ajustar preços dinamicamente com base na previsão de estoque e concorrência.
```
<audio controls>
  <source src="./audio/15.wav" type="audio/wav">
</audio>