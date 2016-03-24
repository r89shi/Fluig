#Fluxo automatico
## Criando um fluxo automatico

Para criar um processo automatico no Fluig realize o passo a passo.

1. Iniciando automaticamente, no eclipse na aba Palette em Fluxos, clique na seta ao lado de **Inicial** e selecione **Timer**.
1.1. O **Timer** criará no **Agendamento de Tarefaz** do Fluig uma rotina com os parametros selecionados na edição.

[[https://github.com/robertoShimokawa/Fluig/tree/master/Fluxo%20Automatico/images/localizandoTimer_01.jpg]]

2. Arraste o **Timer** para o processo e configure os parametros na guia **Geral**.
* **Nome** - Será o nome do **Timer**.
* **Repetição** - O intervalo que acontecerá o evento, ao configurar esta parte ele incluirá esses parametros no **Agendador de Tarfas** do Fluig.
* **Inicializador** - É obrigatório selecionar um inicializador, senão aparecerá um erro.

[[https://github.com/robertoShimokawa/Fluig/tree/master/Fluxo%20Automatico/images/confTimer_02.jpg]]

3. Feito isso criarei duas tarefas simples , uma sendo automatica e a outra executada por um usuário. Conforme imagem abaixo.

[[https://github.com/robertoShimokawa/Fluig/tree/master/Fluxo%20Automatico/images/fluxoAuto_03.jpg]]

4. Agora para que a tarefa **automatico** execute sozinha é necessário informar nas configurações do processo que ela é automatica.
4.1. Para isso clique no campo vazio fora do fluxo.
4.2. Na guia **Properties** do Eclipse, clique em Extensões.
4.3. Clique em **Adicionar novo Atributo**
* **Nome(ID)** - Informe o Atributo que no nosso caso será: **AutomaticTasks**.
* **Label** - Informe o titulo que aparecerá na extensão
* **Tipo** - Selecione o tipo **Campo** , onde informaremos o ID da Atividade.