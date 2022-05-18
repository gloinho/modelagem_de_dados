*Várias informações desse git foram retiradas do canal Bóson Treinamentos durante meus estudos.* 
[Curso de Modelagem de Dados Bóson Treinamentos](https://www.youtube.com/playlist?list=PLucm8g_ezqNoNHU8tjVeHmRGBFnjDIlxD)

# Dados vs Informação
> Dados: são fatos em uma forma primária, que podem ser armazenados em algum meio (CPF, Nome, Data). Dados sem contexto não significam muita coisa, são como poeira ao vento. 

> Informação: São os fatos organizados de maneira a produzir um sifnificado (dados colocados em contexto) como por exemplo uma lista com Nome e Número de CPF ordenados.

# Metadados
> São "dados sobre os dados".
Permitem efetuar a representação e identificação dos dados, garantindo sua consistência e persistência.
Os Metadados são mantidos no Dicionário de dados.
  
# O que é um Banco de Dados?
> BD (Banco de Dados) ou DB (Database) é uma coleção organizada de dados. Esses dados são organizados de modo a modelar aspectos do mundo real, para que seja possível
efetuar processamento que gere informações relevantes para os usuários a partir desses dados.
Um BD é composto por diversos objetos como: tabelas(tables), esquemas(schemas) ,visões(views), consultas(queries), relatórios, procedimentos, triggers etc.
 
# Modelos de Banco de Dados
Fonte: [O Que é um modelo de banco de dados](https://www.lucidchart.com/pages/pt/o-que-e-um-modelo-de-banco-de-dados)

#### Modelo Hierárquico
> O modelo hierárquico organiza dados em uma estrutura do tipo árvore, onde cada registro tem um único "pai" ou raiz. Registros "irmãos" são classificados em uma ordem específica. Essa ordem é usada como a ordem física para armazenar o banco de dados. 
<img src="https://user-images.githubusercontent.com/99846614/169034709-d2a16596-f01b-4bab-b030-79c67f3c9e47.jpg" width="700" height="400" align="middle">

#### Modelo de Rede
> O modelo de rede se baseia no modelo hierárquico, permitindo relações muitas para muitas entre registros vinculados, implicando em vários registros "pai". 
Baseado na teoria de conjuntos matemáticos, o modelo é construído com conjuntos de registros relacionados. Cada conjunto consiste em um registro proprietário, ou "pai", e um ou mais registros de membro, ou "filho". Um registro pode ser um membro, ou "filho", em vários conjuntos, permitindo que esse modelo transmita relações complexas.
<img src="https://user-images.githubusercontent.com/99846614/169034743-c4bb0b95-bb72-4523-8e47-295a536288dd.jpg" width="400" height="400">

#### Modelo Relacional
> O modelo mais comum atualmente. 

Os dados são separados por Entidades. Cada entidade é composta por Relações (tabelas) que possuem caracteristicas que são chamadas de Atributos (que ficam nas Colunas da tabela). Nessas colunas irão existir Tuplas (linhas da tabela) onde serão alocados os dados de cada Entidade. 

> Uma entidade é a representação de alguma coisa do mundo real na qual desejamos armazenar dados. Ex: Alunos, Professores, Produtos.

> Uma relação é uma tabela onde serão alocadas propriedades (ou atributos) de uma entidade.

> Um atributo de entidade é uma propriedade ou característica inerente daquela entidade. Ex: Código de um produto, Nome de um Aluno.
No modelo relacional, as entidades podem se relacionar entre si (por isso é chamado de modelo relacional).

> Um relacionamento é a relação existente entre entidades.
Os relacionamentos serão abordados mais para frente com mais detalhes.
<img src="https://user-images.githubusercontent.com/99846614/169034672-c6811b1e-08b0-4942-b9c7-8e618427fce6.jpg" width="400" height="400">

 # SGBD (Sistema de Gerenciamento de Bancos de Dados)
 
> É uma coleção de softwares que permite aos usuários criarem e manterem um ou mais bancos de dados. 

#### Algumas Funções de um SGBD
- Inserir, excluir, acessar, visualizar, selecionar, ordenar, juntar ou intercalar registros;
- Copiar e eliminar ficheiros;
- Alterar estruturas de campos;
- Inserir, remover e estabelecer relações entre tabelas;
- Importar ou exportar dados entre outras bases de dados;
- Criar chaves primárias e externas;
- Realizar consultas, elaborar formulários e relatórios na base de dados;
- Criar usuários, com permissões de acesso diferenciados.

#### Tipos de SGBD
> SGBDR: sistemas que gerenciam bancos de dados *relacionais* (SQL)

> SGBD: sistemas que gerenciam bancos de dados *não relacionais (noSQL)

#### Mas o que raios é SQL e noSQL ??
> SQL é uma sigla para *"Structured Query Language"* ou *Linguagem de Consulta Estruturada*.

Como uma linguagem de programação usual, a SQL possui códigos para se 'comunicar' com um banco de dados relacional podendo criar, alterar, adicionar entidades, relações, atributos em um banco de dados. Ah, o SQL também tem códigos para criar um banco de dados relacional.

> NoSQL (Not Only SQL) é o termo utilizado para banco de dados não relacionais de alto desempenho, onde geralmente não é utilizado o SQL como linguagem de consulta. 

O NoSQL foi criado para ter uma performance melhor e uma escalabilidade mais horizontal para suprir necessidades onde os bancos relacionais não são eficazes.
Aqui será abordado apenas o SQL.

#### Principais SGBD
Por meio desse site [DB-Engines Ranking - Trend Popularity](https://db-engines.com/en/ranking) podemos ver as SGBDs mais utilizadas atualmente.
<img src="https://user-images.githubusercontent.com/99846614/169036377-4e36c8cf-936f-4300-883f-487012187912.jpg" width="700" height="200">

# Passo a Passo para Modelagem de um Banco de Dados
> Projeto realizado pela [Bóson Treinamentos](http://www.bosontreinamentos.com.br/) - Banco de Dados de uma Faculdade.

### Levantamento de Requisitos 
> Quem estabelece as regras do negócio é o cliente!!!

Nessa fase, você estará em constante comunicação com o cliente que solicitou o banco de dados. É provavelmente a fase mais importante da modelagem, visto que é nela que você irá basear o modelo do banco de dados.
Aqui listei alguma das regras identificadas no treinamento (foram mais, mas não coloquei todas para não me extender).
1. Um aluno só pode estar matriculado em um curso por vez.
2. Alunos possuem um código de identificação (RA)
3. Cursos são compostos por disciplinas
4. Cada disciplina terá no máximo 30 alunos por turma.
5. Cada professor é vinculado a um departamento.

É importante ressaltar que são INÚMERAS as regras, e não são finais!!! Ao longo de uma modelagem, novas regras podem surgir: o cliente entende bastante do negócio mas pode esquecer do relacionamento de alguma entidade (que gera uma regra nova).
O trabalho de levantamento de regras e requisitos é algo constante e que tem que ser manutenido. 

### Identificação de Entidades, Atributos e Relacionamentos

#### Entidades
Por meio das regras de negócio adquiridas pelo levantamento de requisitos, será possivel identificar algumas entidades. 
- Aluno
- Disciplina
- Curso
- Departamento
- Professor
#### Relacionamentos
Observando as regras de negócio, uma facilidade para encontrar alguns relacionamentos iniciais é observar a **verbalização** nas regras. Por exemplo: Cursos **são compostos** por disciplinas. Aqui podemos ver o relacionamento
entre duas entidades: *Cursos* e *Disciplinas*.
- Aluno **está matriculado** em Curso
- Aluno **cursa** Disciplina
- Aluno **realizou** Disciplina
- Disciplina **pertence** a Curso
- Professor **ministra** Disciplina
- Professor **pertence** a Departamento
- Departamento **é responsável por** Disciplina
- Departamento **controla** Curso
#### Atributos
Alguns atributos também podem ser retirados das regras de negócio
1. Aluno
- Numero da matricula
- Nome
- Endereço
- Rua
- Numero
- Bairro
- CEP
- Cidade
- Estado
- Código do Curso
2. Professor
- Código do Professor
- Nome
- Código do Departamento






