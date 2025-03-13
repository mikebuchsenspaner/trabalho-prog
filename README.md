# Instruções
- Faça uma cópia deste arquivo .md para um repositório próprio
- Resolva as 8 questões objetivas assinalando a alternativa correta e **justificando sua resposta.**
- Resolva as 2 questões dissertativas escrevendo no próprio arquivo .md
- Lembre-se de utilizar as estruturas de código como ``esta aqui com ` `` ou
```javascript
//esta aqui com ```
let a = "olá"
let b = 10
print(a)
```
- Resolva as questões com uso do Visual Studio Code ou ambiente similar.
- Teste seus códigos antes de trazer a resposta para cá.
- Cuidado com o uso de ChatGPT (e similares), pois entregar algo só para ganhar nota não fará você aprender. Não seja dependente da máquina!
- Ao final, publique seu arquivo lista_01.md com as respostas em seu repositório, e envie o link pela Adalove. 

## Questões Objetivas

### 1) Saída do código
```js
console.log(x);
var x = 5;
console.log(y);
let y = 10;
```
**Resposta:**
**Alternativa A) A saída será indefinida seguida de erro**

**Justificativa:**
O JavaScript tem um comportamento chamado *hoisting*, onde ele "move" a declaração das variáveis para o topo do escopo. No caso de `var x`, a variável é declarada, mas sem um valor inicial, então `console.log(x);` imprime `undefined`. Já a variável `let y` não permite ser acessada antes da declaração, então causa um erro.

---
### 2) Correção do código
```js
function soma(a, b) {
    if (a || b === 0) {
        return "Erro: número inválido";
    }
    return a + b;
}
console.log(soma(2, 0));
```
**Resposta:**
**Alternativa A) Substituir `if (a || b === 0)` por `if (a === 0 || b === 0)`**

**Justificativa:**
O código original tem um erro na condição do `if`. A forma escrita `a || b === 0` faz com que `b === 0` seja avaliado corretamente, mas `a` por si só já pode ser um valor *truthy* e acabar retornando `true` indevidamente. A correção garante que o `if` só seja verdadeiro se `a` ou `b` forem exatamente `0`.

---
### 3) Saída do código
```js
function calcularPreco(tipo) {
    let preco;

    switch(tipo) {
        case "eletrônico":
            preco = 1000;
        case "vestuário":
            preco = 200;
            break;
        case "alimento":
            preco = 50;
            break;
        default:
            preco = 0;
    }

    return preco;
}

console.log(calcularPreco("eletrônico"));
```
**Resposta:**
**Alternativa B) O código imprime 200.**

**Justificativa:**
No `switch`, falta um `break` depois do `case "eletrônico"`. Isso faz com que, ao cair no primeiro caso, o código continue executando até `case "vestuário"`, sobrescrevendo o valor para `200`. 

---
### 4) Saída do código
```js
let numeros = [1, 2, 3, 4, 5];

let resultado = numeros.map(x => x * 2).filter(x => x > 5).reduce((a, b) => a + b, 0);

console.log(resultado);
```
**Resposta:**
**Alternativa C) 18**

**Justificativa:**
1. Multiplicamos cada número por 2: `[2, 4, 6, 8, 10]`.
2. Filtramos apenas os maiores que 5: `[6, 8, 10]`.
3. Somamos todos os valores: `6 + 8 + 10 = 18`.

---
### 5) Saída do código
```js
let lista = ["banana", "maçã", "uva", "laranja"];
lista.splice(1, 2, "abacaxi", "manga");
console.log(lista);
```
**Resposta:**
**Alternativa C) ["banana", "abacaxi", "manga", "laranja"]**

**Justificativa:**
O `splice(1, 2, "abacaxi", "manga")` remove dois elementos a partir da posição 1 (`maçã` e `uva`) e coloca `abacaxi` e `manga` no lugar.

---
### 6) Herança em JavaScript
**Resposta:**
**Alternativa A) As duas afirmações são verdadeiras, e a segunda justifica a primeira.**

**Justificativa:**
A herança em JavaScript é usada para reutilizar código, permitindo que uma classe filha aproveite os métodos da classe pai sem precisar reescrevê-los. A palavra-chave `extends` é o que permite essa funcionalidade.

---
### 7) Código com classes
**Resposta:**
**Alternativa A) I e II são verdadeiras.**

**Justificativa:**
A classe `Funcionario` herda `Pessoa`, então consegue acessar os atributos `nome` e `idade`. Além disso, o método `apresentar()` da classe `Funcionario` substitui o método original da classe `Pessoa`, mas ainda pode chamá-lo com `super.apresentar()`.

---
### 8) Polimorfismo
**Resposta:**
**Alternativa B) A afirmação é verdadeira e a razão é falsa.**

**Justificativa:**
O polimorfismo realmente permite que métodos sejam redefinidos nas subclasses. No entanto, JavaScript não tem suporte a sobrecarga de métodos como em outras linguagens, então a justificativa está incorreta.

---

## Questões Dissertativas

### 1) Correção do código
```js
function somaArray(numeros) {
    let soma = 0; // Inicializar soma corretamente

    for (let i = 0; i < numeros.length; i++) { // Corrigir size para length
        soma += 2 * numeros[i]; // Somar em vez de apenas atribuir
    }
    return soma;
}
console.log(somaArray([1, 2, 3, 4]));
```
**Explicação:**
1. A variável `soma` precisa ser inicializada antes do loop.
2. `numeros.size` não existe em JavaScript, o correto é `numeros.length`.
3. `soma = 2 * numeros[i];` sobrescrevia o valor ao invés de acumulá-lo, o que fazia o código funcionar incorretamente.

---
### 2) Implementação de herança
```js
class Produto {
    constructor(nome, preco) {
        this.nome = nome;
        this.preco = preco;
    }

    calcularDesconto() {
        return this.preco * 0.9; // 10% de desconto
    }
}

class Livro extends Produto {
    calcularDesconto() {
        return this.preco * 0.8; // 20% de desconto para livros
    }
}

let produto = new Produto("Genérico", 100);
console.log(produto.calcularDesconto()); // 90

let livro = new Livro("JavaScript", 100);
console.log(livro.calcularDesconto()); // 80
```
**Explicação:**
1. Criamos a classe `Produto` com um método `calcularDesconto()` que reduz o preço em 10%.
2. A classe `Livro` herda de `Produto`, mas redefine `calcularDesconto()` para aplicar um desconto maior (20%).
3. Quando chamamos `calcularDesconto()` em uma instância de `Livro`, a versão sobrescrita do método é usada.

