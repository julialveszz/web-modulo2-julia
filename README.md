# Modelo de arquitetura MVC - pesquisa Abandono Zero (INSPA)

Autoria de Júlia Alves de Jesus

![ ](<arquitetura mvc.jpg>)
Figura 1 - Imagem da arquitetura MVC do Draw.io 

## Descrição
Desenvolvimento de uma aplicação WEB para coleta de dados sobre as motivações de adoção/compra e abandono de animais, criando um banco de dados relacional estruturado, para o parceiro INSPA.

## Arquitetura
A arquitetura utilizada é a MVC (Model-View-Controller), que divide a aplicação nessas três camadas principais. 

## Ferramenta de Diagramação
Para desenvolver a arquitetura MVC, a ferramenta utilizada foi o Draw.io.

## Modelos (Models)

Modelo 1 - Usuários:
Uma tabela de usuários tem como atributos principais: id, nome de usuário, senha, entre outros.
Relacionamentos: Um usuário pode estar associado a vários dados coletados.

Modelo 2 - Formulários:
As tabelas referentes aos formulários (trilhas) da aplicação tem como atributos: id do usuário e as respostas às questões produzidas pelo INSPA. 
Existem 4 formulários diferentes - passado, para aqueles tutores que já tiveram um cão; presente, para aqueles que têm; futuro, para os que pretendem ter; e o nulo -- que é quando nenhum desses *paths* (caminhos) atende o caso da pessoa que está preenchendo o formulário. 

Relacionamentos: Um Dado Coletado pode pertencer a um usuário específico e ser utilizado na geração de vários relatórios (esses dados se relacionam tanto o controlador de relatório como o controlador de coleta de dados). 

## Controladores (Controllers)
 O Controlador de Login gerencia a autenticação de usuários, faz a recuperação de senhas e o registro de novos usuários, é capaz de verificar se o usuário tem permissões de administrador, e também de excluir um usuário (caso seja necessário).

O Controlador de Coleta de Dados lida com a entrada, validação e armazenamento dos dados coletados. Ele tem métodos como coletar dados, listar, validar e deletar. Se relaciona com os models dos vários formulários e também com a tela principal multifacetada, que, através de uma condicional inicial, é capaz de identificar qual trilha específica, o usuário deve preenche; ou seja, qual dos formulários aparecerá pra ele nessa tela inicial. 

O Controlador de Relatório  tem como métodos a geração, busca, filtragem, exclusão e download de relatórios. Esse controlador interage com a tela de relatórios, onde estarão dispostas as informações de forma organizada e estruturada para um usuário administrador, por exemplo.


## Views (Views)

Tela Inicial: Apresenta informações sobre o projeto (sobre), facilita a navegação para outras partes da página -- por exemplo, ao clicar no ícone de login o usuário é redirecionado à tela de login/cadastro, ou então, caso o usuário queira ver o rodapé de contatos ao final dessa página de tela inicial, ao clicar nessa seção, no navbar, é possível que a página execute um movimento de rolagem até o local que essa informação está disposta no site. Além disso, a tela incial apresenta informações importantes sobre o parceiro, utilizando blocos de texto e ilustrações/imagens, tornando a página mais dinâmica. 

Tela de Cadastro/Login: essa tela serve basicamente para criação de novos usuários e login daqueles já cadastrados, através de dados (guardados em models) de ID, usuário e senha, por exemplo.

Tela de Relatório: essa tela, que só pode ser vista com permissões específicas de usuário administrador, tem como funcionalidade exibir os relatórios gerados de forma organizada, permitindo ainda o download de arquivos e a utilização de filtros nos dados. 

## Infraestrutura
O projeto usa PostgreSQL para o banco de dados, possibilitando a integração dos controllers com models para fazer uso dos dados e cumprir a função/entrega do projeto. 
Será utilizado também Sails.js para facilitar integrações com APIs externas, combinando linguagens de programação e de marcação no desenvolvimento Web para algumas funções específicas do front-end. Essas escolhas são baseadas nos caminhos mais indicados pela equipe técnica que apoia o projeto (professores e orientadores), além de entregar um alto nível de confiabilidade, modernidade e qualidade nas estruturas. 


## Implicações da Arquitetura
A arquitetura MVC permite a adição de novas funcionalidades de forma modular, o que facilita a escalabilidade do sistema, além disso, ter uma visualização clara das funções, condições e métodos das três camadas (modelos, controladores e visualizações) permite uma maior fidelidade ao escopo do projeto, fornecendo também oportunidades de melhoria e manutenção quando necessários, já que esse é um projeto vivo, e a arquitetura neste modelo pode ajudar a identificar exatamente quais pontos de melhoria e necessidades do parceiro interessado e em qual camada as mudanças devem ser feitas. Por último, 
a testabilidade também é facilitada a partir do momemento que existe uma visualização separada dos diferentes componentes de forma isolada, tornando mais eficaz a identificação de qualquwr problema. 
