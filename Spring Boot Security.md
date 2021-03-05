<h3>Spring Boot Security</h3>

Para haver regras de segurança na classe é necessário inserir os profis na parte de segurança.
- Na classe "SecurityConfiguration é inserido o atributo ."hasHole("NOME")
<em>ex.: .antMatchers(HttpMethod.DELETE, "/topicos/\*")**.hasRole("MODERADOR")** </em>

<h3>Spring Boot Profiles</h3>

- Se quiser que hajam perfis distintos é necessário incluir @Profile("NOME_DO_PERFIL") nas classe a serem chamadas quando o ambiente for o "NOME_DO_PERFIL"
- Para ativar e alterar perfis no IntelliJ, seguir os seguintes passos:
 -> Edit Configurations > Run/Debug Configurations > 
 			**VM Options:** -Dspring.profiles.active="NOME_DO_PERFIL"
			**Program Arguments:** NOME_DO_PERFIL
