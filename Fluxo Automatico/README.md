#Fluxo automatico
## Criando um fluxo automatico

Para criar um processo automatico no Fluig realize o passo a passo.

1. Iniciando automaticamente, no eclipse na aba Palette em Fluxos, clique na seta ao lado de **Inicial** e selecione **Timer**.
  * O **Timer** criará no **Agendamento de Tarefaz** do Fluig uma rotina com os parametros selecionados na edição.
  
  ![localizandoTimer](https://github.com/robertoShimokawa/Fluig/blob/master/Fluxo%20Automatico/images/localizandoTimer_01.JPG)

2. Arraste o **Timer** para o processo e configure os parametros na guia **Geral**.
  * **Nome** - Será o nome do **Timer**.
  * **Repetição** - O intervalo que acontecerá o evento, ao configurar esta parte ele incluirá esses parametros no **Agendador de Tarfas** do Fluig.
  * **Inicializador** - É obrigatório selecionar um inicializador, senão aparecerá um erro.
  
  ![confTimer](https://github.com/robertoShimokawa/Fluig/blob/master/Fluxo%20Automatico/images/confTimer_02.JPG)

3. Feito isso criarei duas tarefas simples , uma sendo automatica e a outra executada por um usuário. Conforme imagem abaixo.
  
  ![fluxoAuto](https://github.com/robertoShimokawa/Fluig/blob/master/Fluxo%20Automatico/images/fluxoAuto_03.JPG)

4. Agora para que a tarefa **automatico** execute sozinha é necessário informar nas configurações do processo que ela é automatica.
  1. Para isso clique no campo vazio fora do fluxo.
  2. Na guia **Properties** do Eclipse, clique em Extensões.
  3. Clique em **Adicionar novo Atributo**
    * **Nome(ID)** - Informe o Atributo que no nosso caso será: **AutomaticTasks**.
    * **Label** - Informe o titulo que aparecerá na extensão
    * **Tipo** - Selecione o tipo **Campo** , onde informaremos o ID da Atividade.
  
  ![novoAtribulto](https://github.com/robertoShimokawa/Fluig/blob/master/Fluxo%20Automatico/images/nvAtrConf_04.JPG)

5. Aparecerá igual a imagem a baixo.
  
  ![novoAtrFica](https://github.com/robertoShimokawa/Fluig/blob/master/Fluxo%20Automatico/images/nvAtrFica_05.JPG)

6. Feito isso, substitua o valor **campo** pelo **ID** da Atividade, no meu caso o ID é igual a **38**.
  * Para localizar o ID da Atividade , clique na atividade e na guia **Properties** na aba **Geral**, localize o campo **Código**.
  
  ![localizandoId](https://github.com/robertoShimokawa/Fluig/blob/master/Fluxo%20Automatico/images/localizandoIdTask_06.JPG)