
Se os arquivos ficam guardados no cache do seu navegador ou no proxy do provedor, surge um grande problema: **Como o cache garante que a cópia que ele possui não está desatualizada?** (Por exemplo, uma notícia que foi alterada no portal).

Para resolver isso, o HTTP utiliza um mecanismo brilhante chamado **GET Condicional**.

Ele funciona através de cabeçalhos (_headers_) HTTP que controlam a validade do arquivo:

### O fluxo do GET Condicional:

1. Da primeira vez que você baixa um arquivo, o servidor de origem o envia e inclui um cabeçalho dizendo quando o arquivo foi modificado pela última vez: `Last-Modified: Wednesday, July 08, 2026 10:00:00 AM`

2. O cache guarda essa data junto com o arquivo.

3. Passado algum tempo, o cache precisa verificar se o arquivo ainda é válido. Ele envia uma requisição para o servidor de origem contendo a linha: `If-Modified-Since: Wednesday, July 08, 2026 10:00:00 AM`

4. **Cenário A (Não mudou):** Se o arquivo não sofreu nenhuma alteração desde aquela data, o servidor de origem responde com um código **`304 Not Modified`** (Sem modificações) e **não envia o corpo do arquivo novamente**. Isso economiza muita banda!

5. **Cenário B (Mudou):** Se o arquivo foi atualizado, o servidor responde com um código **`200 OK`** e envia a nova versão do arquivo.