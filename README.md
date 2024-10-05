## Documento de Fluxo para Criação da APIRest Mhelp

Para o desenvolvimento e teste da API Rest do **Mhelp**, é essencial estabelecer um fluxo que promova agilidade, desempenho e organização durante todo o processo de criação. Este documento tem como objetivo delinear a ordem em que a aplicação será desenvolvida, desde a configuração do ambiente até os testes que serão realizados na API Rest.

### 1\. Criação do Repositório

→ Como teremos uma equipe dedicada ao desenvolvimento da API, é fundamental implementar um controle de versões. A criação de um repositório no **GitHub** é essencial para garantir a organização e a colaboração no projeto. 

Todos os membros da equipe terão acesso a esse repositório, permitindo um gerenciamento eficiente do código e das contribuições.

---

### 2\. Criar e Estruturar os Diretórios

→ Uma boa estrutura de projeto é uma prática fundamental para garantir a organização e facilitar a manutenção do código no futuro. 

Para isso, iremos organizar os diretórios da seguinte forma:

![](https://33333.cdn.cke-cs.com/kSW7V9NHUXugvhoQeFaf/images/0431b7c290c2fa65936f609649965072529f9358a2110c05.png)

#### Descrição dos Diretórios:

*   **config/**:
    *   Armazena configurações da aplicação, como a conexão com o banco de dados, variáveis relacionadas à autenticação e outras configurações gerais.
*   **controllers/**:
    *   Contém os “controladores”, que são responsáveis por receber as requisições, processá-las e devolver as respostas adequadas. Eles geralmente fazem chamadas para os serviços.
*   **middlewares/**:
    *   Contém middlewares para tarefas específicas, como autenticação, validação de tokens JWT, limitação de requisições (rate limiting), etc.
*   **models/**:
    *   Armazena os modelos do banco de dados (usando Sequelize, por exemplo). Esses modelos representam as tabelas no banco de dados e definem as interações com os dados.
*   **routes/**:
    *   Define as rotas da API. Cada arquivo contém as rotas relacionadas a uma entidade, como `migrantes`, `autenticação`, etc.
*   **services/**:
    *   Contém a lógica de negócio que é chamada pelos controladores. Eles geralmente lidam com operações mais complexas que envolvem interações com o banco de dados e outras camadas da aplicação.
*   **tests/**:
    *   Armazena os testes unitários e de integração. Podemos utilizar bibliotecas como `Mocha` e `Chai` para testar as funcionalidades da API.
*   **utils/**:
    *   Contém funções auxiliares e utilitárias, como validadores e constantes usadas ao longo do projeto.
*   **index.js**:
    *   Arquivo principal da aplicação. Aqui o servidor é configurado, middlewares são aplicados e as rotas são carregadas.

---

### 3\. Iniciar um Projeto Node.js com os módulos 

→ Para iniciar o projeto Node.js, utilizaremos o npm para instalar os módulos necessários ao desenvolvimento. 

Os módulos que serão instalados incluem:

`Express`, `pg`, `Sequelize`, `JWT`, `Dotenv`, `Bcrypt`, `Axios`, `Joi`, `generate-password`

Os módulos **Mocha** e **Chai** serão instalados posteriormente, quando formos criar os testes unitários.

---

### **4\. Criar Banco de Dados Local**

→ Antes de implementarmos a API Rest, será necessário criar um banco de dados local para realização de testes. Para isso, utilizaremos dados fictícios para povoar o banco e realizar as validações necessárias.

A criação do banco de dados será feita por meio de um script SQL desenvolvido especificamente para simular algumas operações. 

Cada membro da equipe deverá criar seu próprio banco de dados local, caso deseje realizar testes individuais.

---

### **5\. Começar a Codar!**

Finalmente, chegamos ao momento de codar! Nesta fase, vamos implementar a estrutura da aplicação, seguindo a organização previamente definida. 

Abaixo está a estrutura dos diretórios e suas respectivas responsabilidades:

**OBS**: Como se trata de documento para mostrar o fluxo da construção da API, todos os arquivos não estão incluídos.

1.  **src/config**
    
    Este diretório deve conter arquivos de configuração da aplicação.
    
    *   **database.js**: Configurações de conexão com o banco de dados PostgreSQL usando Sequelize.
        
2.  **src/controllers**
    
    Os controladores lidam com a lógica de negócio e a interação entre os modelos e as rotas.
    
    *   **authController.js**: Controlador responsável pela autenticação, incluindo login, registro e recuperação de senha.
    *   **migrantController.js**: Controlador para operações relacionadas a migrantes, como criação, atualização e listagem.
    *   **organizationController.js**: Controlador para operações relacionadas a organizações e ONGs, abrangendo criação, atualização e busca.
        
3.  **src/middlewares**
    
    Os middlewares são funções que têm acesso ao objeto de solicitação (req), ao objeto de resposta (res) e à próxima função middleware.
    
    *   **authMiddleware.js**: Middleware para verificar o token JWT em requisições protegidas, garantindo que apenas usuários autenticados possam acessar certas rotas.
    *   **errorHandler.js**: Middleware responsável pelo tratamento de erros, que captura e responde a erros de maneira uniforme.
    *   **validationMiddleware.js**: Middleware para validar dados de entrada usando `Joi`, garantindo que os dados recebidos estejam no formato correto.
        
4.  **src/models**
    
    Este diretório deve conter as definições dos modelos de dados.
    
    *   **migrant.js**: Modelo Sequelize para a tabela de migrantes, definindo as propriedades e relacionamentos necessários.
    *   **organization.js**: Modelo Sequelize para a tabela de organizações, com suas respectivas propriedades.
    *   **user.js**: Modelo Sequelize para a tabela de usuários, definindo as propriedas e relacionamentos necessários.
        
5.  **src/routes**
    
    As rotas definem os endpoints da API e vinculam as solicitações aos controladores.
    
    *   **authRoutes.js**: Rotas para autenticação, incluindo login e registro de usuários.
    *   **migrantRoutes.js**: Rotas para operações relacionadas a migrantes, como criar, editar e listar migrantes.
    *   **organizationRoutes.js**: Rotas para operações relacionadas a organizações, como cadastrar e buscar informações.
    *   **userRoutes.js**: Rotas para operações relacionadas a usuários, incluindo gerenciamento de informações e interações.
        
6.  **src/services**
    
    Os serviços são responsáveis pela lógica de negócio mais complexa e podem ser utilizados pelos controladores.
    
    *   **authService.js**: Lógica de autenticação, manipulação de tokens e criptografia de senhas.
    *   **migrantService.js**: Lógica relacionada à manipulação de dados dos migrantes, como busca e filtragem.
    *   **organizationService.js**: Lógica relacionada à manipulação de dados das organizações, como registro e pesquisa.
    *   **userService.js**: Lógica para gerenciar dados de usuários, incluindo criação, atualização e exclusão.
        
7.  **src/utils**
    
    Este diretório pode conter funções utilitárias que são usadas na aplicação.
    
    *   **generatePassword.js**: Função para gerar senhas utilizando a biblioteca `generate-password`.
    *   **encryptPassword.js**: Função para criptografar senhas utilizando a biblioteca `bcrypt`, garantindo segurança nas credenciais dos usuários.
        
8.  **src/tests**
    
    Para garantir que a API funcione corretamente, deve-se criar testes unitários e de integração.
    
    *   **auth.test.js**: Testes para as funcionalidades de autenticação, garantindo que login, registro e recuperação funcionem conforme esperado.
    *   **migrant.test.js**: Testes para operações relacionadas a migrantes, assegurando que as operações de criação e listagem estejam corretas.
    *   **organization.test.js**: Testes para operações relacionadas a organizações, validando o funcionamento das rotas associadas.
    *   **user.test.js**: Testes para operações relacionadas a usuários, garantindo que as interações com o sistema sejam corretas e seguras.
        
9.  **src/index.js**
    
    Este é o ponto de entrada da aplicação. Aqui, inicializamos o servidor, configura middlewares e define as rotas, garantindo que a API esteja pronta para receber requisições.
    

### **6\. Criação de Testes Unitários**

→ A criação de testes unitários é essencial para garantir a qualidade e a confiabilidade da nossa API Rest. Para isso, utilizaremos as bibliotecas **Mocha** e **Chai**.

*   **Mocha** é um framework de testes para JavaScript que permite a execução de testes de forma estruturada, enquanto **Chai** é uma biblioteca de asserções que permite verificar se os resultados dos testes estão corretos.

---

### 7\. Teste da API Rest com o Postman

→ O Postman é uma ferramenta poderosa para testar APIs, permitindo simular requisições HTTP e visualizar as respostas de forma intuitiva. Para realizar os testes na API Rest, siga os passos abaixo:

#### Configuração do Ambiente

Criar um novo ambiente no Postman para definir variáveis, como a URL base da API. Por exemplo: `http://localhost:3000/api`.

#### Criação de Coleções

Organizar as requisições em coleções. Criar uma coleção para cada parte da API, como autenticação, migrantes e organizações.

#### Testes de Requisições

*   **Teste de Login:** Enviar uma requisição POST para `{{url}}/auth/login` com um corpo JSON contendo o e-mail e a senha. Verificar se a resposta retorna o token de autenticação.
*   **Teste de Listagem de Migrantes:** Enviar uma requisição GET para `{{url}}/migrants`. Verificar se a resposta contém a lista de migrantes.

#### Verificação de Respostas

Utilizar a funcionalidade de verificação automática das respostas no Postman. Adicionar testes nas requisições para garantir que as respostas estejam corretas, como verificar o status da resposta ou a presença de propriedades específicas no corpo da resposta.

#### Execução de Testes

Após configurar as requisições e os testes, executar-os e analisar os resultados. 

O Postman fornece feedback claro sobre os testes realizados, facilitando a identificação de problemas.

---

### **8\. Deploy**

→ O próximo passo no desenvolvimento da API Rest será realizar o deploy, tornando-a acessível publicamente. Neste momento, ainda não há um local definido para a realização do deploy, mas várias opções disponíveis no mercado podem ser consideradas.

Algumas das plataformas populares para o deploy de aplicações Node.js incluem:

*   **Heroku**: Uma opção popular para hospedagem de aplicações web, que oferece um nível gratuito para começar.
*   **Vercel**: Especialmente útil para projetos JavaScript, com integração facilitada para aplicações React e Node.js.
*   **DigitalOcean**: Permite a criação de servidores virtuais para hospedar aplicações, oferecendo maior controle e personalização.
*   **AWS (Amazon Web Services)**: Oferece uma gama completa de serviços para a implantação de aplicações, embora possa ser mais complexo de configurar.

Assim que a plataforma de deploy for decidida, será possível seguir os procedimentos necessários para configurar e subir a API, garantindo que todas as funcionalidades estejam operando corretamente após a migração.

---

### **9\. Conclusão**

→ Este documento estabelece um fluxo inicial para o desenvolvimento da API Rest do Mhelp. Com uma abordagem estruturada e colaborativa, esperamos criar uma aplicação robusta e eficiente, capaz de atender às necessidades de nossos usuários.
