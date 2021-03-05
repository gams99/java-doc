<h3>Spring Boot Security</h3>

Para haver regras de segurança na classe é necessário inserir os profis na parte de segurança.
- Na classe "SecurityConfiguration é inserido o atributo <em>."hasHole("NOME")</em>
ex.:` .antMatchers(HttpMethod.DELETE, "/topicos/\*")**.hasRole("MODERADOR")**`

<h3>Spring Boot Profiles</h3>

- Se quiser que hajam perfis distintos é necessário incluir `@Profile("NOME_DO_PERFIL")` nas classe a serem chamadas quando o ambiente for o "NOME_DO_PERFIL"
- Para ativar e alterar perfis no IntelliJ, seguir os seguintes passos:
 -> Edit Configurations > Run/Debug Configurations > 
 			**VM Options:** `-Dspring.profiles.active="NOME_DO_PERFIL"`
			**Program Arguments:** NOME_DO_PERFIL
		
<h3>Spring Boot Test</h3>

Testes automatizados, utilizando JUnit.
<h6>Anotação de início da classe de teste </h6>

`@SpringBootTest` -> serve para que o Spring inicialize o servidor e carregue os beans da aplicação durante a execução dos testes automatizados -> inserir essa anotação na classe que fará o teste
`DataJpaTest` -> Para classes de Repository

Inserir `@Test` em cada teste, abaixo, exemplo de código:

```
@Test  
public void shouldFindByNome() {  
    String nomeCurso = "HTML 5";  
    Curso curso = repository.findByNome(nomeCurso);  
    Assertions.assertNotNull(curso);  
    Assertions.assertEquals(nomeCurso, curso.getNome());  
}
```

Retorna sucesso, pois a variável nomeCurso existe no DB usado:

![[result-test.png]](https://github.com/gams99/java-doc/blob/main/img/result-test.png)