# Estação de Tratamento de Efluentes
Esta aplicação, é uma ilustração de uma solução de monitoramento para os processos no tratamento de efluentes. Este é um aplicativo, multilocatário, que pode oferecer a seus clientes soluções para monitoramento remoto de seus equipamentos, além de aplicação de algoritmos matemáticos para encontrar melhor sintonia para a sua malha de controle, e uso de algoritmos
de Inteligencia Artificial para melhor entendimento e previsão, do comportamento de algumas variáveis.

## Componentes Chave
Aqui estará sendo apresentado um README da aplicação desenvolvida. Alguns itens são destacados a baixo:

* Aplicativo desenvolvido para monitoramento dos dados de processos de ETEs em tempo real, além uso de algoritmos matemáticos e de machine learning para auxiliar e melhorar a performance nos processos de neutralização do pH dos efluentes.
* Visão geral ao vivo e histórica dos dados, e análises destes dados para otimização dos processos em ETEs.
* Painéis de fácil visualização para o monitoramento e acompanhamento do comportamento das principais variáveis do sistema.

## Setup
* Verifique se está habilitado o Workflow [Insert Value](/applications/609557b5642331000694bd9b/workflows/60a6b5296bd5010006b56748/develop).
* Verifique se está habilitado o Workflow [Anomalia](/applications/609557b5642331000694bd9b/workflows/60c39845dce6c40006fb8f9e/develop).
* Verifique se está habilitado o Workflow [Predicao](/applications/609557b5642331000694bd9b/workflows/60c3a4608e871c000620e967/develop).
* Verifique se está habilitado o Workflow [Relevance](/applications/609557b5642331000694bd9b/workflows/60c36459d77a3c00079a3264/develop).
* Verifique se está habilitado o Workflow [Sintonia](/applications/609557b5642331000694bd9b/workflows/60c3644ad77a3c00079a3262/develop).

Realizar o download dos arquivos .xlsx para obter uma tabela com dados de demonstração, mas que pode ser utilizada como template para inserção de dados do próprio usuário, conservando o padrão de nome para as colunas, para o mesmo utilizar essas tabelas para realizar as análises nesta aplicação.

Para inserir estas tabelas nesta aplicação elas devem ser salvas antes em um formato .csv, salvando apenas os dados desconsiderando salvar as fórmulas do arquivo, para que o wegnology reconheça esta tabela e não ocorra problemas.
Quando for inserir as tabelas o usuário deve se atentar ao tipo das colunas que o wegnology reconhece, a coluna de Timestamp deve ser do tipo string, enquanto as demais colunas do arquivo devem sempre ser do formato numérico, que no caso do wegnology deve estar selecionada a opção number.

O usuário em caso de decidir a inserir os seus próprios dados na tabela deve-se atentar ao fato desta plataforma não conseguir armazenar no device dados mais antigos do que 30 dias atrás, portanto em caso de decisão por inserir os seus próprios dados nas tabelas para salvar o csv e inseri-las na aplicação deve se ter um atenção com esta pequena limitação.

Após realizada essas etapas, deve-se acessar a parte de configurações [API Tokens](/applications/609557b5642331000694bd9b/application-tokens), e clicar em adicionar application token, ao ser gerado código de api token, deve-se salvar o arquivo ou o código gerado, pois o código será utilizado para realizar as análises. 
Quando já estiver feito isto, o código de API Token gerado, deve ser colado sobrescrevendo o valor já salvo anteriormente no bloco com nome de order, presente em cada workflow de análise.

## Obter licença
Para se gerar as análises, deve-se responder um formulário para cadastro do cliente, cuja finalidade seja o usuário obter por e-mail um USERNAME e PASSWORD, além de um Id de Projeto que serão utilizados nas configurações de blocos para se gerar as análises.

Ao serem obtidos USERNAME, PASSWORD, ID de projeto, deve-se salva-los e gerar um API Token na aplicação do WEGnology, apos isso deve ser acessada a aba de Globals, para que de acordo com os campos específicos seja inseridos os valores de Password, Username, Id do Projeto e o token API gerado. Os dados de username, password e id de projetos são recebido pelo cliente no seu e-mail após responder o formulário.

Para se obter essa licença e responder o formulário, acesse [Aqui](www.birmind.com.br/api-license).

## workflows
Será explicado agora brevemente o funcionamento de cada Workflow e os processos a se realizar no workflow para gerar uma análise.

