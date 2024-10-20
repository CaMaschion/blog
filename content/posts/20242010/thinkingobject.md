---
title: "Como pensar em termos de objetos"
date: 2024-07-29T18:55:31+01:00
draft: false # Set 'false' to publish
---

O objetivo final do design de orientação a objetos é construir um modelo de objetos robusto e funcional que represente todo o sistema. 
Antes de pensar em uma linguagem de programação é importante **focar na resolução dos problemas do negócio.**
Existem aspectos principais que ajudam a desenvolver uma boa mentalidade em relação ao design de orientação a objetos que são:


### 1. Diferença entre Interface e Implementação

- **Interface:** são os serviços e funcionalidades que a classe oferece ao usuário. Ou seja, tudo o que o usuário precisa acessar e saber para usar a classe.
- **Implementação:** são os detalhes internos da classe, que ficam escondidos do usuário. A ideia é que mudanças na implementação não devem exigir alterações no código do usuário.

---

### 2. Fornecendo a Interface Mínima Necessária

O objetivo ao projetar uma classe é mostrar apenas o que é necessário para o usuário. Isso mantém a classe mais segura e fácil de usar.

É importante que os desenvolvedores **desenvolvam as classes a partir da perspectiva do usuário final**, em vez de focar apenas nas necessidades técnicas do sistema. 

Muitos desenvolvedores de software acabam adaptando as classes para se ajustarem a modelos específicos, o que nem sempre é o mais adequado para atender as reais necessidades dos usuários.

-----

### 3. Identificação de Usuários e Comportamento de Objetos

Depois de identificar quem são os usuários do sistema, é necessário definir os comportamentos dos objetos que serão usados por eles. Essas decisões iniciais são baseadas em **requisitos**, que podem ser levantados através de métodos como **Casos de Uso UML**.

Além disso, é importante considerar **restrições ambientais**, que podem afetar o comportamento dos objetos. Por exemplo, limitações de hardware ou de conexão à rede podem restringir as funcionalidades do software.

------

### 4. Identificando Interfaces Públicas

Com as informações sobre os usuários, os comportamentos dos objetos e as restrições do ambiente, é possível definir as **interfaces públicas** de cada objeto. 

Cada interface deve ser avaliada: se ela não contribui para o funcionamento do objeto, talvez não seja necessária. 

Muitos especialistas recomendam que cada interface modele apenas um comportamento específico, o que nos leva à importância de pensar de forma mais **abstrata** no design.

------

### 5. Identificando a Implementação

Após definir as interfaces públicas, é hora de identificar a implementação da classe. Isso inclui projetar os métodos necessários para fazer a classe funcionar corretamente. Qualquer coisa que não seja interface pública faz parte da implementação interna.

---

### Exemplo prático:

Programa: carrinho de brinquedo.

    inteiro nivelBateria = 100
    
    funcao cadeia moverFrente() {
        nivelBateria = nivelBateria - 10  
        retorne "O carro se move para frente! Nível de bateria: " + nivelBateria + "%"
    }

    funcao cadeia virarEsquerda() {
        nivelBateria = nivelBateria - 5 
        retorne "O carro vira à esquerda! Nível de bateria: " + nivelBateria + "%"
    }
    
    funcao inicio() {
        escreva(moverFrente())   
        escreva(virarEsquerda()) 
    }

### Explicação: 

No desenvolvimento do carrinho de brinquedo, seguimos uma abordagem orientada a objetos que separa a interface da implementação. As funções `moverFrente()` e `virarEsquerda()` formam a interface, permitindo que o usuário controle o carrinho sem conhecer os detalhes de como o nível de bateria é gerido internamente, o que faz parte da **implementação** (oculta do usuário). A interface foi projetada para ser mínima, oferecendo apenas os métodos essenciais para o controle básico do carrinho.

O usuário identificado é alguém que controla o carrinho, e os comportamentos do objeto incluem mover-se para frente e virar à esquerda, ações diretamente acessíveis pelas **interfaces públicas**. A implementação interna, como a lógica que reduz a bateria, pode ser alterada sem afetar a forma como o usuário interage com o carrinho.

![Diagrama](/images/diagrama2.png)
