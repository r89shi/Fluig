# Bloqueio de campos no displayFields.js

Durante um processo para bloquear determinado campo para uma certa atividade, podemos realizar o passo abaixo:

## Apos criar um formulário vamos criar um script de evento de formulários.

1. Clique com o botão direito na pasta form. Selecione new (novo) > Script Fluig:
  ![localizandoTimer](https://github.com/robertoShimokawa/Fluig/blob/master/Validacoes/Bloqueio%20de%20campos/images/01.png)

2. Selecione a opção **Script Evento da Definção de Formulários**.
  ![localizandoTimer](https://github.com/robertoShimokawa/Fluig/blob/master/Validacoes/Bloqueio%20de%20campos/images/02.PNG)

3. Selecione nas caixas de opções.
  1. **Nome do Evento** > **displayFields**
  2. **Relacionar à Formulário** > **nome_do_formulario**
  ![localizandoTimer](https://github.com/robertoShimokawa/Fluig/blob/master/Validacoes/Bloqueio%20de%20campos/images/03.PNG)

4. Note que aparecerá um script com o código abaixo:
  ```
  function displayFields(form,customHTML)
  {

  }
  ```
5. Uma pequena observação nos parametros desse metodo:
  1. **form** - recebe os dados do formulario.
  2. **customHTML** - permite adicioanar custom tags de html , muito util para inserirmos códigos JQuery no nosso script que não é permitido sem esse parametro.

6. Agora para conseguirmos bloquear um determinado campo vamos adicionar no **customHTML** as tags para chamada do JQuery.
  ```
  function displayFields(form,customHTML)
  {
    customHTML.append("<script type='text/javascript'>");
	  customHTML.append("$(document).ready(function(){");


    // Vamos trabalhar aqui dentro


    customHTML.append("});");
	  customHTML.append("</script>");
  }
  ```

7. Feito isso precisaremos coletar qual atividade que estamos e qual gostariamos que um determinado campo fosse bloqueado. Para coletar a atividade utilizaremos o um metodo do sistema **getValue('WKNumState')** que coleta o numero da atividade atual.
  ```
  function displayFields(form,customHTML)
  {
    customHTML.append("<script type='text/javascript'>");
    customHTML.append("$(document).ready(function(){");


    // Coleta a atividade que estamos
    var atividade_atual = getValue('WKNumState');


    customHTML.append("});");
    customHTML.append("</script>");
  }
  ```

8. Vamos determinar uma atividade no fluxo que gostariamos de bloquear , supondo que fosse a atividade **5**.
  ```
  function displayFields(form,customHTML)
  {
    customHTML.append("<script type='text/javascript'>");
    customHTML.append("$(document).ready(function(){");


    // Coleta a atividade que estamos
    var atividade_atual = getValue('WKNumState');

    // Atividades que queros bloquear
    var bloquear_comercial = 5;

    customHTML.append("});");
    customHTML.append("</script>");
  }
  ```

9. Compararemos a atividade atual com a que gostarimos de bloquear.
  ```
  function displayFields(form,customHTML)
  {
    customHTML.append("<script type='text/javascript'>");
    customHTML.append("$(document).ready(function(){");


    // Coleta a atividade que estamos
    var atividade_atual = getValue('WKNumState');

    // Atividades que queros bloquear
    var bloquear_comercial = 5;

    // Comparando Atividades
    if (atividade_atual == bloquear_comercial)
    {
      // Para verdadeiro
    }

    customHTML.append("});");
    customHTML.append("</script>");
  }
  ```

10. Agora podemos determinar um campo ou um array com campos.
  ```
  function displayFields(form,customHTML)
  {
    customHTML.append("<script type='text/javascript'>");
    customHTML.append("$(document).ready(function(){");


    // Coleta a atividade que estamos
    var atividade_atual = getValue('WKNumState');

    // Atividades que queros bloquear
    var bloquear_comercial = 5;

    // Comparando Atividades
    if (atividade_atual == bloquear_comercial)
    {
      // Para verdadeiro

      // Campos no formato input text que serao bloqueados
      var campos_text = ["nome","sobre_nome"];

      // Campos no formato select que serao bloqueados
      var campos_select = ["sexo","logradouro"];
    }

    customHTML.append("});");
    customHTML.append("</script>");
  }
  ```

11. Agora realizaremos um loop para bloquear esses campos.
  ```
  function displayFields(form,customHTML)
  {
    customHTML.append("<script type='text/javascript'>");
    customHTML.append("$(document).ready(function(){");


    // Coleta a atividade que estamos
    var atividade_atual = getValue('WKNumState');

    // Atividades que queros bloquear
    var bloquear_comercial = 5;

    // Comparando Atividades
    if (atividade_atual == bloquear_comercial)
    {
      // Para verdadeiro

      // Campos no formato input text que serao bloqueados
      var campos_text = ["nome","sobre_nome"];

      // Campos no formato select que serao bloqueados
      var campos_select = ["sexo","logradouro"];

      // Loop para bloquear os campos text
      for (var a = 0; a < campos_text.length; a++)
        customHTML.append(" $( '#"+campos_text[a]+"' ).attr('readonly', true); ");

      // Loop para bloquear os campos select
      for (var a = 0; a < campos_select.length; a++)
      {
        customHTML.append(" $( '#"+campos_select[a]+"' ).attr('readonly', true); ");
        customHTML.append(" var options = $( '#"+campos_select[a]+"' ).children('option:not(:selected)'); ");
        customHTML.append(" options.prop('disabled', true); ");
      }
    }

    customHTML.append("});");
    customHTML.append("</script>");
  }
  ```

12. Pronto o bloqueio esta feito