As análises geradas estão configuradas para uma análise de acordo com os dados de demonstração, para dados próprios algumas configurações deveram ser alteradas para se obter melhores análises e consequemente melhores resultados.

### Insert Value
Quando ativado, o workflow [Insert Value](/applications/609557b5642331000694bd9b/workflows/60a6b5296bd5010006b56748/develop), irá habilitar os botões para deletar os dados antigos armazenados, e o botão para inserir os novos dados, o botão Atualizar Dados no dashboard é um único botão que realiza ambas as ações. Estes dados são puxados das tabelas de dados que
 serão importadas pelo usuário para o [Data Tables](/applications/609557b5642331000694bd9b/data-tables) desta aplicação, e são inseridos nas variáveis dos devices salvos, de acordo como foi programado nos blocos do worfklow.
Para acessar as Data Tables e verificar as já salvas basta acessar [Data Tables](/applications/609557b5642331000694bd9b/data-tables), e todas as tabelas salvas na aplicação serão mostradas.

Para obter essas tabelas, o usuário deve fazer o download dos arquivos .xlsx e assim utiliza-las com os dados de demonstração, ou para utilizar esta tabela como um template padrão e a partir das colunas ja estabelecidas, adicionar o seu próprio dado para realizar as análises. Para que assim o usuário consiga estar sempre realizando observações com dados de timestamp atuais, e realizar as ações necessárias para se obter uma demonstração do funcionamento desta aplicação.

