<h2>Maven</h2>

Para criar um executável do programa, executar o comando `mvn clean package` no terminal.

Para trocar o nome final da aplicação do arquivo "".jar", inserir em build o tag "finalName":
```
<build>  
    <finalName\>forum</finalName\>
</build>
```

Para rodar o arquivo ".jar", passar o seguinte comando no terminal
```

java -jar NOME_DO_ARQUIVO.jar 

```
Se tiver Profile e quiser selecionar usar: 
```

java -jar -Dspring.profiles.active="NOME_DO_PERFIL" NOME_DO_ARQUIVO.jar

```
