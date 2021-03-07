<h3>Spring Boot Security</h3>

Para haver regras de segurança na classe é necessário inserir os profis na parte de segurança.
- Na classe "SecurityConfiguration é inserido o atributo <em>."hasHole("NOME")</em>
ex.:` .antMatchers(HttpMethod.DELETE, "/topicos/\*")**.hasRole("MODERADOR")**`

<h3>Spring Boot Profiles</h3>

- Se quiser que hajam perfis distintos é necessário incluir `@Profile("NOME_DO_PERFIL")` nas classe a serem chamadas quando o ambiente for o "NOME_DO_PERFIL"
-  É possível alterar o DB usado, através do `application.properties`, colocando o nome do Profile na frente do application: `application-test.properties`.
- Para ativar e alterar perfis no IntelliJ, seguir os seguintes passos:
 	-> Edit Configurations > Run/Debug Configurations > 
 			**VM Options:** `-Dspring.profiles.active="NOME_DO_PERFIL"`
			**Program Arguments:** "NOME_DO_PERFIL"
`@ActiveProfiles("NOME)"`: inserindo este argumento em uma classe, ele força o ambiente a ser o escolhido. 
			
<h3>Spring Boot Test</h3>

Testes automatizados, utilizando JUnit.
<h4>Anotação de início da classe de teste </h4>

`@SpringBootTest` -> serve para que o Spring inicialize o servidor e carregue os beans da aplicação durante a execução dos testes automatizados -> inserir essa anotação na classe que fará o teste
`@DataJpaTest` -> Para testes classes de Repository
`@WebMvcTest` -> Para testes em classes de Controller

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

- Para usar um DB que não seja alocado na memória, inserir `@AutoConfigureTestDatabase(replace = AutoConfigureTestDatabase.Replace.NONE)`

É possível fazer o teste persistindo os dados através do Entity Manager, incluindo a injeção de dependência:

```
@Autowired  
private TestEntityManager em;

@Test
    public void shouldFindByNome() {

        String nomeCurso = "HTML 5";
        Curso html5 = new Curso();
        html5.setNome(nomeCurso);
        html5.setCategoria("Programacao");
        em.persist(nomeCurso);

        Curso curso = repository.findByNome(nomeCurso);
        Assertions.assertNotNull(curso);
        Assertions.assertEquals(nomeCurso, curso.getNome());
    }
```
