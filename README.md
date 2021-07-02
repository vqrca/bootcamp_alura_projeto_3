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
A [base de dados](https://brasil.io/dataset/covid19/caso_full/) utilizada neste projeto foi extraída do *Brasil.io* e representa os casos de SARS-CoV-2 no Brasil todo. Essa base contém o número de casos novos de covid, número de óbitos e outras informações.

O Notebook com a análise completa e códigos pode ser encontrado [aqui](). 

Uma publicação sumarizando as análises, sem conter os códigos e etapas de tratamento dos dados, pode ser encontrada na minha página do [Medium]().

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


Todas essas ações foram cruciais até que vacinas fossem desenvolvidas, testadas em pessoas e finalmente, aplicadas na população.
	
<p align="center"><img src='https://media.giphy.com/media/Qu1fT51CG14ksIkASL/giphy.gif'</p>
	
## **Cenário da Pandemia no Brasil**

- No final de fevereiro de 2020, o primeiro caso da doença foi confirmado no Brasil [[5]](https://www.scielosp.org/article/ress/2020.v29n4/e2020376/#). 
  
- Em 20 de março de 2020, o país decretou transmissão comunitária em todo o território nacional [[5]](https://www.scielosp.org/article/ress/2020.v29n4/e2020376/#).
  
- Em maio de 2020, a Covid-19 tornou-se a maior causa de morte no Brasil [[5]](https://www.scielosp.org/article/ress/2020.v29n4/e2020376/#). 
  
- Até a semana epidemiológica 20 a região Norte apresentou as maiores taxas de incidência e mortalidade [[5]](https://www.scielosp.org/article/ress/2020.v29n4/e2020376/#) 
  
- Até a semana epidemiológica 20 o Amazonas apresentou a maior taxa de incidência. 
[[5]](https://www.scielosp.org/article/ress/2020.v29n4/e2020376/#). 
  
- Em 8 de agosto, menos de seis meses depois, o Brasil chegou à triste marca de 100.000 mortes causadas pelo novo coronavírus [[6]](https://brasil.elpais.com/ciencia/2020-07-23/evolucao-dos-casos-de-coronavirus-no-brasil.html).
  
- Em 7 de janeiro de 2021, os óbitos chegaram a marca de 200.000 [[6]](https://brasil.elpais.com/ciencia/2020-07-23/evolucao-dos-casos-de-coronavirus-no-brasil.html).
No início de março de 2021, o país registrou sua semana mais letal desde o início da pandemia, com a média móvel de mortes em torno de 1.500 por dia [[6]](https://brasil.elpais.com/ciencia/2020-07-23/evolucao-dos-casos-de-coronavirus-no-brasil.html).
  
- Em abril de 2021 a média móvel de mortes por Covid passou de 3.000 e Brasil registrou 3.673 óbitos em 24 horas. A média móvel média bateu recorde pelo 7º dia seguido[[7]](https://www1.folha.uol.com.br/equilibrioesaude/2021/04/media-movel-de-mortes-passa-de-3000-e-brasil-registra-3673-obitos-em-24-h.shtml#:~:text=M%C3%A9dia%20m%C3%B3vel%20de%20mortes%20por,2021%20%2D%20Equil%C3%ADbrio%20e%20Sa%C3%BAde%20%2D%20Folha). 
  
- Recentemente, o Brasil ultrapassou meio milhão de óbitos por SARS-CoV-2 e o número de casos acumulados reportados é de 17.966.831[[8]](https://covid.saude.gov.br/). 


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
Neste projeto os seguintes datasets foram obtidos:
 
- Todos os Estados, com os seguintes filtros:
   
- Estado Amazonas, com os seguintes filtros:

- Manaus, com os seguintes filtros:

Os arquivos *.csv* desse datasets podem ser encontrados na pasta [data](https://github.com/vqrca/bootcamp_alura_projeto_3/tree/main/Data) desse repositório. 
  
## **Bibliotecas utilizadas e suas respectivas funções**

- Pandas versão 1.1.5: Manipulação dos datasets - 
  
- Numpy versão 1.19.5: Cálculos numéricos
  
- Matplotlib versão 3.2.2: Plotar os gráficos
  
- Seaborn versão 0.11.1: Plotar os gráficos
  
- StatsModel: Análise de correlações
  
- Prophet: Previsão de séries temporais
  
- Sckit-learn: Métricas para avaliar os modelos gerados 
  
> O notebook *.ipynb* foi construído no google colab usando Python 3.7.10. 

<a name="hip"></a>
# **Hipóteses**

O objetivo principal deste módulo é a previsão de dados de séries temporais. Essas previsões foram realizadas para o número de casos e óbitos do Amazonas.
De acordo com esse objetivo as seguintes hipóteses foram definidas:


> Hipótese 1: O número de casos novos deve se estabilizar nos próximos meses, devido ao início da vacinação.
  
  
> Hipótese 2: O número de óbitos novos deve começar a cair nos próximos meses, devido ao início da vacinação.
  
<a name="conclusoes"></a>
# **Conclusões**

Hipótese 1: O número de casos novos deve se estabilizar nos próximos meses, devido ao início da vacinação.
>
  
Hipótese 2: O número de óbitos novos deve começar a cair nos próximos meses, devido ao início da vacinação.
>

Na região nordeste houve registros de diversos empecilhos de adesão, por parte da população, para o isolamento social recomendado pelas autoridades de saúde(https://www.uerj.br/noticia/11078/)

Outro motivo que pode explicar esse resultado é que a rede hospitalar da região Norte é menor quando comparada com as das outras regiões do país, possuindo o menor número de leitos, que em longo prazo é incapaz de responder à demanda, tanto no setor público quanto no privado(http://tabnet.datasus.gov.br/cgi/tabcgi.exe?cnes/cnv/leiintbr.def)


<a name="final"></a>
# **Considerações finais**
O mundo já havia passado por outras crises sanitárias, mas a pandemia causada pelo SARS-CoV-2 tem uma particularidade: devido aos avanços tecnológicos, hoje os indivíduos estão conectados de maneira global e as informações circulam de forma massiva por meio das redes sociais. Nós vimos, claramente, que até mesmo cientistas perderam credibilidade e vivenciamos a era das fake news.

<p align="center"><img src='https://media.giphy.com/media/LMhbwQ27DaXCTbX1zo/giphy.gif'</p>



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
	
<p align="center"><img src=https://media.giphy.com/media/QSJflihoTLhXIzVjYU/giphy.gif </p>
		
<a name="contact"></a>
# **Onde encontrar meu trabalho?**
 
[LinkedIn](https://www.linkedin.com/in/valqu%C3%ADria-alencar-786a8911b/)
 
[ResearchGate](https://www.researchgate.net/profile/Valquiria-Alencar)
 
[Currículo lattes](http://lattes.cnpq.br/7742338443535710)

