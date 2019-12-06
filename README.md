# Curso rest da Alura (JAX-RS)

### Objetivo
- Comunicação entre aplicações diferentes na Internet.
- Cada recurso tem uma URI específica.
- Formatos de arquivo transmitidos do servidor para o cliente (media types): XML, JSON, YALM.
- Bibliotecas JAX B, XStream.

### Teste de requisições
- curl faz requisições HTTP na linha de comando.
- `curl -v http://localhost:8080/carrinhos/1`
  - Request GET que retorna resposta (no exemplo da aula 5, em XML).
  - `-v` indica verbose, ou seja, mostra informações do request e do response.
  - No request é enviado cabeçalhos. 
      - GET é obrigatório
      - Host é obrigatório
      - Quem envia (ex: User-agent: curl) e o que aceita como resposta (Accept: `*/*`) são opcionais.
   - No response é enviado cabeçalhos.
      - `HTTP/1.1 200 OK` indica status.
      - `Content-Type: application/xml`
      - `Date: <data da resposta>`
      - `Content-Length: <tamanho da resposta>` 
      - Resposta (Ex: xml)

- `curl -d "<xml de teste>" http://localhost:8080/carrinhos`
  - Request POST que retorna resposta (no exemplo da aula 5, em String).
  - Quando retorno de create (método adicionar) é Response, é retornado status 201 e o cabeçalho `Location` com a URL do recurso criado.
  
- `curl -v -X "DELETE" http://localhost:8080/carrinhos/1/produtos/3060`
    - Deleta produto com id = 3060 do carrinho com id = 1.
    
- `curl -v -X "PUT" -d "<xml>" http://localhost:8080/carrinhos/1/produtos/3060`
    - Altera produto com id = 3060 pelo produto passado como XML.
    
  
### Verbos HTTP
- `GET`: idempotente, ou seja, pode ser chamado várias vezes (tolerante a falhas). Não altera nada no servidor.
- `POST`: cria novo recurso. Não é idempotente, ou seja, se chamar de novo pode criar recurso que já existe.
  
### Status
- `200` OK
- `400` Erro no lado cliente
- `404` Not Found
- `415` Unsupported Media Type
- `500` Erro no servidor


