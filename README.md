# Pessoa CRUD
.![image](https://github.com/VsN7/elotech/assets/47636635/de052378-ed8c-4a87-bad2-89bf23fc7e9d)


## Descrição do projeto
Esse projeto é uma API responsável por criar, alterar, deletar ou buscar dados referente a rotina de pessoa e seus contatos.

## Tecnologias utilizadas
- Java
- Spring Boot
- PostigreSQL
- JUnit
- AWS
- Render

## Como utilizar a API

- Recomendo que utilize a aplicação Postman para melhor entendimento da API, também é possível verificar as requisições via URL no proprio navegador (exemplo: Google Chrome).

Link para a instação do Postman: https://www.postman.com/downloads/

## Lista de Requisições

### Listar todas as pessoas e seus contatos vinculados:
- get https://elotech-7e3s.onrender.com/api/person/find-all
#### cURL:
> curl --location --request GET 'https://elotech-7e3s.onrender.com/api/person/find-all' \
> --header 'Content-Type: application/json'
### Listar apenas uma pessoa e seus contatos vinculados
- get https://elotech-7e3s.onrender.com/api/person/{id}
#### cURL:
> curl --location --request GET 'https://elotech-7e3s.onrender.com/api/person/1' \
> --header 'Content-Type: application/json'
### Cadastrar uma nova pessoa e seu(s) respectivo(s) contato(s):
- post https://elotech-7e3s.onrender.com/api/person
#### cURL:
> curl --location --request POST 'https://elotech-7e3s.onrender.com/api/person' \
> --header 'Content-Type: application/json' \
> --data-raw '{   
>    "name": "Vitor Santos do Nascimento",
>    "legalIdentifier": "056.647.421-27",
>    "dateBirth": "1996-11-16T12:00:00",
>    "contactList": [
>        {
>            
>            "email" : "teste1@hotmail.com",
>            "name": "amanda nascimento",
>            "telephone": "(44) 99827-1232"
>        },
>        {
>            
>            "email" : "teste2@hotmail.com",
>            "name": "vitor sn",
>            "telephone": "(44) 99827-9999"
>        },
>        {
>            
>            "email" : "teste3@hotmail.com",
>            "name": "carlos santos",
>            "telephone": "(44) 99827-9218"
>        }
>    ]
>
> }'
### Deletar a pessoa e todos os seus contatos vinculados:
- delete https://elotech-7e3s.onrender.com/api/person
#### cURL:
> curl --location --request DELETE 'https://elotech-7e3s.onrender.com/api/person' \
> --header 'Content-Type: application/json' \
> --data '{   
>    "id":1,
>    "name": "Vitor Santos do Nascimento",
>    "legalIdentifier": "056.647.421-27",
>    "dateBirth": "1996-11-16T12:00:00",
>    "contactList": []
>
> }'
### Editar o cadastro da pessoa e/ou adicionar novo contato e/ou remover contato existente e/ou editar contato existente  
- put https://elotech-7e3s.onrender.com/api/person
#### cURL:
> curl --location --request PUT 'https://elotech-7e3s.onrender.com/api/person' \
> --header 'Content-Type: application/json' \
> --data-raw '{
>    "id": 1,  
>    "name": "Vitor Santos do Nascimento Update",
>    "legalIdentifier": "056.647.421-27",
>    "dateBirth": "1996-11-16T12:00:00",
>    "contactList": [
>        {
>            "id" : 1,
>            "email" : "update@hotmail.com",
>            "name": "update nascimento",
>            "telephone": "(44) 99827-1232"
>        }
>        
>    ]
>
> }'
- OBS: dessa maneira o endPoint irá alterar o cadastro da pessoa e o cadatro do contato com ID 1, e também irá remover todos os outros que não estão presente na lista... (caso haja algum contato a mais, o endPoint irá adiciona-lo na lista)
#### Legenda
- get - busca por registros
- post - criação de novos registros
- put - edição de registros
- delete - exclusão de registros

### Dados para acesso no banco postigres deployado na AWS:
> spring.datasource.url=jdbc:postgresql://db-vitor7-sn.cz8iq0us43k4.us-east-1.rds.amazonaws.com:5432/person

> spring.datasource.username=root

> spring.datasource.password=12345678
