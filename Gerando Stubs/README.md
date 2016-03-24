# Gerando Stubs
## Configurando o wsimport
Antes de utilizar o comando **wsimport** é preciso configurar o Java.

1. Abra as variaveis de ambiente.
2. Clique em novo.
3. No nome da variavel, coloque **JAVA_HOME**
4. E no valor da variavel informe o diretorio de instalacao do Java:

    ```
    C:\Program Files\Java\jdk1.7.0_79\bin
    ```
5. Feito isso, salve e saia das variaveis de ambiente.
6. Pronto, esta configurado;

## Criando os stubs
Para gerar o paconte com os Stubs:

1. Abra o CMD
2. Execute o comando:

    ```
    wsimport -d [Diretorio Destino] http://[host]:[port]/[url.wsdl]
    ```

3. Para compactar execute o comando
    
    ```
    jar -cvf fluig-ws-client.jar ./net/* ./com/*
    ```