<h4>Test Driven Development</h4>

![[example-tdd.png]](https://github.com/gams99/java-doc/blob/main/img/example-tdd.png)

É recomendado fazer as classes de testes antes da classe da funcionalidade.
1. TDD são feitos usando o JUnit, para adicionar a lib do JUnit no projeto, ir em *File > Project Structure>Project Settings>select Libraries> procurar por "junit"*
2. Utilizar a anotação `@Test` na classe.
3. Na realização de testes, existem algumas opções de testes como explificadas abaixo:
		`Assert.assertEquals(VALOR_ESPERADO, VALOR_ATUAL, DIFERENCA_ACEITA*)` *opcional*
		
<h4>Exemplo de métodos de teste</h4>

```
@Test  
public void deveReceber2LancesSeguidosDoMesmoUsuario(){  
    Leilao leilao = new Leilao("Mackbook Pro 15");  
    Usuario steveJobs = new Usuario("Steve Jobs");  
    leilao.propoe(new Lance(steveJobs, 2000));  
    leilao.propoe(new Lance(steveJobs, 3000));  
  
    assertEquals(1, leilao.getLances().size());  
    assertEquals(2000.0, leilao.getLances().get(0).getValor(), 0.00001);  
}
```
- O primeiro "*assertEquals*" verifica o tamanho da lista, pra ver se é o que ele espera e o segundo, verifica o valor.