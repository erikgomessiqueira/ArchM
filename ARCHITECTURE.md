# Arquitetura -  ArchM
**Objetivo**: Proposta de arquitetura modular simples para aplicações diversas. Ela é baseada em três camadas como base Domain, Adapter e External.

## Camadas
- **User Interator**: Deve ser responsável por lidar com a aplicação e suas regras.

- **Adapter**: Deve ser responsável pelo tratamento, e adapção dos dados entre a camada de User Interator e a camada External.

- **External**: Deve ser responsável por receber e lidar com informações externas a aplicação.

### Limites
 É importante destacar que _**A camada User Interator não deve ser acessada diretamente pela camada de External**_, para isso utilizamos a camada de Adapter e prover essa comunicação. O objetivo disso é maior flexibilidade e eficiência no desenvolvimento devido ao baixo acoplamento e separação de responsabilidades.
 <br>
 <br>

# Estrutura da arquitetura
O nomes do arquivos devem possuir o sufixo de sua camada.
## Core
Deve conter informações globais e reutilizáveis ​​para todas as camadas da aplicação.

## Interator 
Esta camada deve lidar com a gerência de estados, a representação de regras de negócios, abstrações para comunicação com outras camadas e as interações na interface do usuário.

- #### Models: 
    Deve conter os a regra de negócio.

- #### Ropository: 
    Interface para o repositório de acesso a dados externos.

- #### DTO: 
    DTO(Data Transfer Object) é um padrão de design de transferência de dados no lugar de parâmetros.

- #### Helpers: 
   Classes de auxílio para determinadas rotinas.

- #### Presenter: 
    Deve conter a parte visula da aplicação e suas interações.

    - #### State: 
        Deve conter o estados realacioandos a interação com as telas da aplicação.
    
    - #### Widget: 
        Deve conter os componentes que compõe as telas.

    - #### View: 
        Deve conter as telas relacionada a aplicação.

<br>

## Infra
Esta camada deve ter os elementos relacionados a aplicação.

- #### Ropository: 
    Implementação para o repositório de acesso a dados externos. Deve conter um tratamento para erros.

- #### Service: 
    Realiza alguma ação interna necessária retronado o dado ao repository. Deve possuir interface e implementação.

- #### Adapters: 
   Realiza a adaptação entre os dados do aplicativo e dados externos.


## Exemplo
De acordo com o a proposta de arquitetura, a estuturação de pastas foi definida da seguinte maneira.

```text
.
└── lib/
    ├── core/
    │   └── ...
    ├── interactors/
    │   ├── models
    │   ├── repositories
    │   ├── dto
    │   ├── helpers
    │   └── presenters/
    │       ├── states
    │       ├── widgets
    │       └── views
    └── infra/
        ├── repositories
        ├── services
        └── adapters
```

