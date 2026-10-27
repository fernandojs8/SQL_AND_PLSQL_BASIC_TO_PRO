# SQL e PL/SQL — consultas, modelagem e rotinas de banco

Coleção de estudos de bancos relacionais: scripts **T-SQL para SQL Server** e exercícios de **SQL/PLSQL para Oracle**. Inclui material desenvolvido no contexto do curso de SQL da Softblue e estudos de PL/SQL da Alura.

O objetivo é explorar modelagem, consultas e programação no banco. Os arquivos são exercícios independentes e anotações; não constituem uma migração única pronta para aplicar.

## Organização

| Diretório | Conteúdo e dialeto |
| --- | --- |
| [Script de Banco de Dados](Script%20de%20Banco%20de%20Dados) | SQL Server: tabelas, inserts, índices, views, agregação, paginação, transações, procedure e trigger. |
| [PLSQL](PLSQL) | Oracle: exemplos de `MERGE` e exercícios com `VARCHAR2`, `NUMBER`, sequences e constraints. |
| [Exercícios](Exerc%C3%ADcios) | Material complementar de estudo. |

Os dialetos devem ser executados em bancos separados. `GO`, `sys.objects` e `@@ERROR` são exemplos de recursos presentes no conjunto SQL Server; `VARCHAR2` e `NEXTVAL` aparecem no conjunto Oracle.

## Exemplos para explorar

- **Modelagem:** Funcionario, CPF e Veiculo demonstram chaves primárias e estrangeiras; Cliente possui referência a outro cliente.
- **Consultas:** agrupamento por departamento com `AVG`, subconsulta com `HAVING` e paginação com `OFFSET/FETCH`.
- **Rotinas:** `usp_Pedido_DeletarNaoPago` exclui pedidos não pagos; a trigger de inserção de Estoque chama essa procedure.
- **Transação:** o exercício ContaBancaria debita uma conta e credita outra, ilustrando commit e rollback.
- **Oracle:** exercícios de COMPRAS, sequência de IDs e diferentes formas de `MERGE`.

## Como estudar e executar

Pré-requisitos: Git, uma instância de SQL Server com cliente como SSMS para T-SQL; uma instância Oracle com cliente como SQL Developer para os exercícios Oracle.

```bash
git clone https://github.com/fernandojs8/SQL_AND_PLSQL_BASIC_TO_PRO.git
cd SQL_AND_PLSQL_BASIC_TO_PRO
```

### SQL Server

1. Crie uma base **descartável de estudo** chamada `CursoSQL`, usada pelos comandos `USE` dos arquivos.
2. Abra apenas os scripts do exercício escolhido. Crie tabelas referenciadas antes das tabelas com foreign keys: por exemplo, Funcionario antes de CPF/Veiculo.
3. Insira dados fictícios respeitando as dependências e confira o resultado com SELECT.
4. Execute views, índices, procedures e triggers somente depois dos objetos de que dependem.

Não há instalador nem sequência completa automatizada. Revise cada script: há comandos de alteração e exclusão. A trigger de Estoque tem efeito sobre Pedido; não execute a pasta inteira indiscriminadamente.

### Oracle

Use um schema de estudo próprio. Selecione um exercício, identifique os objetos necessários e adapte placeholders antes da execução. Alguns arquivos misturam listas de comandos, trechos incompletos e alternativas do mesmo exercício; não são scripts executáveis integralmente sem revisão.

## Validação e limitações

- Não foi identificada suíte automatizada de testes de banco. A documentação foi revisada por leitura estática; os scripts não foram executados nesta revisão.
- Há exemplos com erros de sintaxe/placeholders e inconsistências de nomes. Por exemplo, `PLSQL/Merge.sql` usa nomes genéricos de tabelas/colunas e precisa de adaptação.
- Alguns arquivos legados apresentam diferenças de codificação; confira os textos antes de gravar ou comparar dados.
- Os exemplos de tratamento de transações são didáticos e precisam de revisão de rollback e tratamento de falhas antes de reutilização em uma aplicação.
- Tipos monetários e regras de negócio também devem ser revistos: há exemplos com `FLOAT` e saldos inteiros.

## Próximos passos propostos

1. Separar scripts executáveis de anotações e corrigir sintaxe por dialeto.
2. Documentar a ordem de criação e adicionar seed/reset para bases descartáveis.
3. Criar testes de constraints, procedures, triggers e rollback em instâncias de teste.
4. Registrar planos de execução e medições antes/depois de índices, com dataset e consulta reproduzíveis.
5. Para uma demonstração cloud, publicar provisionamento e pipeline de validação de um banco escolhido, com resultados reais e dados fictícios. Não há evidência de implantação cloud apresentada por estes exercícios.

## Referência educacional

[Curso SQL da Softblue](http://www.softblue.com.br/site/curso/id/3/CURSO+DE+SQL+COMPLETO+BASICO+AO+AVANCADO+ON+LINE+BD03+GRATIS). O link original é mantido como referência histórica; a disponibilidade do curso não foi validada.
