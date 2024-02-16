
# Como acessar o serviço do Azure Machine Learning, configurar modelos e conjuntos de dados, testar e analisar resultados


A proposta deste repositório é trazer um tutorial passo a passo para exemplificar a utilização do Azure Machine Learning, realizando a configuração de um modelo, conjunto de dados e o teste e análise de resultados. 

A iniciativa da criação deste repositório foi para registrar a resolução do exercício 'Introdução ao Aprendizado de Máquina' que é parte do curso [Microsoft Azure AI Fundamentals](https://web.dio.me/track/microsoft-azure-ai-fundamentals) fornecido pela Digital Innovation One - [DIO](https://www.dio.me/), este em preparação para a certificação AI-900: Microsoft Azure AI Fundamentals.

Espero poder ajudar todos aqueles que por ventura vierem a este repositório.


## Apresentação do Problema

O problema que iremos resolver é o mesmo apresentando pela Microsoft Learn com o título 'Explore Automated Machine Learning in Azure Machine Learning', este problema pode ser encontrado [aqui](https://microsoftlearning.github.io/mslearn-ai-fundamentals/Instructions/Labs/01-machine-learning.html).

O problema proposto é o seguinte:

> "Neste exercício, você usará o recurso de Automated Machine Learning no Azure Machine Learning para treinar e avaliar um modelo de machine learning. Em seguida, você implantará e testará o modelo treinado."

## Pré-requisitos para resolução do problema

* Ter uma conta do Microsoft Azure. (Caso você não tenha um conta será necessário criar, para isto siga os passos que serão apresentados abaixo)

* Ter muita vontade e disposição para aprender.


#### Passo a Passo para criar a conta no Microsoft Azure

* Acesse o site da [Microsoft Azure](https://azure.microsoft.com/pt-br/free/search/?ef_id=_k_CjwKCAiA_aGuBhACEiwAly57MQIxpbuFTl1YFmHB1o36Rq5fAlKA8JO9CdOLPuyq_oV_3JBza8E_-hoC4OAQAvD_BwE_k_&OCID=AIDcmmzmnb0182_SEM__k_CjwKCAiA_aGuBhACEiwAly57MQIxpbuFTl1YFmHB1o36Rq5fAlKA8JO9CdOLPuyq_oV_3JBza8E_-hoC4OAQAvD_BwE_k_&gad_source=1&gclid=CjwKCAiA_aGuBhACEiwAly57MQIxpbuFTl1YFmHB1o36Rq5fAlKA8JO9CdOLPuyq_oV_3JBza8E_-hoC4OAQAvD_BwE)
* Clique em Experimente gratuitamente ou no botão Início gratuito.
* Será necessário colocar os dados de sua conta da Microsoft, que em geral é de um e-mail da hotmail ou outlook.
* Siga os passos conforme solicitado.

**OBS**: Será necessário cadastrar um cartão de crédito para aderir ao plano gratuito, inicialmente você terá $200 dólares de crédito ou 30 dias para testar os serviços, prevalecendo o que acabar primeiro.

## Passo a Passo para resolver o problema

Agora que você já tem uma conta da Microsoft Azure, vamos começar:

1. Acesse o [Portal da Azure](https://portal.azure.com/) para começar a resolver o problema.

2. Na aba Azure Services procure por 'Create a Resource'.

![Create a Resource](https://i.ibb.co/XXZsckw/Create-a-Resource.png)

3. Em seguida pesquise por Azure Machine Learning. 

![Azure Machine Learning](https://i.ibb.co/JBQbzjK/Azure-Machine-Learning.png)

4. Após acessar o serviço do Azure Machine Learning, clique no botão 'create'.

![Create Azure Machine Learning](https://i.ibb.co/wL79CgX/Create-Azure-Machine-Learning.png)

5. Neste página você irá criar um Machine Learning Workspace. Com os seguintes dados:
 

    Subscription: Aqui é a sua inscrição do Microsoft Azure, se você estiver com uma conta gratuita, provavelmente apareça ela como padrão.

    Resource group: Criar ou selecionar um Grupo de Recursos. (Como provavelmente você não terá um Grupo de Recursos para selecionar, deverá criar um clicando no botão create new, então deverá colocar um nome para o mesmo e clicar em ok. Experimente colocar **LABTesteNomeRG**, onde LAB é Laboratorio e RG é Resource Group)

    Name: Entrar com um nome único para seu Workspace. Neste caso aqui sugiro colocar **laboratorioai900**, mas pode ser qualquer nome a sua escolha.

    Region: Sugiro você colocar a região East US. Que é a mais próximo com custo mais baixo.

    Storage account: Este campo terá preenchimento automático assim que você preencher o nome do workspace, sugiro não mudar.

    Key vault: Este campo terá preenchimento automático assim que você preencher o nome do workspace, sugiro não mudar.

    Application insights: Este campo terá preenchimento automático assim que você preencher o nome do workspace, sugiro não mudar.

    Container registry: Deixe como None.

5. Após o preenchimento dos dados iremos clicar no botão azul 'Review + Create'. 

![Review + Create](https://i.ibb.co/gF1VCF2/Review-create.png)

6. Após o validation passed, clique no botão Create. Após clicar no botão Create, espere o Deployment finalizar. Aparecerá a mensagem 'Your deployment is complete'.

![Validation Passed e Create](https://i.ibb.co/WtxHjxK/validation-passed-e-create.png
)

7. Após a o deploy está completo, iremos clicar no botão Go to resource. 

![Go to resource](https://i.ibb.co/kc6KG8f/Go-to-resource.png)

8. Então clicaremos no botão Launch Studio.

![Launch Studio](https://i.ibb.co/BsfTRFv/Launch-Studio.png)

9. Na página que abrir você deverá localizar no meu lateral esquerdo a opção 'ML Automatizado', caso o menu não esteja expadindo aparecendo os nomes, clique no ícone do menu para expandir.

![ML Automatizado](https://i.ibb.co/gwwNdN9/ML-automatizado.png)

10. Clique em 'Novo trabalho de ML automatizado' e em seguida insira estas informações abaixo:


Configurações Básicas:

    Nome do Trabalho: mslearn-bike-automl
    Novo nome do experimento: mslearn-bike-rental
    Descrição: Aprendizado de máquina automatizado para previsão de aluguel de bicicletas
    Marcas: Não adicionar nenhum.

![ML Automatizado](https://i.ibb.co/d4vrj5W/Configura-es-b-sicas.png)


11. Clique em avançar, selecione o tipo de tarefa como Regressão, em selecionar dados clique em criar.

Tipo de Tarefa e Dados:

    Selecionar o tipo de Tarefa: Regressão

![Criar selecao de dados](https://i.ibb.co/tXVsBbp/Criar-selecao-de-dados.png)


12. Em definir o nome e o tipo do ativo de dados coloque as seguintes informações:

Definir o nome e o tipo do ativo de dados:

    Tipo do dado:
    Nome: bike-rentals
    Descrição: Historic bike rental data
    Tipo: Tabular

![Tipo de dados](https://i.ibb.co/fQY1Tnc/tipo-de-dados.png)

13. Em fonte de dados escolha 'De arquivos da Web' e clique em avançar.

![De arquivos da Web](https://i.ibb.co/bRPyjjj/De-arquivos-da-web.png)

14. Insira as seguintes informações e clique em avançar: 

Fonte de Dados:

    URL da Web:
    Web URL: https://aka.ms/bike-rentals
    Ignorar validação de dados: Não selecionar
    

![URL da web](https://i.ibb.co/0BtNdvJ/URL-da-web.png)
    

15. Insira as seguintes informações e clique em avançar.

Fonte de Dados:

    Configurações:
    Formato do arquivo: Delimitado
    Delimitador: Comma
    Codifição: UTF-8
    Cabeçalhos de coluna: Somente o primeiro arquivo tem cabeçalho
    Ignorar linhas: Nenhuma
    Conjunto de dados de várias linhas: Não selecionar


![Configurações arquivo cvs](https://i.ibb.co/NrTJXMF/Configura-es-arquivo-csv.png)


16. Na aba de esquema, deixe tudo como estiver e clique em avançar.

![Esquema](https://i.ibb.co/mR33dn3/Esquema.png)

17. Em examinar clique em criar

![Configurações arquivo cvs](https://i.ibb.co/qsLH40k/Examinar.png)

18. Selecione os dados criados e clique em avançar

![Selecione dados criados e avançar](https://i.ibb.co/fvG39CM/Selecione-dados-criados-e-avan-ar.png)

19. Em configurações de tarefas, adicione as seguintes informações:

Configurações de tarefas:

    Tipo da Tarefa: Regressão
    Dados: bike-rentals
    Coluna destino: Rentals (integer)

![Configurações de Tarefa](https://i.ibb.co/dj4d31N/Configura-es-de-tarefa.png)


20. Clique em exibir definições de configurações adicionais e adicione as seguintes informações em clique em salvar:

Definições de configurações adicionais:

    Métrica primária: NormalizedRootMeanSquaredError
    
    Explicar melhor o modelo: Não selecionar
    Habilitar empilhamento ensemble: Não selecionar
    Usar todos os modelos suportados: Não selecionar
    
    Modelos permitidos: Selecionar RandomForest e LightGBM 

![Configuração adicional](https://i.ibb.co/x276Z82/Configura-o-adicional.png)

21. Clique em limites para expandir a seção e adicione as seguintes informações:

Limites:    
    
    Máximo de avaliações: 3
    Máximo de avaliações simultâneas: 3
    Máximo de nós: 3
    Limite de pontuação da métrica: 0.085
    Tempo limite do experimento (minutos): 15
    Tempo limite de iteração (minutos): 15
    Habilitar encerramento antecipado: Selecionado

![Limites](https://i.ibb.co/G91Hm0X/Limites.png)




22. Em Validar e testar selecione as seguintes opções e clique em avançar:

Validar e Testar

    Tipo de validação: Divisão de validação de treinamento
    Validação de percentual de dados: 10
    Dados de teste: Nenhum

![Validar e Testar](https://i.ibb.co/HgZTWVV/Validar-e-Testar.png)

23. Em computação adicione as seguintes informações e clique em avançar 

Computação:

    Selecione o tipo de computação: Sem servidor
    Tipo de máquina virtual: CPU
    Tipo de máquina virtual: Dedicado
    Tamanho da máquina virtual: Standard_DS3_V2*
    Número de Instâncias: 1

![Computação](https://i.ibb.co/xsLvKyc/Computacao.png)

24. Clique em enviar trabalho de treinamento

![Enviar trabalho de treinamento](https://i.ibb.co/FDQth38/Enviar-trabalho-de-treinamento.png)

25. Irá aparecer uma tela com status como Não iniciado, espere o status alterar para em execução.


Status não iniciado
![Status Não Iniciado](https://i.ibb.co/H2tm9k9/Status-N-o-Iniciado.png)

Status em execução (Em geral essa execução dura em torno de 16 minutos)
![Status em execução](https://i.ibb.co/bdGwLnz/Status-em-execu-o.png)

26. Após finalizado, no menu lateral esquerdo iremos clicar em Modelos.

![Conclusão e Modelos](https://i.ibb.co/ZJJ18hZ/Conclus-o-e-Modelos.png)


27. Clicaremos em +Registro e selecionaremos a opção 'de uma saída de trabalho'. 

![Registro de uma saida de trabalho](https://i.ibb.co/tzQ3JbM/Registro-de-um-sa-da-de-trabalho.png)


28. Selecionaremos o trabalho que criamos que é o 'mslearn-bike-automl' e clicaremos em avançar.

![Selecionar o trabalho](https://i.ibb.co/7Jg8dfB/Selecionar-o-trabalho.png)

29. Na parte de selecionar saida, já irá aparecer preenchido como padrão, deixe como estiver.

Tipo de Modelo: MLflow
Saída de trabalho: best_model...

![Selecionar saída](https://i.ibb.co/Y2jvgYW/selecionar-saida.png)


30. Em configuração do modelo, coloque as informações abaixo e clique em avançar.

Nome: mslearnbikeauto4
Descrição: Deixe em branco.
Versão: 1
Marcas: Não precisa adicionar

![Configurações do modelo](https://i.ibb.co/P4TyW24/Configura-o-do-modelo.png)

30. Em examinar, clique em registro.

![Examinar e Registro](https://i.ibb.co/dDMcyKV/Examinar-registro.png)

31. No menu lateral esquerdo, agora clicaremos em Pontos Extremidade.

![Ponto de extremidade](https://i.ibb.co/vkYcTr0/Pontos-de-Extremidade.png)

32. Em pontos de Extremidade clicaremos e Criar e então selecionaremos 'mslearnbikeauto4', e clicaremos no botão selecionar.

![Criar e Selecionar](https://i.ibb.co/4S536Nz/Criar-e-Selecionar.png)

33. Na aba de implantar, altere o nome do ponto de extremidade para 'laboratoriocertificaoai900-extr' e clique em implantar e espere a conclusão do processo.

![Criar em implantar](https://i.ibb.co/V2TFdvX/Clicar-em-implantar.png)

34. Após a conclusão da criação do ponto de extremidade, você deverá clica no menu lateral em ponto de extremidade, selecionar então o ponto de extremidade criado e clicar em testar.

![Testar](https://i.ibb.co/yWpQjgS/testar.png)

35. Na aba 'inserir dados para teste de ponto de extremidade', insira os seguintes dados em JSON e clique em testar.

JSON 
```
 {
   "input_data": { 
     "data": [
       {
         "day": 1,
         "mnth": 1,   
         "year": 2022,
         "season": 2,
         "holiday": 0,
         "weekday": 1,
         "workingday": 1,
         "weathersit": 2, 
         "temp": 0.3, 
         "atemp": 0.3,
         "hum": 0.3,
         "windspeed": 0.3 
       }
     ]    
   },   
   "GlobalParameters": 1.0
 }

```

36. O Resultado será apresentado no quadro resultado do teste. Copie o resultado e cole em um bloco de notas com nome ResultadoPredict-Rentals.json

![Resultado](https://i.ibb.co/XbLhWpP/Resultado.png)

Parabéns! Você fez todo o processo!



## Meus Contatos

[![LinkedIn](https://img.shields.io/badge/LinkedIn-000?style=for-the-badge&logo=linkedin&logoColor=0E76A8)](https://www.linkedin.com/in/tiagolisboanovais/)

[![Instagram](https://img.shields.io/badge/instagram-000?style=for-the-badge&logo=instagram&logoColor=0E76A8)](https://www.instagram.com/tiagolisboa.ti/)

[![E-mail](https://img.shields.io/badge/-Email-000?style=for-the-badge&logo=microsoft-outlook&logoColor=007BFF)](mailto:tiagolisboanovais)

[![Github](https://img.shields.io/badge/github-000?style=for-the-badge&logo=github&logoColor=0E76A8)](https://github.com/tiagolisboanovais)


