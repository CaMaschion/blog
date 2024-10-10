---
title: "Classe, objeto e princípios da programação orientada a objetos"
date: 2024-07-29T18:55:31+01:00
draft: false # Set 'false' to publish
---
## Classe, objeto e princípios da programação orientada a objetos

Recentemente resolvi "voltar duas casas" nos meus estudos e revisitar os conceitos fundamentais de programação orientada a objetos (POO) através da leitura do livro  "The Object-Oriented Thought Process" de Matt Weisfeld.

---

Esse é um resumo do primeiro capítulo:

### **Objeto e Classe**

Um **objeto** é uma **instância** de uma classe. 

Uma **classe** é como um **projeto** ou **molde** que define as características e comportamentos dos **objetos** que serão criados a partir dela. 

Quando criamos um objeto a partir de uma classe, estamos criando uma entidade real que possui o **estado e os comportamentos definidos pela classe.**

- **Estado** refere-se aos dados ou atributos que um objeto possui em um determinado momento. No exemplo de uma conta bancária, o estado de uma conta é seu **saldo** atual.
- **Comportamento** refere-se às ações que um objeto pode realizar. No exemplo da conta bancária por exemplo, os comportamentos são os métodos que permitem **depositar**, **sacar** e **consultar o saldo**.

![classandobject.png](/resources/_gen/images/classandobject.png)

---

### Princípios da Programação Orientada a Objetos (POO)

### 1. Encapsulamento

**Encapsulamento** significa **ocultar os detalhes internos** de um objeto, expondo apenas os métodos essenciais que outros objetos podem interagir, como por exemplo na conta bancária os métodos expostos podem ser depositar, sacar ou consultar saldo.

**Exemplo:** você pode acessar o saldo e movimentar seu dinheiro, mas você não pode simplesmente **mudar o saldo diretamente** como quiser, entrando em um sistema bancário e alterando o valor(por mais que isso fosse uma ótima ideia).

### 2. Herança

**Herança** permite que uma classe **reutilize** atributos e comportamentos de outra classe. 

A classe que herda é chamada de **subclasse**, e a classe da qual ela herda é a **superclasse**.

**Exemplo:** Podemos ter uma classe `ContaPoupanca` que herda de `ContaBancaria` e o método calcular juros será adicionado na conta poupança, ou seja, além dos comportamentos herdados da classe conta bancária como sacar, depositar e consultar, a classe “filha” terá também o comportamento de **calcular juros**.

### 3. Polimorfismo

**Polimorfismo** permite que **múltiplas classes** respondam a um mesmo método de maneira diferente. 

Isso significa que você pode usar o mesmo método em diferentes tipos de objetos, mas cada um executa sua própria versão.

**Exemplo:** Tanto `ContaCorrente` quanto `ContaPoupanca` podem ter o método `sacar()`, mas com regras diferentes, a conta poupança pode ter uma regra de limite de saque maior que a conta corrente, pode ter limite de dias para sacar, entre outras regras específicas.

### 4. **Abstração**

É a capacidade de representar objetos do mundo real em um programa, extraindo apenas as características importantes e ignorando as demais.

Como funciona a abstração no exemplo da conta bancária?

Imagine que, no mundo real, uma conta bancária tem diversas características, como:

- O número da agência e da conta.
- O nome do titular.
- Transações passadas.
- Taxas bancárias.
- Histórico de crédito.
- E muito mais...

Entretanto, quando estamos programando um sistema básico para gerenciar uma conta bancária, nem todos esses detalhes são relevantes. 

A abstração nos permite **focar apenas nos aspectos importantes para o nosso problema específico**.

Exemplo: para focarmos nos comportamentos de saque e depósito básicos, podemos abstrair histórico de transações, taxas bancárias, histórico de crédito, porque esses detalhes não são essenciais para o problema específico que é apenas sacar ou depositar.

---

Bom, aqui será como o meu "bloquinho de notas" para fixar conhecimento e quem sabe seja útil para quem tiver interesse em estudar sobre o tema também.