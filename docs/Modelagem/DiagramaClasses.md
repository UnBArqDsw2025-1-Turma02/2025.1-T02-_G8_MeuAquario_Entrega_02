# Modelagem Estática - Diagrama de Classes

## Introdução

A modelagem estática com UML (Unified Modeling Language) é uma etapa fundamental no desenvolvimento de sistemas orientados a objetos. Ela permite visualizar, planejar e documentar a estrutura interna do sistema antes da implementação, promovendo melhor entendimento entre os membros da equipe e maior consistência no código.

Neste projeto, aplicamos a diagramação UML por meio do Diagrama de Classes, que representa graficamente as principais entidades da aplicação Meu Aquário, seus atributos, comportamentos (métodos) e os relacionamentos entre elas. Este modelo fornece uma visão clara e formal da camada de domínio da aplicação, servindo como referência para as demais etapas do desenvolvimento.

A diagramação foi feita utilizando boas práticas de engenharia de software, seguindo padrões de design orientado a objetos, e está alinhada com os requisitos definidos nas fases iniciais do projeto.

## Metodologia

A construção do modelo foi feita com base nos requisitos funcionais e não funcionais levantados durante a fase de análise. Utilizou-se a abordagem orientada a objetos, respeitando princípios como encapsulamento, responsabilidade única e coesão. A notação UML (Unified Modeling Language) foi aplicada seguindo os exemplos dos conteúdos usados como referência.

Para a elaboração do diagrama de classes, foi utilizada a ferramenta draw.io, que oferece recursos visuais intuitivos e compatibilidade com a notação UML, facilitando a criação e edição dos modelos.

## Diagrama de Classes

> Clique na imagem para ampliá-la:

![Diagrama de Classes](./caminho/para/o/arquivo/diagrama-de-classes.png)

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
| postagens        | List<Postagem>        | Postagens feitas pelo usuário     |
| comentarios      | List<Comentario>      | Comentários realizados            |
| postagensSalvas  | List<PostagemSalva>   | Postagens salvas pelo usuário     |

#### Métodos principais:

- `salvarPostagem(Postagem p): void`
- `comentar(Postagem p, String texto): void`

---

### Classe *Postagem*

| Atributo     | Tipo             | Descrição                          |
|--------------|------------------|-------------------------------------|
| id           | int              | Identificador único                 |
| titulo       | String           | Título da postagem                  |
| conteudo     | String           | Texto principal                     |
| dataCriacao  | LocalDate        | Data de criação                     |
| autor        | Usuario          | Referência ao autor                 |
| comentarios  | List<Comentario> | Lista de comentários                |
| midias       | List<Midia>      | Lista de mídias associadas          |

#### Métodos principais:

- `adicionarComentario(Comentario c): void`

---

### Classe *Comentario*

| Atributo     | Tipo      | Descrição                     |
|--------------|-----------|-------------------------------|
| id           | int       | Identificador único           |
| texto        | String    | Conteúdo do comentário        |
| data         | LocalDate | Data do comentário            |
| autor        | Usuario   | Autor do comentário           |
| postagem     | Postagem  | Postagem referenciada         |

---

### Classe *PostagemSalva*

Representa uma postagem que foi salva por um usuário, para consulta posterior.

| Atributo    | Tipo     | Descrição                         |
|-------------|----------|------------------------------------|
| id          | int      | Identificador único                |
| usuario     | Usuario  | Quem salvou a postagem             |
| postagem    | Postagem | Referência à postagem salva        |
| dataSalva   | LocalDate| Quando foi salva                   |

---

### Classe *Midia*

| Atributo | Tipo        | Descrição                        |
|----------|-------------|----------------------------------|
| id       | int         | Identificador único              |
| url      | String      | Caminho do arquivo               |
| tipo     | TipoMidia   | Enum: FOTO ou VIDEO              |
| postagem | Postagem    | Postagem à qual pertence         |

---

### Classe *Glossario*

| Atributo | Tipo    | Descrição                        |
|----------|---------|----------------------------------|
| id       | int     | Identificador                    |
| termo    | String  | Palavra ou termo técnico         |
| definicao| String  | Significado do termo             |

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

---

### Enum *TipoUsuario*

| Tipos |
| ----- |
| Comum |
| Administrador |

### Enum *TipoMidia*

| Tipos |
| ----- |
| Video |
| Foto |
| Documento |

### Enum *NivelCuidado*

| Tipos |
| ----- |
| Facil |
| Medio |
| Dificil |

## Referências Bibliográficas

- UML-DIAGRAMS. The Unified Modeling Language. Disponível em: [https://www.uml-diagrams.org/](https://www.uml-diagrams.org/). Acesso em: 04 maio. 2025.

- SERRANO, Milene. **AULA - MODELAGEM UML ESTÁTICA**. [S. l.], 2025. 55 slides. Disponível em: [AULA-MODELAGEM UML ESTÁTICA.pdf](https://aprender3.unb.br/pluginfile.php/3070937/mod_page/content/1/Arquitetura%20e%20Desenho%20de%20Software%20-%20Aula%20Modelagem%20UML%20Est%C3%A1tica%20-%20Profa.%20Milene.pdf). Acesso em:  03 maio. 2025.

## Histórico de Versão
| Versão | Alteração | Responsável | Data       |
|------|--------|-----------|---------|
| 1.0 | Criação do arquivo | [Brenno Silva](https://github.com/brenno-silva01) | 05/05/2025 |
| 1.1 | Adição da descrição do diagrama | [Brenno Silva](https://github.com/brenno-silva01) | 05/05/2025 |
| 1.2 | Adição da imagem do diagrama | [Brenno Silva](https://github.com/brenno-silva01) | 05/05/2025 | 

