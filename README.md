# Microsserviço de Categorias – Projeto Final Gestão Financeira Pessoal

## Descrição

Este é o microsserviço responsável pela gestão das **categorias de gasto** dentro do sistema de **Gestão Financeira Pessoal**.

Desenvolvido em **Spring Boot**, com persistência em **PostgreSQL**, comunicação assíncrona via **RabbitMQ (Producer)** e documentação gerada com **Swagger**.

---

## Tecnologias utilizadas

- Java 17  
- Spring Boot  
- PostgreSQL  
- RabbitMQ  
- Swagger (OpenAPI)  
- Maven  

---

## Funcionalidades implementadas

- CRUD completo de Categorias (Create, Read, Update, Delete)  
- Swagger para documentação dos endpoints  
- Configuração de CORS global (Permite acesso ao back-end via Flutter e outras origens)  
- Integração com RabbitMQ (Envia mensagem para a fila sempre que uma nova categoria é criada)  

---

## Endpoints disponíveis

| Operação                         | Método HTTP | Endpoint           |
|---------------------------------|-------------|--------------------|
| Listar todas as categorias       | GET         | `/categories`      |
| Buscar uma categoria por ID      | GET         | `/categories/{id}` |
| Criar nova categoria             | POST        | `/categories`      |
| Atualizar uma categoria existente| PUT         | `/categories/{id}` |
| Deletar uma categoria            | DELETE      | `/categories/{id}` |

---

## Exemplo de Body para POST (JSON)

```json
{
  "nome": "Alimentação",
  "descricao": "Gastos com comida"
}

Configuração de CORS
Para permitir que o aplicativo Flutter e outras origens consigam consumir os endpoints REST deste microsserviço, foi criada a configuração global de CORS conforme abaixo:
package com.leticia.categorias;

import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.web.servlet.config.annotation.CorsRegistry;
import org.springframework.web.servlet.config.annotation.WebMvcConfigurer;

@Configuration
public class CorsConfig {

    @Bean
    public WebMvcConfigurer corsConfigurer() {
        return new WebMvcConfigurer() {
            @Override
            public void addCorsMappings(CorsRegistry registry) {
                registry.addMapping("/**")
                        .allowedOrigins("*")
                        .allowedMethods("GET", "POST", "PUT", "DELETE", "OPTIONS")
                        .allowedHeaders("*");
            }
        };
    }
}

Integração com RabbitMQ
Este microsserviço atua como Producer e envia mensagens para a fila RabbitMQ toda vez que uma nova categoria é criada. A conexão e configuração do RabbitMQ estão definidas no arquivo application.properties:
spring.rabbitmq.host=localhost
spring.rabbitmq.port=5672
spring.rabbitmq.username=guest
spring.rabbitmq.password=guest

Como rodar localmente
Certifique-se que o PostgreSQL e o RabbitMQ estão rodando localmente.

Configure o arquivo application.properties com suas credenciais de banco de dados e RabbitMQ.

No terminal, execute:
mvnw spring-boot:run





