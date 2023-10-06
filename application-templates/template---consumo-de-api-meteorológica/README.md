# TEMPLATE - Consumo de API Meteorológica

Esse modelo é a implementação do [*WEGnology Walkthrough*](https://docs.app.wnology.io/getting-started/walkthrough/#wegnology-walkthrough), o nosso passo a passo inicial.
Neste passo a passo é fornecido um guia de como desenvolver uma estação meteorológica na plataforma utilizando dados de uma API externa.


## Descrição 

Em uma implementação real, você usaria sensores e hardware para capturar as informações meteorológicas e enviar esses dados para WEGnology usando MQTT ou HTTP. Para este modelo, em vez de hardware real, usamos a API OpenWeather para simular o hardware que envia dados meteorológicos.

Desta forma, mesmo sem ter algum dispositivo físico, é possível experimentar várias funções da Plataforma WEGnology.

Esse modelo é uma estação meteorológica que supervisiona temporalmente o clima de uma localização com informações providas pela API [*OpenWeather*](https://openweathermap.org/). 
Os dados são requisitados temporalmente através do WORKFLOW *Weather Grabber* e armazenados no DEVICE *Weather*, esses dados registrados são então apresentados no DASHBOARD *Weather Station*. 

## Componentes Chaves 

* DEVICE *Weather*: 
Nessa aplicação, o dispositivo é responsável por guardar os dados de clima obtidos pelo *workflow* e serve como referência para os blocos no *dashboard*; 
* WORKFLOW *Weather Grabber*: 
É a parte que realiza a requisição HTTP e informa os dados recebidos para os atributos do DEVICE *Weather*.
Comunica-se com a API por meio do NODE "*Busca dados*", nele é informado o link do serviço contendo a chave de acesso e a localização que será monitorada.
Esses valores são armazenados em variáveis globais que podem ser facilmente alteradas a qualquer momento, fique atento ao tópico "Configuração" para saber como alterá-las. **Precisa ser ativado pelo usuário**;
* DASHBOARD *Weather Station*: É no *dashboard* que as informações recebidas pelo *workflow* serão apresentadas. Cada bloco precisa referenciar o atributo equivalente do *device*, por exemplo, para mostrar a temperatura
o bloco precisa referenciar o atributo *temp*;
 
## Configuração

1. Alguns serviços requisitam uma permissão apropriada para serem utilizados. No caso desse modelo, cadastre-se no [OpenWeather](https://home.openweathermap.org/users/sign_up) 
para obter a chave de acesso;
2. Assim que já estiver cadastrado obtenha sua chave de API:
    - Clique no nome do seu usuário;
    - Escolha a opção "My API Keys";
    - Copie sua chave e a guarde em um lugar de fácil acesso, pois ela será utilizada nos passos seguintes.
3. Navegue até *Application Globals* para alterar os valores das variáveis globais:
    - Selecione a variável "*gps_location*" e informe no campo "value" a latitude e longitude da localização que deseja monitorar;
    - Repita o mesmo processo para a variável "*api_key*" e cole no campo "value" a chave obtida no passo 2. 
4. Ative o WORKFLOW *Weather Grabber*, 
para isso basta clicar na palavra "*Enable*" presente no aviso localizado no canto inferior direito da tela.

Após finalizar as configurações, o *workflow* enviará atualizações climaticás sobre a localização informada a cada 10 minutos (esse tempo pode ser alterado no bloco "*Timer*"). Os dados
serão armazenados no DEVICE *Weather* e poderão ser visualizados através do DASHBOARD *Weather Station*. 

## Documentação Auxiliar 

* Veja todos os passos de desenvolvimento desse modelo no [WEGnology Walkthrough](https://docs.app.wnology.io/getting-started/walkthrough/#wegnology-walkthrough).
* OpenWeather é uma API que fornece dados meteorológicos de maneira simples. Esse serviço apesar de ser pago possui um plano gratuito bastante generoso que fornece 1.000.000
de chamadas mensais e até 60 por minuto. Consulte a [tabela de preços](https://openweathermap.org/price) caso deseje mais detalhes sobre os planos
ou acesse sua [documentação](https://openweathermap.org/current) para saber mais sobre essa API.

## Sobre 

Este modelo está em sua versão 1.0.0

Para esclarecer qualquer dúvida, recomendamos o uso do [fórum](https://forums.app.wnology.io/).

Copyright © 2023 WEG SA. Todos os direitos reservados.

Licenciado sob a licença MIT.

https://www.weg.net