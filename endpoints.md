# Documentação da API 

## Serviço de Transcrição

Esta documentação descreve como consumir o endpoint de transcrição de áudio da aplicação. O objetivo é enviar um arquivo de áudio e receber o texto correspondente.

## Transcrever Áudio

### Endpoint
```POST /api/transcribe```


### Descrição

Envia um arquivo de áudio para ser processado pelo servidor e retorna o texto transcrito.

### Requisição (Request)

-   **Método:** `POST`
-   **Content-Type:** `multipart/form-data`
-   **Corpo (Body):** A requisição deve conter um corpo do tipo `form-data` com a seguinte chave:
    -   `file`: O arquivo de áudio a ser transcrito (ex: `.wav`, `.mp3`, `.m4a`, etc.).

### Respostas (Responses)

#### ✅ Sucesso (200 OK)

Retornado quando a transcrição é bem-sucedida.

-   **Content-Type:** `application/json`
-   **Corpo (Body):** Um objeto JSON contendo o resultado da transcrição. O serviço Vosk retorna um JSON, então o resultado final será algo como:
 
Nota: Substitua http://localhost:8080 pela URL base da sua API e /caminho/para/seu/arquivo_de_audio.wav pelo caminho real do arquivo que você quer testar.

### Exemplo de Implementação em JavaScript (Fetch API)

Aqui está um exemplo prático de como chamar a API a partir de um código frontend em JavaScript.


#### ❌ Erro: Arquivo Vazio (400 Bad Request)

Retornado se nenhum arquivo for enviado ou se o arquivo estiver vazio.

-   **Corpo (Body):**


#### ❌ Erro: Falha no Servidor (500 Internal Server Error)

Retornado se ocorrer um erro inesperado durante o processamento do áudio no servidor (ex: falha na conversão, erro no modelo de IA, etc.).

-   **Corpo (Body):**


--------

## Gerenciamento de Contatos

Esta documentação detalha os endpoints disponíveis para criar, listar e gerenciar contatos de emergência.

---

### 1. Listar Todos os Contatos

Retorna uma lista com todos os contatos cadastrados no sistema.

#### Endpoint
```GET /api/contacts```

#### Resposta de Sucesso (200 OK)

-   **Content-Type:** `application/json`
-   **Corpo (Body):** Um array de objetos `Contact`.

### 2. Adicionar um Novo Contato

Cria um novo contato no sistema.

#### Endpoint
```POST /api/contacts```

#### Requisição (Request)
- Content-Type: application/json
- Corpo (Body): Um objeto JSON representando o contato a ser criado.


#### Respostas
- 201 Created: Retornado em caso de sucesso, com corpo vazio.
- 400 Bad Request: Retornado se o corpo da requisição estiver malformado ou se faltarem campos obrigatórios.

#### Exemplo cURL
```
curl -X POST http://localhost:8080/api/contacts 
-H "Content-Type: application/json" 
-d '{ "nome": "Ana Paula", "telefone": "61977776666", "ativo": true }'
```


#### Requisição (Request)

-   **Content-Type:** `application/json`
-   **Corpo (Body):** Um objeto JSON representando o contato a ser criado.

```PUT /api/contacts/{nome}/desactive```

```DELETE /api/contacts/{nome}```