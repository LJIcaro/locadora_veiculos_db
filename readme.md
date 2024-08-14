# locadora_veiculos_db

O principal objetivo é a criação de um banco de dados para guardar informações dos Clientes, Funcionários e Veículos com suas respectivas Marcas e Modelos Tendo para armazenar informações das reservas dos carros vinculados aos contratos de locação onde servem como principal base para o controle do sistema por meio dos funcionários responsáveis da entrada e saída de veículos na locadora.

- [Sobre](#sobre)
- [Funcionalidades](#funcionalidades)
- [Estrutura do Banco](#estrutura-do-banco)
- [Requisitos](#requisitos)
- [Instalação](#instalação)
- [Considerações Finais](#considerações-finais)
- [Autores](#autores)
- [Licença](#licença)

## Sobre

Este projeto foi desenvolvido como parte de um processo avaliativo semestral do Centro Universirtário Uniruy cuja a disciplina foi ministrada pelo Professor Heleno Cardoso. O projeto pode ser escalado conforme a necessidade e tem posibilidade de ser adaptado e implementado em qualquer aplicação que o demande.

## Funcionalidades

1) O Sistema Cadastra, Modifica, Exclui e Busca Informações dos
Funcionários;
2) O Sistema Pede Login e Senha dos Funcionários;
3) O Sistema Cadastra, Modifica, Exclui e Busca Informações dos Clientes;
4) O Sistema Pede Login e Senha dos Clientes;
5) O Sistema Cadastra, Modifica, Exclui e Busca Informações dos Veículos,
juntamente com as Marcas e modelos;
6) O Sistema informa a disponibilidade do Modelo do veículo;
7) O Sistema retém informações no Contrato de locação do veículo que o
cliente reserva e também os dados do pagamento;
8) O Sistema Informa Defeitos encontrados, conforme a realização do
Checklist na devolução no término de locação do veículo;
9) O Sistema Guarda e Consulta Informações da Nota Fiscal gerada para
pagamento, referente ao defeito do veículo;

## Estrutura do Banco

Uma visão geral das tabelas, relacionamentos e outros objetos importantes:


**Modelagem Entidade-Relacionamento ou Modelo Conceitual:** A partir das funcionalidades do banco de dados foi elaborado o modelo E.R O modelo conceitual ou Diagrama Entidade-Relacionamento (DER), define as entidades e requisitos do banco de dados, e de que maneira se relacionam.


**Entidades Principais:**

- Cliente
- Funcionários
- Veículo
- Marca
- Modelo
- ContratoLocacao
- Checklist
- Defeitos
- NFDefeito
- Peças


**Relacionamentos:**

- *Um cliente pode fazer vários contratos de locação* (relação 1 para N entre
Cliente e ContratoLocacao);
- *Um funcionário pode estar associado a vários contratos de locação* (relação
1 para N entre Funcionários e ContratoLocacao);
- *Um veículo pode estar associado a vários contratos de locação* (relação 1
para N entre Veículo e ContratoLocacao);
- *Um veículo pertence a um modelo de carro* (relação 1 para 1 entre Veículo e
Modelo);
- *Um modelo de carro pertence a uma marca* (relação 1 para 1 entre Modelo e
Marca);
- *Um contrato de locação pode ter vários checklists* (relação 1 para N entre
ContratoLocacao e Checklist);
- *Um checklist pode estar associado a vários defeitos* (relação 1 para N entre
Checklist e Defeitos);
- *Um defeito pode estar relacionado a uma nota fiscal de defeito* (relação 1
para 1 entre Defeitos e NFDefeito);
- *Uma nota fiscal de defeito pode ter várias peças relacionadas* (relação 1 para
N entre NFDefeito e Peças);


**Modelo Lógico:** O modelo lógico relacional define quais os nomes das tabelas e os nomes das colunas que compõem essas tabelas, tal como o tipo de dado que cada coluna vai receber, e a cardinalidade entre as tabelas no BD.


**CHAVES DAS TABELAS**

***Primárias:***

- **Cliente**: *idclientecpf*
- **Funcionários:** *idfuncionarios*
- **Veículo:** *idplaca*
- **Marca:** *idmarca*
- **Modelo:** *idmodelo*, *marca_idmarca*
- **ContratoLocacao**: *idreserva*
- **Checklist**: *idchecklist, reserva_idreserva*
- **Defeitos**: *iddefeitos*
- **NFDefeito**: *defeitos_iddefeitos*
- **Peças**: *idpecas*, *nfdefeito_defeitos_iddefeitos*

***Secundárias:***

- A tabela **ContratoLocacao** possui chaves estrangeiras para
***Cliente*** e ***Funcionários***.
- A tabela **Veículo** possui chaves estrangeiras para
***ContratoLocacao*** e ***Modelo***.
- A tabela **Checklist** possui chave estrangeira para
***ContratoLocacao***.
- A tabela **Defeitos** possui chave estrangeira para ***Checklist***.
- A tabela **NFDefeito** possui chave estrangeira para ***Defeitos***.
- A tabela **Peças** possui chave estrangeira para ***NFDefeito***.

## Requisitos

- MySQL Server 8.0 ou superior
- MySQL Workbench (opcional, para gerenciamento)

## Instalação

1. Clone o repositório:
   ```bash
   git clone https://github.com/ljicaro/locadora_veiculos_db.git
2. Importe o arquivo schema.sql no seu MySQL para criar as tabelas:
   ```sql
   source caminho/para/db/schema.sql;
3. (Opcional) Importe o arquivo data.sql para inserir exemplos de dados:
   ```sql
   source caminho/para/db/data.sql;
4. (Opcional) Importe o arquivo select.sql para selecionar conjuntos dados:
   ```sql
   source caminho/para/db/select.sql;
5. (Opcional) Importe o arquivo delete.sql para deletar dados:
   ```sql
    source caminho/para/db/delete.sql;


## Considerações Finais

A modelagem do banco de dados é uma parte crítica do desenvolvimento de aplicativos e sistemas que envolvem o armazenamento e recuperação de informações. Além disso, abordamos questões relacionadas à integridade referencial, garantindo que as relações entre as tabelas sejam mantidas para evitar dados inconsistentes e conflitantes. Compreendemos que a manutenção da integridade dos dados é essencial para garantir a qualidade e confiabilidade das informações armazenadas no banco de dados.

## Autores

- Ícaro Lima: https://github.com/LJIcaro
- Ruan Müller: https://github.com/ruanmuller20
- Alan Goes: https://github.com/alangoess

## Licença

Este projeto está licenciado sob a MIT License.

