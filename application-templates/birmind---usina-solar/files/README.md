# TEMPLATE - Usina Solar

Esta aplicação ilustra uma solução de monitoramento de placas solares utilizadas em geradores de energia. Este é um aplicativo, multilocatário, que pode oferecer a seus clientes soluções para monitoramento remoto de seus equipamentos, além de previsões do comportamento de algumas variáveis.

## Componentes Chave

Aqui estará sendo apresentado um README da aplicação desenvolvida. Alguns itens são destacados a baixo:

* Aplicativo desenvolvido para predição e monitoramento de dados em tempo real, de painéis solares usado em geradores.
* Visão geral ao vivo e histórica e painéis do dispositivo.
* Painéis de fácil visualização para acompanhamento das principais variáveis do sistema.

## Setup

* Habilite o workflow Forecast.
* Habilite o workflow InsertValues.

Realizar o download dos arquivos .xls para obter uma tabela com dados de demonstração, mas que pode ser utilizada como template para inserção de dados do próprio usuário, conservando o padrão de nome para as colunas, para o mesmo utilizar essas tabelas para realizar as análises nesta aplicação.

Para inserir estas tabelas nesta aplicação elas devem ser salvas antes em um formato .csv, salvando apenas os dados desconsiderando salvar as fórmulas do arquivo, para que o wegnology reconheça esta tabela e não ocorra problemas.
O usuário em caso de decidir a inserir os seus próprios dados na tabela deve-se atentar ao fato desta plataforma não conseguir armazenar no device dados mais antigos do que 30 dias atrás, portanto em caso de decisão por inserir os seus próprios dados nas tabelas para salvar o csv e inseri-las na aplicação deve se ter um atenção com esta pequena limitação.

## Obter licença

Para se gerar as análises, deve-se responder um formulário para cadastro do cliente, cuja finalidade seja o usuário obter por e-mail um USERNAME e PASSWORD, além de um Id de Projeto que serão utilizados nas configurações de blocos para se gerar as análises.

Ao serem obtidos USERNAME, PASSWORD e o ID de PROJETO, deve-se salva-los e acessar o workflow chamado de Forecast, neste workflow deve-se acessar o bloco de CN custom node, de cor rosa, e nos campos BirminD Username e BirminD Password deve ser substituidos pelos dados obtidos como resposta do forms no e-mail do cliente.

