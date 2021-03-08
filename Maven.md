<h2>Maven</h2>

<h4>Deploy com War</h4>

Para definir o formato do arquivo a ser gerado:
`<packaging\>war</packaging\>`
Também é necessário inserir tomcat como provided
```
<dependency\>  
    <groupId\>org.springframework.boot</groupId\>  
    <artifactId\>spring-boot-starter-tomcat</artifactId\>  
    <scope\>provided</scope\>  
</dependency\>
```
Por fim, na classe de Start, inserir essa extensão e esse método
```
public class NOME_DA_CLASSE extends SpringBootServletInitializer {

.
.
.

@Override  
protected SpringApplicationBuilder configure(SpringApplicationBuilder builder) {  
    return builder.sources(NOME_DA_CLASSE.class);  
}
```
<h4>Criando executável</h4>

Para criar um executável do programa, executar o comando `mvn clean package` no terminal.

<h4>Start no projeto</h4>
Para rodar o arquivo ".jar", passar o seguinte comando no terminal
```

java -jar NOME_DO_ARQUIVO.jar 

```
Se tiver Profile e quiser selecionar usar: 
```

java -jar -Dspring.profiles.active="NOME_DO_PERFIL" NOME_DO_ARQUIVO.jar

```

<h4>Alterar o nome do arquivo</h4>

Para trocar o nome final da aplicação do arquivo "".jar", inserir em build o tag "finalName":
```
<build>  
    <finalName\>forum</finalName\>
</build>
```

