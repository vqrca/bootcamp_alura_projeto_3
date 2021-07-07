[![Badge](https://img.shields.io/badge/Author-Valquíria_Alencar-%237159c1?style=flat-square&logo=ghost)](https://github.com/vqrca/) [![Gmail Badge](https://img.shields.io/badge/-valquiria.c.alencar@gmail.com-6633cc?style=flat-square&logo=Gmail&logoColor=white&link=mailto:valquiria.c.alencar@gmail.com)](mailto:valquiria.c.alencar@gmail.com) [![Linkedin Badge](https://img.shields.io/badge/-Valquíria_Alencar-6633cc?style=flat-square&logo=Linkedin&logoColor=white&link=https://www.linkedin.com/in/valquiria-alencar/)](https://www.linkedin.com/in/valquiria-alencar/)

<p align="center">
  <img src="https://github.com/vqrca/bootcamp_alura_projeto_3/blob/main/Images/cover_3.png" />
</p>

# **Sumário:**
<!--ts-->
   * [Introdução](#intro)
   * [Dados](#dados)
   * [Hipóteses](#hip)
   * [Conclusões](#conclusoes)
   * [Considerações finais](#final)
   * [Referências](#ref)
   * [Documentação](#doc)
   * [Agradecimentos](#agra)
   * [Contato](#contact)
   <!--te-->

<a name="intro"></a>
# **Introdução**

Neste projeto apliquei os conhecimentos obtidos no módulo 3 do Bootcamp de Data Science Aplicada da Alura. Todo arcabouço teórico adquirido até aqui foi aplicado para o entendimento das nuances envolvendo as séries temporais. Da estatística descritiva, passando pela análise exploratória e chegando às previsões, utilizando ferramentas específicas para esse tipo de dados, como o StatisModel e Prophet desenvolvido pelo Facebook. 

O Notebook com a análise completa e códigos pode ser encontrado [aqui](https://github.com/vqrca/bootcamp_alura_projeto_3/blob/main/Notebooks/Projeto_3_Valquiria_Alencar.ipynb). 
> Recomendo que seja aberto pelo google colab para melhorar a visualização! 

Uma publicação sumarizando as análises, sem conter os códigos e etapas de tratamento dos dados, pode ser encontrada na minha página do [Medium](https://medium.com/p/fefbc0d385cc).

## **Contexto: Pandemia causada pelo novo coronavírus SARS-CoV-2**
Os coronavírus são um grupo diversificado de vírus que infectam diferentes animais e podem causar infecções respiratórias leves a graves em humanos. Em 2002 e 2012, respectivamente, dois coronavírus altamente patogênicos de origem zoonótica, o coronavírus com síndrome respiratória aguda grave (SARS-CoV) e o  coronavírus com síndrome respiratória do Oriente Médio (MERS-CoV), surgiram em humanos e tornam-se um novo problema de saúde pública no século XXI [[1]](https://www.nature.com/articles/s41579-018-0118-9).
No final de 2019, um novo coronavírus designado como SARS-CoV-2 surgiu na cidade de Wuhan, na China, e causou um surto de pneumonia viral incomum. Por ser altamente transmissível, essa nova doença conhecida como COVID-19, se espalhou rapidamente por todo o mundo. Superou de forma esmagadora o SARS e o MERS em termos de número de pessoas infectadas e da amplitude espacial das áreas epidêmicas. O surto contínuo de COVID-19 representa uma ameaça extraordinária à saúde pública global [[2]](https://www.thelancet.com/journals/lancet/article/PIIS0140-6736(20)30260-9/fulltext). 

Na figura abaixo, pode-se observar uma linha do tempo dos principais eventos relacionados ao início da pandemia:
<p align="center">
  <img src="https://github.com/vqrca/bootcamp_alura_projeto_3/blob/main/Images/linha_tempo.png" />
</p>

*Fonte: Universidade Federal do Rio Grande do Sul - Projeto: Use o R [[3]](https://www.ufrgs.br/user/covid-19/).*

Por ser uma doença altamente contagiosa, a vida em praticamente todo o planeta foi  modificada. Os grandes centros urbanos se transformaram: ruas vazias, o home office se tornou realidade da vida da maioria das pessoas, aulas também se tornaram online e  diversas atividades foram suspensas. O objetivo dessas medidas sempre foi diminuir a transmissão do vírus, na tentativa de achatar a curva de contágio e não permitir um crescimento exponencial desenfreado no número de casos, e consequentemente, no número de óbitos.
A experiência da China mostrou que intervenções não farmacológicas, que incluem diversas formas de distanciamento social, desde o isolamento de casos e contatos, até o bloqueio total (lockdown), poderiam conter a epidemia [[4]](https://www.who.int/docs/default-source/coronaviruse/situation-reports/20200304-sitrep-44-covid-19.pdf?sfvrsn=783b4c9d_2). 

<p align="center"><img src='https://media.giphy.com/media/Qu1fT51CG14ksIkASL/giphy.gif'</p>
	
Todas essas ações foram cruciais até que vacinas fossem desenvolvidas, testadas e finalmente, aplicadas na população!
	
## **Cenário da Pandemia no Brasil**

- No final de fevereiro de 2020, o primeiro caso da doença foi confirmado no Brasil [[5]](https://www.scielosp.org/article/ress/2020.v29n4/e2020376/#). 
  
- Em 20 de março de 2020, o país decretou transmissão comunitária em todo o território nacional [[5]](https://www.scielosp.org/article/ress/2020.v29n4/e2020376/#).
  
- Em maio de 2020, a Covid-19 tornou-se a maior causa de morte no Brasil [[5]](https://www.scielosp.org/article/ress/2020.v29n4/e2020376/#). 
  
- Até a semana epidemiológica 20 a região Norte apresentou as maiores taxas de incidência e mortalidade [[5]](https://www.scielosp.org/article/ress/2020.v29n4/e2020376/#) 
  
- Até a semana epidemiológica 20 o Amazonas apresentou a maior taxa de incidência. 
[[5]](https://www.scielosp.org/article/ress/2020.v29n4/e2020376/#). 
  
- Em 8 de agosto, menos de seis meses depois, o Brasil chegou à triste marca de 100.000 mortes causadas pelo novo coronavírus [[6]](https://brasil.elpais.com/ciencia/2020-07-23/evolucao-dos-casos-de-coronavirus-no-brasil.html).
  
- Em 7 de janeiro de 2021, os óbitos chegaram à marca de 200.000 [[6]](https://brasil.elpais.com/ciencia/2020-07-23/evolucao-dos-casos-de-coronavirus-no-brasil.html).
No início de março de 2021, o país registrou sua semana mais letal desde o início da pandemia, com a média móvel de mortes em torno de 1.500 por dia [[6]](https://brasil.elpais.com/ciencia/2020-07-23/evolucao-dos-casos-de-coronavirus-no-brasil.html).
  
- Em abril de 2021 a média móvel de mortes por Covid passou de 3.000 e o Brasil registrou 3.673 óbitos em 24 horas. A média móvel média bateu recorde pelo 7º dia seguido[[7]](https://www1.folha.uol.com.br/equilibrioesaude/2021/04/media-movel-de-mortes-passa-de-3000-e-brasil-registra-3673-obitos-em-24-h.shtml#:~:text=M%C3%A9dia%20m%C3%B3vel%20de%20mortes%20por,2021%20%2D%20Equil%C3%ADbrio%20e%20Sa%C3%BAde%20%2D%20Folha). 
  
- Recentemente, o Brasil ultrapassou meio milhão de óbitos por SARS-CoV-2 e o número de casos acumulados reportados ultrapassou 17 milhões [[8]](https://covid.saude.gov.br/). 


## **O caso de Amazonas**

No meu [projeto 1: Análise dos Gastos Hospitalares do SUS (Sistema Único de Saúde) e Evolução das Taxas de Mortalidade no Brasil ](https://github.com/vqrca/bootcamp_alura_projeto_1), desenvolvido anteriormente nesse Bootcamp, eu fiz uma análise da evolução das taxas de mortalidade nas Unidades da Federação. Essas análises mostraram que a taxa de mortalidade dobrou em Amazonas em 2021 (apresentando uma taxa de mortalidade de 10.82), quando comparado a 2020 (5.46), consequentemente se tornando o Estado com maior taxa de mortalidade.

O gráfico abaixo foi obtido com os dados dessas análises anteriores:
> O dataset utilizado foi obtido no [Tabnet](http://tabnet.datasus.gov.br/cgi/tabcgi.exe?sih/cnv/qiuf.def) em junho de 2021, e nesse período os dados disponíveis eram de 2007 a março de 2021.

<p align="center">
  <img src="https://github.com/vqrca/bootcamp_alura_projeto_3/blob/main/Images/taxa_mortalidade_final.png" />
</p>

Além disso: 

- O estado do Amazonas, que apresentou as maiores taxas de incidência e de mortalidade por COVID-19, reportou colapso no sistema de saúde e crise no sistema funerário [[9]]( https://saude.estadao.com.br/noticias/geral,amazonas-apresenta-colapso-no-sistema-de-saude-por-causa-do-coronavirus,70003272136). 
  
- Em janeiro de 2021, o Amazonas começou a viver um colapso com a segunda onda, com a falta de oxigênio nos hospitais de Manaus[[6]](https://brasil.elpais.com/ciencia/2020-07-23/evolucao-dos-casos-de-coronavirus-no-brasil.html).

Por esses motivos, esse projeto teve como foco o estado Amazonas! 


<a name="dados"></a>
# **Dados**

## **Coleta dos dados:**

Os dados utilizados neste projeto foram obtidos do [Brasil.io](https://brasil.io/dataset/covid19/caso_full/), um banco de dados que disponibiliza dados acerca dos casos e óbitos de SARS-CoV-2 no Brasil todo.

Eu escolhi o dataset: caso_full, que possui os dados para todos os municípios do país. 

>API: https://brasil.io/api/dataset/covid19/caso_full/data

>Dados completos para download: https://data.brasil.io/dataset/covid19/caso_full.csv.gz

O arquivo *.csv* desse dataset foi salvo no dia 18/06/21 e pode ser encontrado no [Google Drive](https://drive.google.com/drive/folders/1skKBY8LjHj0tL7vk_nZfAQuZ-2G0cDZz).

  
## **Bibliotecas utilizadas e suas respectivas funções**

- Pandas versão 1.1.5: Manipulação dos datasets  
  
- Numpy versão 1.19.5: Cálculos numéricos
  
- Matplotlib versão 3.2.2: Plotar os gráficos
  
- Seaborn versão 0.11.1: Plotar os gráficos
  
- StatsModel: Análise de correlações
  
- Prophet: Previsão de séries temporais
  
- Sckit-learn: Métricas para avaliar os modelos gerados 
  
> O notebook *.ipynb* foi construído no google colab usando Python 3.7.10. 

<a name="hip"></a>
# **Hipóteses**

O objetivo principal deste módulo é a previsão de dados de séries temporais. Essas previsões foram realizadas para o número de novos casos e novos óbitos em Manaus.
De acordo com esse objetivo as seguintes hipóteses foram definidas:


> Hipótese 1: O número de casos novos deve se estabilizar nos próximos meses, devido ao início da vacinação.
  
  
> Hipótese 2: O número de óbitos novos deve começar a cair nos próximos meses, devido ao início da vacinação.
  
<a name="conclusoes"></a>
# **Conclusões**
 
- As análises preliminares desse projeto mostraram que a **Pandemia de COVID-19 no Amazonas é, até o momento, caracterizada por dois picos**:  **a primeira onda começou em março de 2020 e atingiu o pico por volta do início de maio de 2020**, quando o número de casos diminuiu e então permaneceu praticamente estável de junho a novembro de 2020. Porém, **em meados de dezembro o número de casos começou a crescer exponencialmente, configurando a segunda onda da pandemia** 
 
- Os óbitos também tiveram a **primeira onda se iniciando em março de 2020, que atingiu o pico por volta do início de maio de 2020**, quando o número de óbitos diminuiu e então permaneceu praticamente estável de junho a novembro de 2020. Porém, **em meados de dezembro o número de óbitos começou a crescer exponencialmente, configurando a segunda onda**.
 
- Estudos acreditam que **o aumento de casos e óbitos foram impulsionados por uma combinação de diminuições das medidas de distanciamento social e pelo surgimento de uma forma mais transmissível do vírus, a variante P.1**, identificada em meados de novembro de 2020. **Essa variante causou um aumento exponencial da doença, o que estabeleceu a segunda onda da pandemia no estado**.
 
- Várias hipóteses foram propostas para explicar a segunda onda inesperada que resultou no colapso do sistema de saúde em Manaus entre dezembro de 2020 e janeiro de 2021 [[18]](https://www.thelancet.com/article/S0140-6736(21)00183-5/fulltext): Uma hipótese é que a **variante P.1 pode escapar da imunidade gerada em resposta a uma infecção anterior e tem o potencial de reinfectar indivíduos convalescentes**. Embora alguns casos de reinfecção com a variante P.1 tenham sido descritos em Manaus [[19]](https://science.sciencemag.org/content/372/6544/815), até que ponto as reinfecções efetivamente contribuem para a transmissão progressiva do SARS-CoV-2 e o aumento de casos na segunda onda no Amazonas permanece controverso. No entanto, várias **evidências complementares apoiam que esses eventos foram provavelmente motivados pelo surgimento de uma variante mais transmissível em um contexto de distanciamento social relaxado** [[14]](https://www.nature.com/articles/s41591-021-01378-7).
 
- Quando analisei as **médias móveis** de casos e óbitos, notei que houve uma **diminuição  e estabilização tanto para casos e óbitos, após abril de 2021**. O que, certamente, deve ser **reflexo da vacinação**, que foi iniciada em Janeiro de 2021 e segundo informações da secretaria municipal de saúde de Manaus em maio de 2021, mais de 250 mil pessoas já estavam com o ciclo de imunização completo em Manaus. Até o final de maio Manaus ultrapassou a meta de 90% estabelecida pelo Ministério da Saúde em dez grupos: povos indígenas; trabalhadores de saúde, pessoas de 60 a 64 anos; pessoas de 65 a 69%; grupo de 70 a 74 anos; de 75 a 79 anos; idosos de 80 anos e mais ; e pessoas de 18 a 59 anos com comorbidades.
 
**Relembrando as hipóteses que haviam sido definidas neste projeto:**
  
> Hipótese 1: O número de casos novos deve se estabilizar nos próximos meses, devido ao início da vacinação.
 
> Hipótese 2: O número de óbitos novos deve começar a cair nos próximos meses, devido ao início da vacinação.
 
- Após realizar as **previsões com o Prophet**, tanto para novos **casos** quanto para novos **óbitos**, consegui obter **modelos com curvas bem ajustadas e com dados de teste aderidos à curva**. Ambos **os modelos**,  **mostram uma tendência de queda para os próximos meses.**
 
- Portanto, **as duas hipóteses levantadas no início do projeto foram respondidas: Sim, após alguns meses de vacinação houve queda de casos e óbitos e a tendência é de que continuem diminuindo**.

- Quando testamos **previsões com períodos mais longos**, vemos que o **intervalo de confiança tende a aumentar cada vez mais**. No caso das previsões feitas neste projeto, **a curva de tendência indica que os números de novos casos e novos óbitos poderão se manter baixos nos próximos dois meses**. Porém, quando pensamos em séries temporais o esperado seria encontrar uma sazonalidade constante e não foi isso que vimos nestes dados de Manaus. **Em Manaus, observamos essa segunda onda catastrófica, que poderia ter sido evitada**, mas uma série de fatores [[11]](https://portal.fiocruz.br/sites/portal.fiocruz.br/files/documentos/boletim_covid_2021_extraordinario_junho_parte1.pdf) nos trouxeram essa triste realidade de vários óbitos causados pela COVID-19: 
  - Falha do governo em assumir a liderança e responsabilidade no desenvolvimento de estratégias coerentes destinadas à prevenção da transmissão do vírus; 
  - Descoordenação das políticas e ações entre os níveis nacional e estados/municípios, comprometendo as capacidades de mobilizar recursos essenciais para o enfrentamento da pandemia; 
  - Desvalorização de medidas preventivas e de tratamentos baseados na ciência e estímulo generalizado para a adoção de tratamentos sem comprovação científica;
  - Demora nas decisões e ações necessárias para garantia de estoque de insumos (equipamentos de UTI e proteção, medicamentos e vacinas); 
  - E é claro: a criação de um clima de descrédito e desconfiança na população em temas relacionados ao uso de máscaras e ao conjunto de medidas de distanciamento físico e social, bem como às vacinas, minando os esforços de enfrentamento e respostas.
 
- As análises de componentes, incluindo tendência, sazonalidade e feriados, mostraram que aos **domingos e segundas há uma diminuição da notificação dos casos e óbitos.** Esses dados da Pandemia aos domingos, segundas e feriados, costumam ser menores devido a atrasos de notificação nas secretarias da saúde, que nesses dias, trabalham com menos profissionais, em esquema de plantão. Além disso, podemos perceber que há uma **baixa nos casos e óbitos notificados, quando os dias úteis se tornam feriados.**
 
- O modelo de **sazonalidade multiplicativa**, que é usado com flutuações sazonais que variam dependendo do nível global da série, **se mostrou mais adequado para os modelos previstos neste projeto**. Destaque deve ser dados de novos Óbitos, onde nos valores das métricas do *Scikit-learn*, a média do erro absoluto foi de apenas 8.1, no caso da sazonalidade multiplicativa.
 
- Após realizar o *Cross-Validation* dos modelos de previsão, no geral, vemos que **quanto maior o número de dias do `horizon`, maior é a dispersão dos dados no nosso modelo**. Como esse projeto está usando dados reais da Pandemia de COVID-19, sabemos que em muitos momentos da pandemia os dados sofreram grandes mudanças, com picos de casos e óbitos e isso influencia nessa questão da dispersão dos pontos no modelo. Se fosse uma série temporal estabilizada, contendo dados de um tempo maior, possivelmente, os erros vistos nesses parâmetros poderiam ser bem menores do que estamos vendo aqui. Contudo, **na previsão de Novos Óbitos os resultados obtidos com essas métricas foram melhores no geral**.


<a name="final"></a>
# **Considerações finais**

Obtive os modelos deste projeto após:
- Criar uma lista com todos os feriados nacionais, estaduais (Amazonas) e do município Manaus;
- Remover os *outliers*;
- Então, fiz uma série de testes de como conseguir ajustar os dados e cheguei nos seguintes parâmetros finais:

<p align="center">
  <img src="https://github.com/vqrca/bootcamp_alura_projeto_3/blob/main/Images/modelo_final.png" />
</p>

> Quando ajustei o modelo para Novos óbitos um `changepoint_range=0.92` me trouxe um melhor resultado. 
 
- `n_changepoints`: Este é o número de changepoints colocados automaticamente. O padrão de 25 deve ser suficiente para capturar as mudanças de tendência em uma série temporal típica. Em vez de aumentar ou diminuir o número de pontos de mudança, provavelmente será mais eficaz se concentrar em aumentar ou diminuir a flexibilidade nessas mudanças de tendência, o que é feito com `changepoint_prior_scale`. 
 
- `changepoint_range`: Esta é a proporção em que a tendência pode mudar. O *default* desse parâmetro é 0.8, (80%), o que significa que o modelo não se ajustará a nenhuma mudança de tendência nos últimos 20% da série temporal. Isso é bastante conservador, para evitar *overfitting* nas mudanças de tendência no final da série temporal, onde não há pista suficiente para se encaixar bem. Isso é algo que pode ser identificado visualmente com bastante facilidade: pode-se ver claramente se a previsão está indo mal nos últimos 20%. Porém, acabei ajustando para 0.90 (nos Novos Casos) e para 0.92 (nos Novos óbitos), pois devido ao pico de segunda onda da pandemia, a curva não estava se ajustando bem apenas com o valor *default* de 0.8. 
 
- `changepoint_prior_scale`: Este é provavelmente o parâmetro mais impactante. Ele determina a flexibilidade da tendência e, em particular, o quanto a tendência muda nos pontos de mudança de tendência. O *default* desse parâmetro é de 0.05 e isso funciona para muitas séries temporais, porém ajustei para 0.1.
 
- `seasonality_mode`: As opções são ['additive' ou 'multiplicative']. O *default* é 'aditivo', mas muitas séries temporais terão sazonalidade multiplicativa. Isso é melhor identificado apenas olhando para a série temporal e ver se a magnitude das flutuações sazonais cresce com a magnitude da série temporal. No meu caso, a sazonalidade multiplicativa gerou resultados melhores.
 
- `holidays`: para passar em um dataframe de feriados especificados.
 
- `weekly_seasonality`: 7 dias 
 
 
Após concluir as análises, vemos que em poucas linhas de código é possível fazer previsões e validações, o que faz do Prophet uma ferramenta bastante poderosa e prática.

<a name="ref"></a>
# **Referências**
[[1]](https://www.nature.com/articles/s41579-018-0118-9) Origin and evolution of pathogenic coronaviruses. 
 
[[2]](https://www.thelancet.com/journals/lancet/article/PIIS0140-6736(20)30260-9/fulltext) Nowcasting and forecasting the potential domestic and international spread of the 2019-nCoV outbreak originating in Wuhan, China: a modelling study.
 
[[3]](https://www.ufrgs.br/user/covid-19/) Universidade Federal do Rio Grande do Sul - Projeto: Use o R. 
 
[[4]](https://www.who.int/docs/default-source/coronaviruse/situation-reports/20200304-sitrep-44-covid-19.pdf?sfvrsn=783b4c9d_2) World Health Organization - WHO. Coronavirus disease 2019 (COVID-19): situation report – 44.
 
[[5]](https://www.scielosp.org/article/ress/2020.v29n4/e2020376/) COVID-19 no Brasil: evolução da epidemia até a semana epidemiológica 20 de 2020. 
 
[[6]](https://brasil.elpais.com/ciencia/2020-07-23/evolucao-dos-casos-de-coronavirus-no-brasil.html) Evolução dos casos de coronavírus no Brasil. 
 
[[7]](https://www1.folha.uol.com.br/equilibrioesaude/2021/04/media-movel-de-mortes-passa-de-3000-e-brasil-registra-3673-obitos-em-24-h.shtml#:~:text=M%C3%A9dia%20m%C3%B3vel%20de%20mortes%20por,2021%20%2D%20Equil%C3%ADbrio%20e%20Sa%C3%BAde%20%2D%20Folha) Folha de São Paulo: Média móvel de mortes por Covid passa de 3.000 e Brasil registra 3.673 óbitos em 24h.
 
[[8]](https://covid.saude.gov.br/) Painel Coronavírus (acessado em 22/06/21).
 
[[9]](https://saude.estadao.com.br/noticias/geral,amazonas-apresenta-colapso-no-sistema-de-saude-por-causa-do-coronavirus,70003272136) Estadão: Amazonas apresenta colapso no sistema de saúde por causa do coronavírus. 
 
[[10]](https://www.cnnbrasil.com.br/saude/2021/03/17/covid-19-no-brasil-17-3-2021) CNN: Brasil bate recorde de casos de Covid-19 e média de mortes fica acima de 2.000.
 
[[11]](https://portal.fiocruz.br/sites/portal.fiocruz.br/files/documentos/boletim_covid_2021_extraordinario_junho_parte1.pdf) Boletim extraordinário do Observatório Covid-19 - 25 de junho - parte 1.
 
[[12]](https://www.scielo.br/j/mioc/a/zZcPQFjhhgYrJLVJ77HJC3C/?lang=en) Genomic and phylogenetic characterisation of an imported case of SARS-CoV-2 in Amazonas State, Brazil.
 
[[13]](https://www.fvs.am.gov.br/media/publicacao/21_02_21_BOLETIM_DIÁRIO_DE_CASOS_COVID-19.pdf) Fundação em Vigilância e Saúde do Amazonas. Boletim diários dos casos de COVID-19.
 
[[14]](https://www.nature.com/articles/s41591-021-01378-7) COVID-19 in Amazonas, Brazil, was driven by the persistence of endemic lineages and P.1 emergence.
 
[[15]](https://wwwnc.cdc.gov/eid/article/27/4/21-0138_article) Novel SARS-CoV-2 Variant in Travelers from Brazil to Japan.
[[16]](https://agenciabrasil.ebc.com.br/saude/noticia/2021-01/vacinacao-contra-covid-19-come%C3%A7a-em-todo-o-pais) Agência Brasil: Vacinação contra a covid-19 começa em todo o país
 
[[17]](https://semsa.manaus.am.gov.br/noticia/mais-de-250-mil-pessoas-ja-estao-com-o-ciclo-de-imunizacao-completo-em-manaus/) Imunização SEMSA - Manaus

[[18 ]](https://www.thelancet.com/article/S0140-6736(21)00183-5/fulltext) Resurgence of COVID-19 in Manaus, Brazil, despite high seroprevalence.
	
[[19]](https://science.sciencemag.org/content/372/6544/815) Genomics and epidemiology of the P.1 SARS-CoV-2 lineage in Manaus, Brazil.
  
<a name="doc"></a>
# **Documentação**

[Matplotlib](https://matplotlib.org/)
 
[Numpy](https://numpy.org/)
 
[Pandas](https://pandas.pydata.org/)
 
[Prophet](https://facebook.github.io/prophet/docs/quick_start.html)
 
[Scikit-learn](https://scikit-learn.org/)
 
[Seaborn](https://seaborn.pydata.org/)
 
[StatsModels](https://www.statsmodels.org/stable/index.html)
 
<a name="agra"></a>
# **Agradecimentos**

Gostaria de deixar meu agradecimento aos instrutores do módulo 3: Allan Spadini e Karoline Penteado. 
	
Ao pessoal do Scuba team e do Discord, que sempre trazem excelentes discussões e ideias.

Também gostaria de agradecer aos amigos Carolina Dias e Junior Torres, que sempre dão apoio, incentivo e fazem os dias serem mais leves e descontraídos. 
	
<p align="center"> <img src=https://media.giphy.com/media/ZfK4cXKJTTay1Ava29/giphy.gif </p> 
		
<a name="contact"></a>
# **Onde encontrar meu trabalho?**
  
[Medium](https://valquiria-c-alencar.medium.com/)
	
[LinkedIn](https://www.linkedin.com/in/valqu%C3%ADria-alencar-786a8911b/)
 
[ResearchGate](https://www.researchgate.net/profile/Valquiria-Alencar)
 
[Currículo lattes](http://lattes.cnpq.br/7742338443535710)

