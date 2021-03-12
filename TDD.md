<h4>Test Driven Development</h4>

![[example-tdd.png]](https://github.com/gams99/java-doc/blob/main/img/example-tdd.png)

É recomendado fazer as classes de testes antes da classe da funcionalidade.
1. TDD são feitos usando o JUnit, para adicionar a lib do JUnit no projeto, ir em *File > Project Structure>Project Settings>select Libraries> procurar por "junit"*
2. Utilizar a anotação `@Test` na classe.
3. Na realização de testes, existem algumas opções de testes como explificadas abaixo:
		`Assert.assertEquals(VALOR_ESPERADO, VALOR_ATUAL, DIFERENCA_ACEITA*)` *opcional*
4. É uma boa prática criar métodos para classes e atributos repetitivos. 
	- Para algo, como por exemplo um método, ser chamado antes do `@Test` e **automaticamente** ao iniciar a classe de TESTE, anotar com `@Before` e o metódo ser público:
	- Usar [Test Data Builder](#ancora1)
```
@Before  
public void criaAvaliador(){  
    this.leiloeiro = new Avaliador();  
}
```

<h4>Exemplo de métodos de teste</h4>

```
@Test  
public void deveReceber2LancesSeguidoMesmoUsuario(){  
    Leilao leilao = new Leilao("Mackbook Pro 15");  
    Usuario steveJobs = new Usuario("Steve Jobs");  
    leilao.propoe(new Lance(steveJobs, 2000));  
    leilao.propoe(new Lance(steveJobs, 3000));  
  
    assertEquals(1, leilao.getLances().size());  
    assertEquals(2000.0, leilao.getLances().get(0).getValor(), 0.00001);  
}
```
- O primeiro "*assertEquals*" verifica o tamanho da lista, pra ver se é o que ele espera e o segundo, verifica o valor.

<a id="ancora1"></a>
<h4>Test Data Builder</h4>

Utilizado em métodos repetivos, como por exemplo

```
Leilao leilao = new Leilao("PS5");

leilao.propoe(new Lance(maria, 300.0));

leilao.propoe(new Lance(joao, 400.0));

leilao.propoe(new Lance(jose, 500.0))
```

Podemos substituir por um método mais elegante, como:

```
Leilao leilao = new CriadorDeLeilao().para("PS5")

.lance(joao, 100.0)

.lance(maria, 200.0)

.lance(joao, 300.0)

.constroi();
```
Repare que os códigos fazem a mesma coisa, sendo necessário criar apenas a classe `CriadorDeLeilao` com os atributos e métodos:

```
public class CriadorDeLeilao {  
  
    private Leilao leilao;  
  
    public CriadorDeLeilao para(String descricao) {  
        this.leilao = new Leilao(descricao);  
        return this;  
    }  
  
    public CriadorDeLeilao lance(Usuario usuario, double valor) {  
        leilao.propoe(new Lance(usuario, valor));  
        return this;  
    }  
  
    public Leilao constroi() {  
        return leilao;  
    }  
}
```

