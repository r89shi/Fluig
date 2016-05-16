![logoFluig](https://github.com/robertoShimokawa/Fluig/blob/master/images/fluig-logo.png)

Repositorio contendo assuntos pertinentes ao Fluig, com exemplos , codigos e tutoriais.

# Acessando os Servicos e API do Fluig
## Servico
Para acessar os servicos do Fluig, informe na URL do navegador o seguinte endereco:
```
http://[host]:[port]/services
```

## API
Para acessar as API do Fluig, Informe na URL do navegador o seguinte endereco:
```
http://[host]:[port]/api/doc
```

 Porta travada durante a instalação
## Processos para destravar

Para destravar possíveis portas travadas durante a instalação realize o processo abaixo:
1. Finalize todos os processo do Fluig e do prizm, são eles: FLUIG_MEMChace, FLUIG_RealTime, FLUIG, Prizm e PrizmDemo.

2. Verifique se as portas não estão travadas, para isso execute o comando no cmd:
  ```
  netstat -a
  ```

3. Caso exista alguma porta travada, como por exemplo:
  ```
  TCP    [::]:10000             [::]:0                 LISTENING
  ```

4. Será necessário finalizar o prcesso que esta ocupando esta porta, para isso execute o seguinte comando no cmd:
  ```
  netstat -ano
  ```

5. Agora coleta o PID do processo:
  ```
  Proto  Local Address          Foreign Address        State           PID
  TCP    [::]:10000             [::]:0                 LISTENING       2172
  ```

6. Abra o gerenciador de tarefas, procure o PID do processo e finalize-o.

7. Caso este processo não funcione, tente apagar a pasta **[diretorio_onde_o_fluig_esta_instalado] / jboss / standalono / tmp**
