# Poder Aquisitivo vs Saúde Mental vs Big Mac Index 🍔

Análise do poder de compra do trabalhador em diferentes países,
cruzando o Big Mac Index (The Economist) com dados de salário mínimo global
para entender se existe uma relação entre saúde mental e situação econômica.

## Dataset

- [Big Mac Index - The Economist (Github)](https://github.com/TheEconomist/big-mac-data)
- [Minimum Wage by Country (Kaggle)](https://www.kaggle.com/datasets/peipeichen/minimum-wage-by-country)
- [Vendas de Remédios Antidepressivos e Ansiolíticos](https://console.cloud.google.com/bigquery?p=basedosdados&d=br_anvisa_medicamentos_industrializados&t=microdados&page=table)
- [Remuneração média por ano/trimestre](https://console.cloud.google.com/bigquery?p=basedosdados&d=br_ibge_pnadc&t=microdados&page=table)
- [Minimum Wage by Country (Kaggle)](https://www.kaggle.com/datasets/peipeichen/minimum-wage-by-country)

## Tecnologias

- Python, Pandas, Matplotlib, Seaborn
- Google Colab

## Novos planos

Fonte da dados: medicamentos vendidos entre 2014 e 2021
Fazer relação com o aumento de custo de vida
CID 9 para TRANSTORNOS DEPRESSIVOS NCOP = 311

## Como identificar via CID 10 casos de doenças psiquiatricas

Identificar transtornos mentais na CID-10 (Classificação Internacional de Doenças, 10ª edição) envolve focar principalmente no Capítulo V, que abrange os códigos de F00 a F99. Para busca em bases de dados (como SUS/DATASUS), é necessário utilizar subcategorias específicas para depressão, ansiedade e burnout.

Aqui está um guia prático para buscar esses códigos:

1. Estrutura Geral (Capítulo V: F00-F99)

F00-F09: Transtornos mentais orgânicos (demência, delirium).
F10-F19: Transtornos mentais devidos ao uso de substâncias.
F20-F29: Esquizofrenia, transtornos esquizotípicos e delirantes.
F30-F39: Transtornos do humor (afetivos) - Depressão/Bipolaridade.
F40-F48: Transtornos neuróticos, estresse e somatoformes (Ansiedade, fobias).
F50-F59: Síndromes comportamentais (transtornos alimentares, sono).
F60-F69: Transtornos de personalidade.
F70-F79: Retardo mental.
F99: Transtorno mental não especificado.

2. Códigos para Busca de Dados (Foco: Depressão, Ansiedade, Burnout)
   Para pesquisas em bases de dados, use os códigos abaixo, preferencialmente utilizando a raiz (ex: F32) para capturar variações:

Depressão (F32 - F33)
F32: Episódios Depressivos (inclui leve, moderado, grave).
F32.0, F32.1, F32.2, F32.9 (não especificado).
F33: Transtorno Depressivo Recorrente.

Ansiedade (F41 - F43)
F41: Outros transtornos ansiosos.
F41.0: Transtorno de Pânico.
F41.1: Ansiedade Generalizada.
F41.2: Transtorno misto ansioso e depressivo.
F43: Reações ao Estresse Grave e Transtornos de Adaptação.
F43.1: Estresse Pós-Traumático (TEPT).
F43.2: Transtornos de Adaptação.

Burnout (Esgotamento)
Z73.0: Esgotamento (Burnout) - Este é o código mais utilizado na CID-10 para Burnout, classificado como "Problemas relacionados com a organização de seu modo de vida".

3. Como buscar em Base de Dados (Dicas Técnicas)
   Utilize a Raiz (Fxx): Ao buscar no DATASUS ou prontuários, procure pela "raiz" do código (primeiros 3 caracteres) para incluir as subdivisões. Exemplo: F32% (para buscar F32.0, F32.1, F32.9).
   Combinação de códigos: Frequentemente, o Burnout é registrado como uma combinação de Z73.0 + F43.2 (transtorno de adaptação) ou F32 (depressão).
   Atenção à Mudança CID-11: A partir de 2025, o Brasil adotou o CID-11, onde o burnout (agora com código QD85) foi reclassificado como um fenômeno ocupacional, não uma doença mental em si. Se o dado for anterior a 2025, o foco é Z73.0.

Principais códigos de alerta:
F32.9: Depressão não especificada (altamente comum em atestados).
F41.9: Transtorno ansioso não especificado.
F99: Transtorno mental não especificado.
