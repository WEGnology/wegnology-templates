# Módulo EXPERIENCE (Users and Groups)

O módulo **EXPERIENCE**
é o meio pelo qual pode-se construir uma interface web para usuários interagirem com o que foi desenvolvido na plataforma. Esse módulo fornece
algumas ferramentas que foram utilizadas nesse modelo para entregar uma aplicação de controle de usuários com sistema de login, cadastro e exclusão de contas, 
permissões por grupos de usuários, navegação entre páginas e muito mais.  

## Descrição 

Esse modelo é uma aplicação completa de controle de usuários. Foram utilizados os componentes *page*,
*component*, *layout*, *endpoint* e *experience workflows* para controlar as ações dos usuários na aplicação, restringindo o acesso de usuários comuns a página inicial
e permitindo ações como cadastro e exclusão de contas apenas para usuários com permissões de administrador, ou seja, aqueles que pertencem ao grupo "adm". 

## Componentes Chaves 

* LAYOUT *layout-base*:
Um *layout* fornece componentes que precisam estar presentes em diferentes páginas, poupando o trabalho de reescrever código; 
* PAGE *Login*: 
É a página inicial da aplicação, onde o usuário informa suas credenciais para serem autenticadas pelo WORKFLOW *Endpoint/login*;
* PAGE *Home*: 
Essa página contém apenas o DASHBOARD *Dashboard* e pode ser acessada por qualquer usuário, desde que esse seja autenticado;
* PAGE *Create Account*:
Essa página contém um formulário de cadastro de usuários que ao clicar no botão "confirmar cadastro" o WORKFLOW *POST api/v2/user*
valida os dados informados para só então enviar um email de configuração. Somente usuários do grupo "adm" podem acessar;
* PAGE *Delete Account*:
Essa página apresenta uma lista com todos os usuários da aplicação, nela você pode excluir qualquer um que não seja do grupo "adm" clicando na "lixeira", assim que efetuar essa ação
as informações do usuário na linha selecionada são enviadas ao WORKFLOW *DELETE api/v1/user*
para esse ser removido da aplicação. Somente usuários do grupo "adm" podem acessar essa página;
* COMPONENT *js-imports*: 
Componente que importa arquivos JS necessários para algumas funcionalidades, é importante que todos os imports estejam salvos na aplicação (em *Files*) 
e que esse componente seja importado em todas as páginas antes da *tag* "script";
* COMPONENT *js-notify*: 
Componente que apresenta uma notificação personalizada com parâmetros definidos pelo usuário, deve ser instanciado após o componente "js-import" e somente em páginas que seja necessário apresentar
alguma notificação;  
* ENDPOINT *GET/*:
Esse endereço redireciona o usuário para a página de *login* quando ainda não autenticado, caso contrário ele é redirecionado para a página home;  
* ENDPOINT *POST/login*:
Caminho de envio das credenciais para autenticação, esse *endpoint* é invocado pela tela de *login* para enviar as credenciais informadas ao WORKFLOW *Endpoint/login* que irá então autentica-las;  
* ENDPOINT *DELETE/delete-account*:
Esse endereço envia os dados do usuário da linha selecionada na PAGE *Delete Account* para o WORKFLOW *DELETE/api/v1/user* que irá então remove-lo da aplicação;
* WORKFLOW *Endpoint/login*: 
É acionado ao usuário acessar o *endpoint* "/" e quando credenciais são enviadas a partir da tela de *login*, avalia qual foi o modo de acesso, se as credenciais informadas são válidas e redireciona o usuário
para tela inicial caso seja autenticado;
* WORKFLOW *POST/api/v2/user*: 
Primeiro passo para o cadastro de usuário, é acionado ao enviar os dados de cadastro a partir da página *Create Account*, 
valida se o usuário ainda não existe e envia um email de confirmação;
* WORKFLOW *GET/validate-email*:
Segundo passo do cadastro de usuário, é acionado a partir do email de confirmação, se o *token* não for expirado um novo usuário é cadastrado e já pode realizar *login* na aplicação;
* WORKFLOW *DELETE/api/v1/user*: 
Acionado ao usuário clicar na lixeira, avalia os dados do usuário da linha selecionada e o exclui da aplicação;
* GROUP *normal*:
Usuários que pertencem a esse grupo só podem acessar a página inicial da aplicação;
* GROUP *adm*:
Usuários que pertencem a esse grupo possuem acesso a todas as páginas além de poderem cadastrar e excluir outros usuários na aplicação;
* DASHBOARD *Dashboard*: 
É apresentado na PAGE *Home*,
contém gráficos com os dados do DEVICE *random-device* que fornece valores simulados apenas para popular esse *dashboard*;

## Configuração 

1. Informe uma nova senha para o usuário "admin": 
    - Navegue até Experience *Users & Groups*;
    - Selecione o usuário "user@adm.com";
    - Selecione o *check-box* "Change Password?";
    - Adicione uma senha e salve a alteração.
2. Para apresentar valores no *dashboard* é necessário forçar um valor no device "random-device": 
    - Navegue até *Devices*;
    - Selecione o *device* "random-device";
    - Clique em "Device Actions" no canto superior direito;
    - Escolha "Force State";
    - Selecione o atributo "attribute", informe um valor inteiro e clique em "Force Report State". 
3. Defina o *slug* da sua aplicação para acessa-la pelo seu navegador:
    - Navegue até *Experience Domains & Slugs*;
    - Clique no botão verde com o texto "Add";
    - Salve a alteração clicando em "Create Slug";
    - Obtenha o link da aplicação clicando no botão de ação do seu *slug* ou navegue até *Experience Edit* e copie o link no canto superior direito.

Finalizando essas configurações você conseguirá acessar a aplicação através do seu navegador e os demais usuários já podem ser adicionados a partir da tela de cadastro.
Ao enviar os dados de um novo usuário, é enviado um email de confirmação para o endereço informado e o cadastro só é efetivado quando esse usuário realizar a confirmação.

## Documentação Auxiliar 

* Para mais informações sobre o módulo *EXPERIENCE*
consulte a documentação da plataforma.

## Sobre 

Este modelo está em sua versão 1.0.0

Para esclarecer qualquer dúvida, recomendamos o uso do [fórum](https://forums.app.wnology.io/).

Copyright © 2023 WEG SA. Todos os direitos reservados.

Licenciado sob a licença MIT.

https://www.weg.net