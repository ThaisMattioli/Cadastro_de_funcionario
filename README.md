# Cadastro_de_funcionário

Estácio 2025.01
Trabalho Sobre Estrutura De Dados (ARA0098)
Professo: Marcelo Peratoni
Turma: 1001

Grupo:
- Lucas Vianna Carvalho - 202403689571
- Rodrigo Vasconcelos Oliveira Junior - 202403890615
- Matheus Rodrigues Soares Nunes - 202403680701
- Elise Malvão Carlson - 202403679922
- Thais de Souza Mattioli - 202202975991

**Relatório Técnico - Sistema de Cadastro e Gerenciamento de Funcionários em Linguagem C**

---

### 1. Introdução

Este relatório apresenta a análise detalhada de um sistema desenvolvido em linguagem C para o cadastro, listagem, cálculo de salário com horas extras e exclusão de funcionários. O sistema utiliza alocação dinâmica de memória para gerenciar uma lista flexível de funcionários e é controlado por um menu interativo em terminal.

---

### 2. Objetivos

* Permitir o cadastro de funcionários com dados pessoais e salariais;
* Calcular salários incluindo horas extras mensais;
* Listar todos os funcionários cadastrados;
* Excluir funcionários do sistema;
* Gerenciar a memória de forma eficiente e segura com alocação dinâmica.

---

### 3. Estrutura do Código

#### 3.1 Bibliotecas Utilizadas

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
```

* **stdio.h**: Entrada e saída padrão.
* **stdlib.h**: Alocação dinâmica, controle de execução.
* **string.h**: Manipulação de strings.

#### 3.2 Definição de Constantes

```c
#define LIMITE_FUNCIONARIOS 100
#define TAM_MAX_NOME 100
#define TAM_MAX_FUNCAO 100
#define SEMANAS_MES 4
```

Definem os limites de uso do sistema, como tamanho máximo de nomes e funções, e o número padrão de semanas no mês para cálculos salariais.

#### 3.3 Estrutura Funcionario

```c
typedef struct {
    char nome[...];
    char funcao[...];
    float salarioBase;
    float valorHoraExtra;
    int diasExtrasPorSemana;
    float horasExtrasPorDia;
    float totalHorasExtrasMes;
    float valorTotalExtrasMes;
} Funcionario;
```

Representa um registro completo do funcionário com dados para cálculo de salário.

#### 3.4 Variáveis Globais e Tabelas de Dados

```c
Funcionario *funcionarios = NULL;
int quantidade = 0;
const char *funcoes[] = {...};
const float salariosBase[] = {...};
const float valorHoraExtra[] = {...};
const float limiteHorasExtrasSemanais[] = {...};
```

* `funcionarios` é um ponteiro para vetor dinâmico de `Funcionario`.
* `quantidade` representa o número atual de funcionários.
* As tabelas utilizam índices compatíveis para associação de função, salário e valores.

---

### 4. Funcionalidades

#### 4.1 Cadastro de Funcionário

A função `cadastrarFuncionario()` solicita dados, valida entradas e realiza cálculo de horas extras. Ao final, usa `realloc()` para expandir o vetor dinâmico de forma segura.

#### 4.2 Listagem de Funcionários

A função `listarFuncionarios()` percorre o vetor e imprime os dados de cada funcionário, incluindo cálculo do salário total.

#### 4.3 Exclusão de Funcionário

A função `excluirFuncionario()` utiliza índice informado pelo usuário, move os dados subsequentes e reduz o tamanho do vetor com `realloc()`.

#### 4.4 Liberação de Memória

A função `liberarMemoria()` utiliza `free()` para evitar vazamentos de memória.

#### 4.5 Menu Interativo

A função `menu()` é responsável pela interação com o usuário e chamada das demais funções.

---

### 5. Alocação Dinâmica de Memória

O programa utiliza `realloc()` para expandir ou reduzir o vetor de funcionários conforme a necessidade. Esta abordagem é eficiente pois economiza memória e evita limites fixos artificiais, ao contrário de vetores estáticos.

---

### 6. Uso de Índice

O sistema associa as funções aos dados salariais por meio do índice selecionado pelo usuário. Esta técnica elimina estruturas repetitivas e facilita a manutenção.

---

### 7. Considerações Finais

O sistema desenvolvido cumpre com os objetivos propostos, utilizando boas práticas de programação em C, como modularização de funções, uso de structs, controle de entradas e alocação dinâmica de memória.

---

### 8. Sugestões de Futuras Melhorias

* Implementar gravação e leitura de dados em arquivo (persistência);
* Adicionar ordenação e busca por nome;
* Melhorar validação de entradas usando `isalpha()` e `tolower()`;
* Usar listas ligadas para evitar realocações constantes.

