# OSLite_POO


## Descrição do Projeto

O projeto **OSLite_POO** implementa um mini-domínio de **Ordem de Serviço** para uma assistência técnica, aplicando os conceitos fundamentais de **Programação Orientada a Objetos (POO)** em C#.  
A solução foi construída com foco em **modelagem de domínio**, boas práticas de **encapsulamento** e **testabilidade**, conforme os requisitos estabelecidos pelo professor.

---

## Estrutura do Domínio

O sistema foi modelado com **três entidades principais**:

- `Cliente` – Representa o cliente da assistência técnica.
- `OrdemDeServico` – Modela a ordem de serviço, associada a um cliente e composta por itens.
- `ItemDeServico` – Representa os serviços ou produtos que compõem uma ordem.

Além das entidades, o domínio utiliza **Value Objects** e **Enums**:

### Value Objects

- `Money` (record struct) – Representa valores monetários, garantindo imutabilidade e validação.
- `Email` (record) – Garante formato e integridade do endereço de e-mail.

### Enums

- `StatusOS` – Define os estados possíveis da ordem (`Aberta`, `EmExecucao`, `Concluida`, `Cancelada`).
- `CategoriaItem` – Classifica itens como `Diagnóstico`, `Peças` ou `Mão de Obra`.

---

## Restrições e Regras de Negócio

- Associações 1:N entre `Cliente → Ordens` e `Ordem → Itens`.
- Navegabilidade bidirecional entre `Cliente` e `Ordem`.
- Composição entre `Ordem` e `Itens`.
- Proibição de herança e polimorfismo.
- Sem associações N:M.
- Proteção de invariantes com exceções (**fail-fast**).
- Cálculo do total derivado dos itens, sem redundância de dados.
- Bloqueios de ações em estados finais (`Concluída` ou `Cancelada`).

---

## Abordagem de Desenvolvimento

A implementação foi **dirigida por TDD (Test-Driven Development)**, com cobertura de:

- **Casos felizes** (fluxos esperados).
- **Casos de falha** (violação de regras e transições inválidas).

Os testes utilizam **xUnit** e **FluentAssertions**, garantindo clareza e rastreabilidade.

---

## Estrutura do Projeto

OSLite_POO/
├── OSLite.Domain/
│ ├── Models/
│ ├── ValueObjects/
│ ├── Enums/
│ └── OSLite.Domain.csproj
├── OSLite.Domain.Tests/
│ ├── Tests/
│ └── OSLite.Domain.Tests.csproj
├── REFLECTION.pdf
└── .github/workflows/dotnet.yml


---

## Execução dos Testes

1. Instale o SDK do **.NET 8.0** ou superior.
2. No terminal, execute:

```bash``
dotnet restore
dotnet test ./OSLite.Domain.Tests/OSLite.Domain.Tests.csproj
``

Reflexão

O documento REFLECTION.pdf apresenta uma análise sobre o uso de record, record struct e enum na clareza, testabilidade e manutenção do código, conforme solicitado no enunciado do trabalho.

Autor - Desenvolvido por: Shara Palharini Lima
Curso: Ciências da Computação
Disciplina: Programação Orientada a Objetos (POO)
Ano: 2025