Após o download destas tabelas e já possuindo os dados corretos armazenados, deve-se salvar estas tabelas no formato .csv, e assim importar estas tabelas em .csv para a aplicação. Sendo realizada esta etapa, o usuário deve acessar este workflow, e ir em cada bloco de [Storage: Set Value](https://docs.app.wnology.io/workflows/data/store-value/) e ao selecionar o bloco para a Key value, no item de Value você deverá substituir o valor já salvo pelo valor do número de linhas da tabela que será utilizada para aquela análise, em caso de utilizar as tabelas de demonstração para as análises esta etapa pode ser desconsiderada. 
Posteriormente a esta etapa, deve-se entrar no bloco de loop de cada workflow de análise (mostrado nos blocos de nota qual workflow corresponde a determinada análise) e dentro deste bloco, no bloco [Table: Get Rows](https://docs.app.wnology.io/workflows/data/table-get-rows/) o usuário deve escolher a tabela
que corresponde aos dados daquela análise a ser realizada.

### Anomalia
Quando ativado, o workflow [Anomalia](/applications/609557b5642331000694bd9b/workflows/60c39845dce6c40006fb8f9e/develop), irá permitir que sejam realizadas as análises de possíveis anomalias nos dados de consumo das ETEs salvos no device [DeviceETEConsumo](/applications/609557b5642331000694bd9b/devices/60be5a78dce6c40006fb7961/properties).

As linhas deste workflow podem ser acionadas tanto no proprio workflow pelo virtual button no próprio workflow, neste worfklow ocorrem 2 ações ou através de requisições HTPP de GET em URLs específicos, a primeira é a linha para se criar os orders de analise com os inputs selecionados e as configurações de analise, e dar dispatch nesse order. Já a outra linha do workflow, consiste nas requisições para a coleta
dos resultados obtidos das análises enviadas.

### Predição
Quando ativado, o workflow [Predicao](/applications/609557b5642331000694bd9b/workflows/60c3a4608e871c000620e967/develop), irá permitir que seja realizada a análise para prever o comportamento da variável de processo analisada de ETEs, que está salvo no device [DeviceETEPredict](/applications/609557b5642331000694bd9b/devices/60be5981b072ff0007135fc7/properties).

As linhas deste workflow podem ser acionadas tanto no proprio workflow pelo virtual button no próprio workflow ou através de requisições HTPP de GET em URLs específicos, neste worfklow ocorrem 2 ações, a primeira é a linha para se criar os orders de analise com os inputs selecionados e as configurações de analise, e dar dispatch nesse order. Já a outra linha do workflow, consiste nas requisições para a coleta
dos resultados obtidos das análises enviadas.

### Relevance
Quando ativado, o workflow [Relevance](/applications/609557b5642331000694bd9b/workflows/60c36459d77a3c00079a3264/develop), irá permitir que seja realizada a análise para observar a influência que determinadas variáveis possuem em relação a saída de análise desejada, e assim determinar quais variáveis possuem maior influência no processo. Os dados enviados para análise foram salvos no [DeviceETE Relevance](/applications/609557b5642331000694bd9b/devices/60be59cedce6c40006fb7959/properties).

As linhas deste workflow podem ser acionadas tanto no proprio workflow pelo virtual button no próprio workflow ou através de requisições HTPP de GET em URLs específicos, neste worfklow ocorrem 2 ações, a primeira é a linha para se criar os orders de analise com os inputs selecionados e as configurações de analise, e dar dispatch nesse order. Já a outra linha do workflow, consiste nas requisições para a coleta
dos resultados obtidos das análises enviadas.

### Sintonia
Quando ativado, o workflow [Sintonia](/applications/609557b5642331000694bd9b/workflows/60c3644ad77a3c00079a3262/develop), irá permitir que seja realizada a análise para se obter os melhores parâmetros de sintonia da malha de controle do processo, para que se minimize as perdas, aumentando assim o ganho. Também são obtidos 
como resposta desse workflow os indices de saúde da malha, e o novo consumo da variável manipulada. Os dados enviados para análise foram salvos no [DeviceETESintonia](/applications/609557b5642331000694bd9b/devices/6099706bd24a820006c96eff/properties).

As linhas deste workflow podem ser acionadas tanto no proprio workflow pelo virtual button no próprio workflow ou através de requisições HTPP de GET em URLs específicos, neste worfklow ocorrem 2 ações, a primeira é a linha para se criar os orders de analise com os inputs selecionados e as configurações de analise, e dar dispatch nesse order. Já a outra linha do workflow, consiste nas requisições para a coleta
dos resultados obtidos das análises enviadas.

## Dashboard
Este modelo possui um painél, onde são exibidos dados em tempo real e historico, além de mostrar na tela em alguns blocos, análises dos dados, realizada pelos algoritmos da BirminD na API da empresa, para auxilixar neste monitoramento, reduzir perdas e aumentar ganhos, entender mais sobre o processo e mensurar a influência de cada variável no processo, além de permitir prever possíveis falhas e observar algumas anomalias.

### Otimização Controle de pH
O dashboard [Otimização Controle de pH](/dashboards/60996bc7d0d6a90007fd7a47), neste dashboard é apresentado blocos para monitoramento das variáveis mais importantes para o processo de neutralização que ocorre nas ETEs.
Também podemos observar nesta tela, alguns blocos com dados colhidos após análise realizada na API da BirminD, e enviado para os blocos presentes nesta tela para facilitar a visualização destes dados.

As análises realizadas com os dados foram análise de sintonia, fornecendo os melhores parâmetros de Kp, Ki, Kd para a malha de controle, o novo consumo e a economia que a malha terá sintonizada com esses parâmetros, os indicadores de saúde dessa malha, e a precisão deste modelo fornecido.Já da parte de Machine Learning, ocorre as análises de Predição da Variável de Processo, para observar o comportamento do pH para prever possíveis comportamentos indesejáveis, há a análise de anomalia do consumo para observar possíveis comportamentos fora do esperado e observar quando ocorreu este comportamento,
e é apresentado em um dos blocos, um gráfico fornecendo a porcentagem que cada variável de entrada possui na variável de saída escolhida.

Neste dashboard, para se gerar as análises é preciso apagar os dados inseridos nos devices, e inseri-los novamente através do botão Atualizar Dados, localizado na parte superior do lado direito da tela, para se gerar os orders das análises é necessário
apertar os botões de recalcular presentes em cada bloco de cada análise, após selecionar para ser calculada cada uma das análises, o botão passará para o estado de recalculando e será exibida uma mensagem com o tempo necessário a se aguardar até o resultado das análises enviadas estarem prontos, é preciso aguardar alguns poucos minitos enquanto as análises estão sendo calculadas, após passar o tempo informado, deve-se apertar o botão de aplicar presente em algum dos blocos de análise, que a página irá atualizar automaticamente e mostrará os resultados obtidos nas telas.
Em caso de alguma análise que nao seja mostrada ou que apresente resultados estranhos, realizar as etapas novamente para obter uma nova análise.

## Experience
Este template inlcui uma experience page, que para acessá-la primeiro deve ser inserido um usuário salvo na aplicação que seja válido na página de [Login](https://templateete.wnology.io/login), após iniciar a sessão você será redirecionado para a página com a mesma tela do Dashboard e contendo as mesmas informações.
A navegação e o funcionamento para gerar análises e puxar os seus resultados é o mesmo realizado no dashboard. Logo na experience page [ETE](https://templateete.wnology.io/), a pagina inicial a qual o usuário é redirecionado após realizar o login. 

Nesta página é possível monitorar as variáveis mais importantes para o processo de neutralização que ocorre nas ETEs.
Também podemos observar em alguns blocos, os resultados das análises realizadas na API da BirminD, e enviados para a tela facilitando a visualização e entendimento destes dados.

As análises realizadas com os dados foram análise de sintonia, fornecendo os melhores parâmetros de Kp, Ki, Kd para a malha de controle, o novo consumo e a economia que a malha terá sintonizada com esses parâmetros, os indicadores de saúde dessa malha, e a precisão deste modelo fornecido.Já da parte de Machine Learning, ocorre as análises de Predição da Variável de Processo, para observar o comportamento do pH para prever possíveis comportamentos indesejáveis, há a análise de anomalia do consumo para observar possíveis comportamentos fora do esperado e observar quando ocorreu este comportamento,
e é apresentado em um dos blocos, um gráfico fornecendo a porcentagem que cada variável de entrada possui na variável de saída escolhida.

No experience page, o funcionamento para se gerar as análises é o mesmo do dashboard, deve-se acionar o botão e apagar os dados inseridos nos devices, e inseri-los novamente selecionando o botão de inserir os dados, os botões estão localizados na parte superior do lado direito da tela, para gerar os orders das análises é necessário
selecionar os botões de recalcular presentes em cada bloco de cada análise, é preciso aguardar alguns poucos minitos enquanto as análises estão sendo calculadas, após estes alguns minutos é deve-se apertar o botão de aplicar para que a página atualize automaticamente e passe a mostrar os novos resultados obtidos.

Para facilitar a visualização das etapas para se gerar as análises e obter as respostas, será mostrada a ordem na lista abaixo:

1. **Fazer o download dos arquivos de tabelas, escolher quais dados usar e salvar no formato .csv**
2. **Importar as tabelas em csv para o Data Tables para poder puxar os dados e salvá-los nos devices**
3. **Acessar workflow Insert Values e em cada workflow de análise colocar os valores corretos no Value do bloco Storage: Set Value de acordo com a tabela que será utilizada para aquela análise**
4. **Acessar workflow Insert Values e em cada workflow de análise selecionar a tabela correta a qual os dados para análise devem ser obtidos no bloco Table: Get Rows**
5. **Apertar o botão de Save & Deploy**
6. **Gerar um API Token**
7. **Acessar a area de Globals e inserir nos campos correspondentes os valores de Username, Password e Id do projeto com os obtidos após responder o formulário e inserir também o API Token obtido**
8. **Apertar o botão de Save**
9. **Apertar o botão de atualizar Datas**
10. **Apertar o botão de Recalcular presente em cada bloco de análise**
11. **Aguardar alguns minutos**
12. **Apertar o botão de Aplicar para a página ser atualizada e mostrado os novos resultados calculados**

Em caso de alguma análise que nao seja mostrada ou que apresente resultados estranhos, realizar as etapas novamente para obter uma nova análise.

### Users

Este template possui os seguintes usuários:

1. ete@birmind.com.br - Admin que possui acesso a todos os devices. A senha para esse usuário é etebirmind123 porém não é salva quando importamos a aplicação para a nossa sandbox

Pode se alterar estes dados, adicionando, removendo ou modificando estes usuários da aplicação através da [User & Group](/applications/609557b5642331000694bd9b/experience/users) page.

## Recursos

A lista a seguir contém recurso úteis que se relacionam com a implementação desta aplicação:

* [Dashboard Overview](https://docs.app.wnology.io/dashboards/overview/)
* [Dashboard Custom HTML](https://docs.app.wnology.io/dashboards/custom-html/)
* [Workflow Overview](https://docs.app.wnology.io/workflows/overview/)
* [Experience Overview](https://docs.app.wnology.io/experiences/overview/)
* [Experience Groups](https://docs.app.wnology.io/organizations/overview/)
* [Experience Users](https://docs.app.wnology.io/user-accounts/overview/)
* [Applications](https://docs.app.wnology.io/applications/overview/)

---

Esse template foi criado por BirminD. Para obter detalhes da licença ou para enviar solicitações de recursos ou bugs, perguntas ou comentarios gerais contate-nos.

As informações de contato podem ser encontradas através do site da [BirminD](https://www.birmind.com.br/).

© 2021. All rights reserved. Powered by BirminD
