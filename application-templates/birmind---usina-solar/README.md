# Usina Solar

Esta aplicação para [Usina Solar](https://console.app.wnology.io/dashboards/~exportplaceholderid-dashboard-solar-0~), ilustra uma solução de monitoramento de placas solares utilizadas em geradores de energia. Este é um aplicativo, multilocatário, que pode oferecer a seus clientes soluções para monitoramento remoto de seus equipamentos, além de previsões do comportamento de algumas variáveis possibilitando identificar o problema e corrigi-lo antecipadamente, evitando a paralisação da geração de energia na placa com falhas, e consequentemente diminuindo as perdas financeiras do cliente.

## Descrição

Em uma implementação real, poderiamos usar sensores e hardware para coletar os dados e enviá-los ao WEGnology com uso de protocolos de comunicação, para que o device criado receba estes dados. Para este modelo sera disponibilizada uma tabela de dados para possibilitar ao usuário que não possui dados próprios, a utilização deste template,
para os usuários que já possuirem dados próprios, é necessário que o nome das colunas possuam os mesmos nomes das colunas do arquivo .xls.

Esse modelo apresenta um dashboard para monitoramento e manutenção preditiva de placas fotovoltaicas em usinas de geração de energia solar, com dados obtidos da tabela [Dados_PlantaSolar](https://files.wnology.io/~exportplaceholderid-application-applicationBirminDUsinaSolar-0~/Dados_PlantaSolar.xls).
Essa tabela deve ser baixada e salva em um arquivo .csv, para que seja possível importa-la para esta aplicação na seção de [Data Tables](/applications/~exportplaceholderid-application-applicationBirminDUsinaSolar-0~/data-tables), os dados serão obtidos da tabela importada e armazenados no DEVICE [Solar Power Generator](/applications/~exportplaceholderid-application-applicationBirminDUsinaSolar-0~/devices/610b3537955fa10006d5ebca/attributes), através do WORKFLOW [InsertValues](/applications/~exportplaceholderid-application-applicationBirminDUsinaSolar-0~/workflows/~exportplaceholderid-flow-insertValues-2~/develop),
estes dados são registrado para serem apresentados no DASHBOARD [Solar](https://console.app.wnology.io/dashboards/~exportplaceholderid-dashboard-solar-0~). 

Estes dados podem ser enviados para a API da BirminD para serem realizadas estimativas de algumas variáveis salvas no device, para esta aplicação foram selecionadas estimativas do KPI do Inversor e a estimativa da Performance Ratio, esta requisição de dados e envio para análise é realizada pelo WORKFLOW [Forecast](/applications/~exportplaceholderid-application-applicationBirminDUsinaSolar-0~/workflows/~exportplaceholderid-flow-forecast-1~/develop), e após gerado o resultado desta análise, os dados são então mostrado no DASHBOARD [Solar](https://console.app.wnology.io/dashboards/~exportplaceholderid-dashboard-solar-0~).

## Componentes Chave

Aqui estará sendo apresentada uma lista com os principais componentes desta aplicação desenvolvida. 

* TABELA [Dados_PlantaSolar](https://files.wnology.io/~exportplaceholderid-application-applicationBirminDUsinaSolar-0~/Dados_PlantaSolar.xls) que deve ser importada na seção [Data Tables](/applications/~exportplaceholderid-application-applicationBirminDUsinaSolar-0~/data-tables);
* DEVICE [Solar Power Generator](/applications/~exportplaceholderid-application-applicationBirminDUsinaSolar-0~/devices/610b3537955fa10006d5ebca/attributes): O dispositivo é responsável por salvar os dados coletados das tabelas pelo *workflow* servindo como referência em alguns blocos do *dashboard*;
* WORKFLOW [InsertValues](/applications/~exportplaceholderid-application-applicationBirminDUsinaSolar-0~/workflows/~exportplaceholderid-flow-insertValues-2~/develop): Insert Value é o *workflow* que possui a funcionalidade de puxar os dados da tabela selecionada no bloco de [Table: Get Rows](https://docs.app.wnology.io/workflows/data/table-get-rows/), e enviar estes dados para o *device*.
* WORKFLOW [Forecast](/applications/~exportplaceholderid-application-applicationBirminDUsinaSolar-0~/workflows/~exportplaceholderid-flow-forecast-1~/develop): Forecast é o *workflow* que possui a função de coletar os dados desejados do *device*, para gerar a ordem das análises através do bloco [Custom Node](/workflows/custom-nodes/overview/#configuring-custom-node-instances) e depois enviar o result obtido da análise para o *dashboard* desenvolvido.
* DASHBOARD [Solar](https://console.app.wnology.io/dashboards/~exportplaceholderid-dashboard-solar-0~):Painéis de fácil visualização dos dados, para acompanhamento das principais variáveis do sistema e para visualização dos resultados obtidos das análises geradas a partir do bloco de [Custom Node](/workflows/custom-nodes/overview/#configuring-custom-node-instances), no *dashboard* há um bloco com a função de atualizar os dados salvos no *device*, apagando os dados armazenados e salvando os novos dados de acordo com as tabelas selecionada no *workflow Insert Value*, e há os botões de controle da análise, onde é possível pedir para ser calculada uma análise e um botão que tem a função de aplicar o resultado  obtido da análise nos blocos presentes na tela do *dashboard*.
* EXPERIENCE [Solar BirminD](https://solarbirmind.wnology.io): Página experience que o usuário é redirecionado para uma visualização da tela de forma direta, a tela apresentada é a mesma do *dashboard*, sem precisar acessar o WEGnology, ao entrar no link, o usuário é redirecionado para uma tela de login, onde devem ser fornecidos o usuário e senha cadastrados com os usuários mostrados abaixo, após realizado o login, o usuário será redirecionado para a página onde será mostrada a tela para acompanhamento da placa solar.
### Usuários para acesso da página de Experience

Este template possui os seguintes usuários:

1. solar@birmind.com.br - Ao se importar a aplicação deve ser gerada uma nova senha para este user.

Pode se alterar estes dados, adicionando, removendo ou modificando estes usuários da aplicação através da [User & Group page](/applications/~exportplaceholderid-application-applicationBirminDUsinaSolar-0~/experience/users).

## Configuração

1. Para iniciar o uso desta aplicação, os usuários devem obter um USERNAME, PASSWORD e PROJECTID com uma licença que permita ao cliente realizar análises na API da BirminD, para isso é necessário o preenchimento do formulário da BirminD, para ir até este formulário acesse [Aqui](https://www.birmind.com.br/api-license/register/).
2. Realizar o download da tabela [Dados_PlantaSolar](https://files.wnology.io/~exportplaceholderid-application-applicationBirminDUsinaSolar-0~/Dados_PlantaSolar.xls) que deve ser importada na seção [Data Tables](/applications/~exportplaceholderid-application-applicationBirminDUsinaSolar-0~/data-tables), que também podem ser encontradas nos [files](/applications/~exportplaceholderid-application-applicationBirminDUsinaSolar-0~/files).
    - O usuário pode utilizar estas tabelas de demonstração nesta aplicação, ou inserir seus próprios dados, desde que seja mantido os nomes das colunas dos arquivos baixados.
3. Após download das tabelas, estas devem ser salvas em .csv e posteriormente importadas na seção [Data Tables](/applications/~exportplaceholderid-application-applicationBirminDUsinaSolar-0~/data-tables).
4. Deve-se acessar a seção dos [WORKFLOWS](/applications/~exportplaceholderid-application-applicationBirminDUsinaSolar-0~/workflows), e realizar as seguintes ações:
    - Habilite o workflow [Forecast](/applications/~exportplaceholderid-application-applicationBirminDUsinaSolar-0~/workflows/~exportplaceholderid-flow-forecast-1~/develop) selecionando o toggle switch presente do lado do ícone de lixeira, ficando com a cor verde.
    - Habilite o workflow [InsertValues](/applications/~exportplaceholderid-application-applicationBirminDUsinaSolar-0~/workflows/~exportplaceholderid-flow-insertValues-2~/develop) selecionando o toggle switch presente do lado do ícone de lixeira, ficando com a cor verde.
5. Após ativar os *workflows* o usúario deverá acessar o WORKFLOW [InsertValues](/applications/~exportplaceholderid-application-applicationBirminDUsinaSolar-0~/workflows/~exportplaceholderid-flow-insertValues-2~/develop), e seguir algumas etapas:
    - Em cada bloco nomeado de Linhas Tabela, o usuário deverá acessar o bloco e inserir no campo Value o número de linhas da tabela que o workflow será responsável por coletar os dados, como padrão para a tabela fornecida no bloco está inserido o valor 3154 que é o número de linhas da tabela [Dados_PlantaSolar](https://files.wnology.io/~exportplaceholderid-application-applicationBirminDUsinaSolar-0~/Dados_PlantaSolar.xls). 
    - Acessar cada bloco loop, e no bloco [Table: Get Rows](https://docs.app.wnology.io/workflows/data/table-get-rows/), deve ser selecionada a tabela a qual o workflow ficará responsável por coletar os dados e enviar ao dispositivo, cada linha de *workflow* fica responsável por enviar uma *tabela*.
6. Acessar o workflow [Forecast](/applications/~exportplaceholderid-application-applicationBirminDUsinaSolar-0~/workflows/~exportplaceholderid-flow-forecast-1~/develop) que já deve estar ativado, e realizar os passos a seguir:
    - Selecionar cada bloco de [Custom Node](https://docs.app.wnology.io/workflows/custom-nodes/overview/#configuring-custom-node-instances), e inserir no campo BirminD Username, BirminD Password e Project Id de cada bloco, o USERNAME, PASSWORD e PROJECTID obtido por e-mail após preenchimento do formulário que pode ser acessado atráves do seguinte [Link](https://www.birmind.com.br/api-license/register/).
7. Assim que realizadas todas estas etapas, o usuário deverá acessar o DASHBOARD [Solar](https://console.app.wnology.io/dashboards/~exportplaceholderid-dashboard-solar-0~) para poder visualizar a tela de monitoramento do cliente. Ao se acessar o *dashboard* o usuário deverá:
    - Selecionar o botão atualizar dados, o qual da um trigger no *WORKFLOW INSERT VALUE* para poder enviar os dados das *tabelas* importadas para o *device*.
    - Apertar o botão de recalcular, para dar um trigger no *WORKFLOW FORECAST* e gerar um pedido de análise para os dados de KPI do Inversor e Performance Ratio das *tabelas*.
    - Aguardar alguns minutos para selecionar o botão aplicar, para a página ser atualizar, e novamente dar um trigger no *WORKFLOW FORECAST* e coletar o resultado das análises enviadas.
    - Em caso de não aparecer os resultados de análise após selecionar o botão aplicar, aguardar mais um tempo para selecionar novamente o botão, isto ocorre pois a API da BirminD pode estar com uma fila de análises o que acarreta em uma maior demora para se obter estes resultados.

Após realizadas estas etapas, o usuário poderá visualizar no *dashboard* como seria a tela de monitoramento de uma placa fotovoltaica, atentando-se ao fato de que este *dashboard* é totalmente customizável, tanto para as variáveis monitoradas como as variáveis preditas, para isso o cliente deve entrar em contato com a equipe da BirminD através do [fórum](https://forums.app.wnology.io/) desta aplicação, ou contactando a BirminD
através do seu site acessando [Aqui](https://www.birmind.com.br/).

## Documentação Auxiliar

* Veja de maneira mais completa todos os passos e explicação para utilização deste template atráves do arquivo [README](https://files.wnology.io/~exportplaceholderid-application-applicationBirminDUsinaSolar-0~/README.md).

## Sobre

Este modelo está em sua versão 2.0.0

Para esclarecer qualquer dúvida ou resolução de problemas, recomendamos o uso do [fórum](https://forums.app.wnology.io/) ou entrar em contato conosco através do nosso [Site](https://www.birmind.com.br/).

Esse template foi criado por BirminD. Para obter detalhes da licença ou para enviar solicitações de recursos ou bugs, perguntas ou comentarios gerais contate-nos.

As informações de contato podem ser encontradas através do site da [BirminD](https://www.birmind.com.br/).

© 2021. All rights reserved. Powered by BirminD

Licenciado sob a licença MIT.

https://www.birmind.com.br

https://www.weg.net