Microsserviço de Categorias – Projeto Final Gestão Financeira Pessoal
Descrição
Este é o microsserviço responsável pela gestão das categorias de gasto dentro do sistema de Gestão Financeira Pessoal.

Desenvolvido em Spring Boot, com persistência em PostgreSQL, comunicação assíncrona via RabbitMQ (Producer) e documentação gerada com Swagger.

Tecnologias utilizadas
Java 17

Spring Boot

PostgreSQL

RabbitMQ

Swagger (OpenAPI)

Maven

Funcionalidades implementadas
CRUD completo de Categorias
(Create, Read, Update, Delete)

Swagger para documentação dos endpoints

Configuração de CORS global
(Permite acesso ao back-end via Flutter e outras origens)

Integração com RabbitMQ
(Envia mensagem para a fila sempre que uma nova categoria é criada)

Endpoints disponíveis
Operação	Método HTTP	Endpoint
Listar todas as categorias	GET	/categories
Buscar uma categoria por ID	GET	/categories/{id}
Criar nova categoria	POST	/categories
Atualizar uma categoria existente	PUT	/categories/{id}
Deletar uma categoria	DELETE	/categories/{id}

Exemplo de Body para POST (JSON)
json
Copy
{
  "nome": "Alimentação",
  "descricao": "Gastos com comida"
}
Configuração de CORS
Foi implementada uma configuração global de CORS para permitir requisições de qualquer origem, garantindo que o aplicativo Flutter consiga consumir os endpoints.

Integração com RabbitMQ
Este microsserviço atua como Producer, enviando mensagens para a fila sempre que uma nova categoria é criada.

Como rodar localmente
Certifique-se de que o PostgreSQL e o RabbitMQ estão rodando localmente.

Configure o arquivo application.properties com suas credenciais de banco de dados e RabbitMQ.

No terminal, execute:

bash
Copy
mvnw spring-boot:run
