#Criando um dataset
Para desenvolver um dataset é bem simples, você utilizará o seguinte passo.

1. No projeto do Fluig clique com o botão direito, em new e em seguida Dataset Customizado.

 ![novoDTS](https://github.com/robertoShimokawa/Fluig/blob/master/Dataset/Criando%20dataset/images/01.jpg)

2. Informe um código e uma descrição, clique em finish.

3. Note que será criado uma estrutura igual a baixo.

 ```
 function defineStructure() {
 
 }
 function onSync(lastSyncDate) {
 
 }
 function createDataset(fields, constraints, sortFields) {
 
 }function onMobileSync(user) {
 
 }
 ```

4. Dentro dessa estrutura utilizaremos a função **createDataset** , não pode mudar este nome pois será executado dentro do Fluig e caso alterado ele não consiguirá criar o dataset.

5. Vamos criar o dataset, insirá o comando.
 
 ```
 function createDataset(fields, constraints, sortFields) {
    // Criando o dataset
    var nomeQueQuiser = DatasetBuilder.newDataset();
 }
 ```
 
 A variável **nomeQueQuiser** pode ser colocado qualquer nome, isso não intefere. O sugerido é **dataset** para melhor entendimento.

6. O dataset está criado, mas sem colunas ou linhas, então vamos criar uma coluna no dataset.
 
 ```
 function createDataset(fields, constraints, sortFields) {
    // Criando o dataset
    var nomeQueQuiser = DatasetBuilder.newDataset();
    
    // Criando um coluna no dataset
    nomeQueQuiser.addColumn("minhaPrimeiraColuna");
 }
 ```

 Importante, na hora de criar uma coluna você precisa chamar o local onde foi instanciado o dataset, no nosso caso na **var nomeQueQuiser** por isso fica sendo **nomeQueQuiser**.addColumn("minhaPrimeiraColuna");
 
 * **addColumn** - adiciona uma nova coluna no dataset.
 * **minhaPrimeiraColuna** - nome da coluna , pode ser o nome que quiser.
 
7. Após criar uma coluna já é possível inserir uma linha no dataset, nesta linha será armazenado um valor.

 ```
 function createDataset(fields, constraints, sortFields) {
    // Criando o dataset
    var nomeQueQuiser = DatasetBuilder.newDataset();
    
    // Criando um coluna no dataset
    nomeQueQuiser.addColumn("minhaPrimeiraColuna");
    
    // Adicionando uma linha na coluna
    nomeQueQuiser.addRow(new Array("minhaPrimeiraLinha"));
 }
 ```
 
 Importante sempre chamar o dataset que será adicionado por isso **nomeQueQuiser**
 
 * **addRow(new Array())** - adiciona os valores no dataset, caso o dataset tenha mais de 1 coluna dentro do **new Array()** você informa os valores de acordo com as posicoções,
 
 **Exemplo:**
 
 ```
 dataset.addRow(new Array(posicao1, posicao2, posicao3));
 ```

8. Agora que o dataset esta criado e com valor é preciso retornar-lo para que seja possível utilizar-lo.

 ```
 function createDataset(fields, constraints, sortFields) {
    // Criando o dataset
    var nomeQueQuiser = DatasetBuilder.newDataset();
    
    // Criando um coluna no dataset
    nomeQueQuiser.addColumn("minhaPrimeiraColuna");
    
    // Adicionando uma linha na coluna
    nomeQueQuiser.addRow(new Array("minhaPrimeiraLinha"));
    
    // Retornando dataset
    return nomeQueQuiser;
 }
 ```
 
 * **return** - devolve o dataset, sem isso não será possível utilizar os valores dele.