Para se obter essa licença e responder o formulário, acesse [Aqui](https://www.birmind.com.br/api-license).

## Workflows

Será explicado agora brevemente o funcionamento de cada Workflow e os processos a se realizar no workflow para gerar uma análise.

As análises geradas estão configuradas para uma análise de acordo com os dados de demonstração, para dados próprios algumas configurações deveram ser alteradas para se obter melhores análises e consequemente melhores resultados.

### InsertValues

Quando ativado o workflow InsertValues, ele irá ativar os botões presentes no dashboard, para que o usuário consiga realizar as ações de configuração para inserir os dados das tabelas importadas para a aplicação nos devices.
Os dados apresentados nos dashboards são dados demonstrativos obtidos das tabelas. Para acessar e verificar as tabelas que existem salvas, deve-se acessar a seção de files.

Para obter essas tabelas, o usuário deve fazer o download dos arquivos .xls e assim utiliza-las com os dados de demonstração, ou para utilizar esta tabela como um template padrão e a partir das colunas ja estabelecidas, adicionar o seu próprio dado para realizar as análises. Para que assim o usuário consiga estar sempre realizando observações com dados de timestamp atuais, e realizar as ações necessárias para se obter uma demonstração do funcionamento desta aplicação.

Após o download destas tabelas e já possuindo os dados corretos armazenados, deve-se salvar estas tabelas no formato .csv, e assim importar estas tabelas em .csv para a aplicação. Sendo realizada esta etapa, o usuário deve acessar este workflow, e ir em cada bloco de [Storage: Set Value](https://docs.app.wnology.io/workflows/data/store-value/) e ao selecionar o bloco para a Key value, no item de Value você deverá substituir o valor já salvo pelo valor do número de linhas da tabela que será utilizada, em caso de utilizar as tabelas de demonstração para as análises esta etapa pode ser desconsiderada. 
Posteriormente a esta etapa, deve-se entrar no bloco de loop de cada workflow de análise (mostrado nos blocos de nota qual workflow corresponde a determinada análise) e dentro deste bloco, no bloco [Table: Get Rows](https://docs.app.wnology.io/workflows/data/table-get-rows/) o usuário deve escolher a tabela que corresponde aos dados daquela análise a ser realizada.

### Forecast

Quando ativado o workflow Forecast, ele irá permitir gerar as análises, a partir dos botões presente no dashboard, o botão além de gerar uma análise a ser feita, irá deletar o storage local do workflow, o que permite ser realizada uma nova análise de predição dos novos dados inseridos no device.

A função deste workflow é a de gerar e replicar a análise de predição para o dashboard, quando apertado o botão de calcular, ele irá enviar os dados para ser realizada a análise, após alguns minutos quando é pressionado o botão de aplicar a pagina do browser será atualizada, e automaticamente ocorre uma requisição ao webhook de trigger presente no workflow, para puxar o resultado da análise.
A partir do envio dos dados, é aguardado o resultado da análise realizada. Após disponibilizado o resultado, o workflow envia os dados de resultado para os blocos do dashboard, e é realizado o plot dos dados que serão msotrados na tela.

Deve-se alterar nos blocos de custom node, os campos de BirminD Username, BirminD Password e Id de Projeto, inserindo neles o USERNAME, PASSWORD e PROJECTID, enviados para o e-mail do cliente após responder o formulário, que pode ser acessado neste [Link](www.birmind.com.br/api-license).

## Dashboards

Este modelo inclui dois painéis. Um exibe uma visão geral da forma que os dados serão apresentados. E o outro exibe os dados de um device específico selecionado através da variavel context. 

### Solar Overview Dashboard

O painel Solar Overview, usa uma variável de contexto, para identificar o usuário que está logado ao sistema visualizando as informações do painel em questão. Os blocos do dashboard, apresentam as informações gerais que são lidas dos device cadastrados nesta aplicação.

Ao se acessar a experience page PageInicial, o usuário de acesso é salvo como a variavel de contexto utilizada pelo dashboard, para identificar os devices que estão associados a este usuário.

### Solar Dashboard

O dashboard Solar, usa uma variável de contexto do dispositivo, para exibir os detalhes específicos do dispositivo selecionado. Os blocos presentes nesse dashboard, apresentam as principais informações a serem monitoradas para,
 uma boa análise dos dados que o paínel solar selecionado está apresentando.

A PageDevice é a experience page do painel deste dispositivo.

Neste workflow está presente os botões para atualizar os dados que foram importados para esta aplicação na seção de Data Tables, há também outros 2 botões presentes nesse dashboard, para Calcular uma nova predição, o qual ao ser selecionado irá gerar as 2 predições para o KPI do Inversor e da PerformanceRatio, o botão após o click será desativado e uma mensagem será exibida para aguardar 15 minutos
e após esses 15 minutos, deverá ser feito o click no botão aplicar para atualizar a página do browser e assim apresentar na tela os resultados obtidos das análises.

## Experience

Este template inclui uma experience page Solar Page, que ao acessá-la com um usuário válido, será redirecionado para a pagina de overview, onde poderá selecionar o dispositvo que se deseja ler os dados atuais coletados naquele dia.
Quando o usuário efetua o login, é redirecionado para a pagina experience Solar Overview, é apresentado um painel com uma visão geral da apresentação dos dados dos dispositivos, além de uma lista de dispositivos associados ao usuário de login, para acessá-los e assim verificar os status atuais do device.

Ao selecionar um dispositivo específico, o usuário será redirecionado para uma página Solar, que será apresentado o dashboard contendo os detalhes especificos deste dispositivo. Neste dashboard também é apresentado um timeseries do kpi e da performance ratio e a estimativa para os próximos 4 dias.
Já será apresentada uma estimativa com os ultimos dados inseridos, porém é possível realizar uma nova análise para os dados em timestamp atual. 

Para facilitar a visualização das etapas para se gerar as análises e obter as respostas, será mostrada a ordem na lista abaixo:

1. **Fazer o download dos arquivos de tabelas, escolher quais dados usar e salvar no formato .csv**
2. **Importar as tabelas em csv para o Data Tables para poder puxar os dados e salvá-los nos devices**
3. **Acessar workflow Insert Values e em cada workflow de análise colocar os valores corretos no Value do bloco Storage: Set Value de acordo com a tabela que será utilizada para aquela análise**
4. **Acessar workflow Insert Values e em cada workflow de análise selecionar a tabela correta a qual os dados para análise devem ser obtidos no bloco Table: Get Rows**
5. **Apertar o botão de Save & Deploy**
6. **Acessar o workflow de análise e substituir os valores de Username e Password com os obtidos após responder o formulário**
7. **Apertar o botão de Save & Deploy**
8. **Apertar o botão de atualizar Dados**
9. **Apertar o botão de calcular para realizar o cálculo**
10. **Aguardar o tempo informado na mensagem e após apertar o botão de aplicar**

Após realizar estas etapas, você deve atualizar a pagina do seu browser e aguardar uns minutos enquanto a análise preditiva é realizada, Em caso de alguma análise que nao seja mostrada ou que apresente resultados estranhos, realizar as etapas novamente para obter uma nova análise.

Para acessar a página de login do experience, basta acessar a página Solar Page, onde será levado para a página de login, onde poderá entrar com os usuários apresentados abaixo.


### Users

Este template possui os seguintes usuários:

1. solar@birmind.com.br - Admin que possui acesso a todos os devices. A senha para esse usuário é solar123, talvez seja necessario criar uma nova senha.

Pode se alterar estes dados, adicionando, removendo ou modificando estes usuários da aplicação através da [User & Group](/applications/607486e1ca605a0007c7b3bc/experience/users) page.

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