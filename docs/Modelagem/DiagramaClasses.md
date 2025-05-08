# Modelagem Estática - Diagrama de Classes

## Introdução

A modelagem estática com UML (Unified Modeling Language) é uma etapa fundamental no desenvolvimento de sistemas orientados a objetos. Ela permite visualizar, planejar e documentar a estrutura interna do sistema antes da implementação, promovendo melhor entendimento entre os membros da equipe e maior consistência no código.

Neste projeto, aplicamos a diagramação UML por meio do Diagrama de Classes, que representa graficamente as principais entidades da aplicação Meu Aquário, seus atributos, comportamentos (métodos) e os relacionamentos entre elas. Este modelo fornece uma visão clara e formal da camada de domínio da aplicação, servindo como referência para as demais etapas do desenvolvimento.

A diagramação foi feita utilizando boas práticas de engenharia de software, seguindo padrões de design orientado a objetos, e está alinhada com os requisitos definidos nas fases iniciais do projeto.

## Metodologia

A construção do modelo foi feita com base nos requisitos funcionais e não funcionais levantados durante a fase de análise. Utilizou-se a abordagem orientada a objetos, respeitando princípios como encapsulamento, responsabilidade única e coesão. A notação UML (Unified Modeling Language) foi aplicada seguindo os exemplos dos conteúdos usados como referência.

Para a elaboração do diagrama de classes, foi utilizada a ferramenta draw.io, que oferece recursos visuais intuitivos e compatibilidade com a notação UML, facilitando a criação e edição dos modelos.

<h2 align="center">Diagrama de Classes</h2>

<div align="center">
    <img src="./assets/DiagramaClasses.png" alt="Diagrama de classes">
</div>

<p align="center"><em> Imagem 01 - Diagrama de Classes </em></p>
<p align="center"><strong>Autor:</strong> Brenno Silva</p>

---

## Detalhes do Diagrama

### Classe *Usuario*

| Atributo | Tipo        | Descrição                          |
|----------|-------------|------------------------------------|
| id       | int         | Identificador único                |
| nome     | String      | Nome do usuário                    |
| email    | String      | Email para login e contato         |
| senha    | String      | Senha criptografada                |
| tipo     | TipoUsuario | Enum indicando se é Comum ou Administrador |
| postagens        | List\<Postagem\>        | Postagens feitas pelo usuário     |
| comentarios      | List\<Comentario\>      | Comentários realizados            |
| postagensSalvas  | List\<PostagemSalva\>   | Postagens salvas pelo usuário     |

#### Métodos:

+ autenticar(email: String, senha: String): boolean
+ criarPostagem(titulo: String, conteudo: String, midias: List\<Midia\>): Postagem
+ editarPerfil(novoNome: String, novoEmail: String): void
+ alterarSenha(senhaAtual: String, novaSenha: String): boolean
+ listarPostagensSalvas(): List\<Postagem\>

#### Relacionamentos:

+ *Usuario* cria *Postagem* - Agregação
+ *Usuario* \<\<use>\> *TipoUsuario* - Dependência
+ *Usuario* publica *Comentario* - Associação
+ *Usuario* salva *PostagemSalva* - Associação

---

### Classe *Postagem*

| Atributo     | Tipo             | Descrição                          |
|--------------|------------------|-------------------------------------|
| id           | int              | Identificador único                 |
| titulo       | String           | Título da postagem                  |
| conteudo     | String           | Texto principal                     |
| dataCriacao  | LocalDate        | Data de criação                     |
| autor        | Usuario          | Referência ao autor                 |
| comentarios  | List\<Comentario\> | Lista de comentários                |
| midias       | List\<Midia\>      | Lista de mídias associadas          |

#### Métodos:

+ adicionarComentario(autor: Usuario, texto: String): Comentario
+ adicionarMidia(url: String, tipo: TipoMidia): Midia
+ removerMidia(midiaId: Long): boolean
+ atualizarTitulo(novoTitulo: String): void
+ atualizarConteudo(novoConteudo: String): void
+ listarComentarios(): List\<Comentario\>

#### Relacionamentos:

+ *Postagem* é criada por *Usuario* - Agregação
+ *Postagem* é referenciada por *PostagemSalva* - Associação
+ *Postagem* possui *Comentario* - Composição
+ *Postagem* contem *Midia* - Composição

---

### Classe *Comentario*

| Atributo     | Tipo      | Descrição                     |
|--------------|-----------|-------------------------------|
| id           | int       | Identificador único           |
| texto        | String    | Conteúdo do comentário        |
| data         | LocalDate | Data do comentário            |
| autor        | Usuario   | Autor do comentário           |
| postagem     | Postagem  | Postagem referenciada         |

#### Métodos:

+ editarTexto(novoTexto: String, editor: Usuario): boolean

#### Relacionamentos:

+ *Comentario* é publicado por *Usuário* - Associação
+ *Comentario* é possuído por *Postagem* - Composição

