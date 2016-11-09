# Validando se existe um arquivo anexa do no formulario

Uma validação bem simples para ver se o formulário em uma determinada atividade
possui um arquivo anexado.

Esse evendo é um script de formulario.

1. Clique com o botão direito do mouse na pasta de diagrama.
2. Selecione a opção :
3. Dentro desse evento faremos o seguinte passo:

  Primeiro precisamos saber qual a atividade em que estamos e para isso
  utilizaremos o comando : ** getValue("WKNumState"); **

  ```
  function beforeTaskSave(colleagueId,nextSequenceId,userList)
  {
    // Coleta a atividade atual
    var atividade_atual = getValue("WKNumState");
  }
  ```
4. Vamos definir agora uma mensagem de alerta caso o usuário esqueça de inserir o anexo.
  Criaremos uma constante: ** var ATTACHMENT_ERROR_MESSAGE = ""; **

    ```
    function beforeTaskSave(colleagueId,nextSequenceId,userList)
    {
      // Coleta a atividade atual
      var atividade_atual = getValue("WKNumState");

      // Mensagem de erro caso o usuario esqueca de inserir o anexo
      var ATTACHMENT_ERROR_MESSAGE = "Por favor insira um arquivo no anexo.";
    }
    ```
5. Feito isso compararemos o estado da atividade para que caso seja a atividade em encontrasse o processo ele alertar o usuário.
  ```
  function beforeTaskSave(colleagueId,nextSequenceId,userList)
  {
    // Coleta a atividade atual
    var atividade_atual = getValue("WKNumState");

    // Mensagem de erro caso o usuario esqueca de inserir o anexo
    var ATTACHMENT_ERROR_MESSAGE = "Por favor insira um arquivo no anexo.";

    // Valida se a atividade atual é igual a que gostarios de forçar o usuario a inserir um anexo
    if (atividade_atual == 9)
    {

    }
  ```
6. Agora coletaremos os dados do anexo utilizando o comando ** hAPI.listAttachments(); **
  ```
  function beforeTaskSave(colleagueId,nextSequenceId,userList)
  {
    // Coleta a atividade atual
    var atividade_atual = getValue("WKNumState");

    // Mensagem de erro caso o usuario esqueca de inserir o anexo
    var ATTACHMENT_ERROR_MESSAGE = "Por favor insira um arquivo no anexo.";

    // Valida se a atividade atual é igual a que gostarios de forçar o usuario a inserir um anexo
    if (atividade_atual == 9)
    {
      // Coleta os anexos
      var docs = hAPI.listAttachments();
    }
  ```
7. O proximo passo é realizar uma validação para ver se existe algum elemento na lista de anexos, para isso utilizaremos o metodo: ** size() **
  ```
  function beforeTaskSave(colleagueId,nextSequenceId,userList)
  {
    // Coleta a atividade atual
    var atividade_atual = getValue("WKNumState");

    // Mensagem de erro caso o usuario esqueca de inserir o anexo
    var ATTACHMENT_ERROR_MESSAGE = "Por favor insira um arquivo no anexo.";

    // Valida se a atividade atual é igual a que gostarios de forçar o usuario a inserir um anexo
    if (atividade_atual == 9)
    {
      // Coleta os anexos
      var docs = hAPI.listAttachments();

      // Verifica se existe anexo na listAttachments
      if(docs.size()== 0)
      {
        // Caso nao exista anexos
      }
    }
  ```
8. Agora dentro do ** if(docs.size()== 0) ** forçaremos uma mensagem que não permite o usuario avançar sem inserir um anexo.
  ```
  function beforeTaskSave(colleagueId,nextSequenceId,userList)
  {
    // Coleta a atividade atual
    var atividade_atual = getValue("WKNumState");

    // Mensagem de erro caso o usuario esqueca de inserir o anexo
    var ATTACHMENT_ERROR_MESSAGE = "Por favor insira um arquivo no anexo.";

    // Valida se a atividade atual é igual a que gostarios de forçar o usuario a inserir um anexo
    if (atividade_atual == 9)
    {
      // Coleta os anexos
      var docs = hAPI.listAttachments();

      // Verifica se existe anexo na listAttachments
      if(docs.size()== 0)
      {
        // Caso nao exista anexos
        // Dentro do metodo throw informaremos nossa contante com a mensagem de erro
        throw ATTACHMENT_ERROR_MESSAGE;
      }
    }
  ```
9. Pronto a validação esta feita para a atividade 9.
