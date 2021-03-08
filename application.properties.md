<h2>Sobre o application.properties</h2>

`spring.datasource.initialization-mode=never` -> não lê o DB, inicia vazio.
É possível exportar as configurações do arquivo para não ficarem direto lá, através de `${}`, como por exemplo:
`spring.datasource.url=${FORUM_DATABASE_URL}`

e para passar essas variavéis, é só inserir no terminal:
`export FORUM_DATABASE_URL=jdbc:h2:mem:gams-forum`