---

### Classe *PostagemSalva*

Representa uma postagem que foi salva por um usuário, para consulta posterior.

| Atributo    | Tipo     | Descrição                         |
|-------------|----------|------------------------------------|
| id          | int      | Identificador único                |
| usuario     | Usuario  | Quem salvou a postagem             |
| postagem    | Postagem | Referência à postagem salva        |
| dataSalva   | LocalDate| Quando foi salva                   |

#### Métodos:

+ adicionarNota(nota: String): void

#### Relacionamentos:

+ *PostagemSalva* é salva por *Usuario* - Associação
+ *PostagemSalva* referencia *Postagem* - Associação

---

### Classe *Midia*

| Atributo | Tipo        | Descrição                        |
|----------|-------------|----------------------------------|
| id       | int         | Identificador único              |
| url      | String      | Caminho do arquivo               |
| tipo     | TipoMidia   | Enum: FOTO ou VIDEO              |
| postagem | Postagem    | Postagem à qual pertence         |

#### Métodos:

+ getUrl(): String
+ getTipo():TipoMidia

#### Relacionamentos:

+ *Midia* é contida em *Postagem* - Composição
+ *Midia* \<\<use>\> *TipoMidia* - Dependência

---

### Classe *Glossario*

| Atributo | Tipo    | Descrição                        |
|----------|---------|----------------------------------|
| id       | int     | Identificador                    |
| termo    | String  | Palavra ou termo técnico         |
| definicao| String  | Significado do termo             |

#### Métodos:

+ buscarTermo(termo: String): Optional\<Glossario\>
+ gets e sets(): void

#### Relacionamentos:

+ Independente (não se relaciona diretamente com outras classes). Os dados são apenas consultados por usuários.

---

### Classe *WikiPeixe*

| Atributo     | Tipo   | Descrição                    |
|--------------|--------|------------------------------|
| id           | int    | Identificador único          |
| nomeComum    | String| Nome popular do peixe        |
| nomeCientifico| String| Nome científico do peixe     |
| descricao    | String| Descrição detalhada          |
| phIdeal     | Double | PH ideal da água do peixe    |
| temperaturaIdeal | Double | Temperatura ideal da agua para o peixe |
| dificuldade | NivelCuidado | Enum: Facil, Medio ou Dificil |

#### Métodos:

+ gets e sets(): void

#### Relacionamentos:

+ *WikiPeixe* \<\<use>\> *NivelCuidado* - Dependência
+ Independente (não se relaciona diretamente com outras classes). Os dados são apenas consultados por usuários.

---

### Enum *TipoUsuario*

| Tipos |
| ----- |
| Comum |
| Administrador |

#### Relacionamentos:

+ *TipoUsuario* é usado por *Usuario* - Dependência

### Enum *TipoMidia*

| Tipos |
| ----- |
| Video |
| Foto |
| Documento |

#### Relacionamentos:

+ *TipoMidia* é usado por *Midia* - Dependência

### Enum *NivelCuidado*

| Tipos |
| ----- |
| Facil |
| Medio |
| Dificil |

#### Relacionamentos:

+ *NivelCuidado* é usado por *WikiPeixe* - Dependência

## Referências Bibliográficas

- UML-DIAGRAMS. The Unified Modeling Language. Disponível em: [https://www.uml-diagrams.org/](https://www.uml-diagrams.org/). Acesso em: 04 maio. 2025.

- SERRANO, Milene. **AULA - MODELAGEM UML ESTÁTICA**. [S. l.], 2025. 55 slides. Disponível em: [AULA-MODELAGEM UML ESTÁTICA.pdf](https://aprender3.unb.br/pluginfile.php/3070937/mod_page/content/1/Arquitetura%20e%20Desenho%20de%20Software%20-%20Aula%20Modelagem%20UML%20Est%C3%A1tica%20-%20Profa.%20Milene.pdf). Acesso em:  03 maio. 2025.

## Histórico de Versão
| Versão | Alteração | Responsável | Data       |
|------|--------|-----------|---------|
| 1.0 | Criação do arquivo | [Brenno Silva](https://github.com/brenno-silva01) | 05/05/2025 |
| 1.1 | Adição da descrição do diagrama | [Brenno Silva](https://github.com/brenno-silva01) | 05/05/2025 |
| 1.2 | Adição da imagem do diagrama | [Brenno Silva](https://github.com/brenno-silva01) | 05/05/2025 |
| 2.0 | Adição dos métodos e relacionamentos à descrição das classes | [Brenno Silva](https://github.com/brenno-silva01) | 06/05/2025 |
| 2.1 | Atualização da imagem do diagrama | [Brenno Silva](https://github.com/brenno-silva01) | 06/05/2025 |
| 2.2 | Ajuste na exibição do diagrama | [Brenno Silva](https://github.com/brenno-silva01) | 07/05/2025 | 

