# Modelagem Organizacional - Diagrama de Casos de Uso

## Introdução

O diagrama de casos de uso é uma ferramenta da UML que permite representar as funcionalidades principais de um sistema na perspectiva dos usuários. Ele foca no "o que" o sistema faz, e não no "como", sendo essencial para entender os requisitos funcionais em alto nível.

Esse tipo de diagrama identifica os atores que interagem com o sistema e os casos de uso, que representam as ações que esses atores podem executar. Essa modelagem serve como base para decisões de projeto, priorização de funcionalidades e rastreabilidade com outros diagramas (como atividades ou classes).

No projeto *Meu Aquário*, o diagrama de casos de uso representa as interações possíveis com o sistema por parte de visitantes, usuários cadastrados e administradores da plataforma.

---

## Metodologia

Para construir o diagrama, foram considerados os principais fluxos do sistema com base nos requisitos do projeto. Os atores foram definidos conforme os níveis de acesso (usuário visitante, autenticado e administrador). Em seguida, os casos de uso foram identificados e agrupados, observando onde há ações comuns, exclusivas ou herdadas.

A notação UML foi aplicada seguindo boas práticas:
- Elipses para representar casos de uso
- Bonecos/ícones para os atores
- Setas sólidas para associações
- Setas com triângulo para generalizações
- Estereótipos `<<include>>` e `<<extend>>` usados para descrever relacionamentos entre casos

O diagrama foi construído utilizando a ferramenta draw.io, na qual possui uma grande váriedade de icones e representações assim como as da notação UML.

---

## Diagrama de Casos de Uso

<h2 align="center">Diagrama de Casos de Uso</h2>

<div align="center">
    <img src="./assets/DiagramaCasosUso.png" alt="Diagrama de Casos de Uso">
</div>

<p align="center"><em>Imagem 01 - Diagrama de Casos de Uso do sistema Meu Aquário</em></p>
<p align="center"><strong>Autor:</strong> Brenno Silva</p>

---

## Atores do Diagrama

### 1 - Usuário Não Autenticado
Representa qualquer visitante do sistema que ainda não fez login. Pode visualizar postagens, buscar conteúdo, acessar o glossário e a wiki, além de realizar login ou cadastro.

### 2 - Usuário Autenticado
Representa um usuário logado na plataforma. Herda todas as permissões do visitante e ganha acesso a interações como: criar postagens, comentar, salvar postagens, editar perfil e sair do sistema.

### 3 - Administrador
Ator com permissões especiais, responsável por gerenciar os dados técnicos do sistema: termos do glossário e informações da wiki sobre espécies de peixes.

---

## Casos de Uso

| Caso de Uso                  | Atores envolvidos             | Descrição                                                                     |
|------------------------------|-------------------------------|-------------------------------------------------------------------------------|
| Visualizar postagens         | Todos os usuários             | Consulta ao feed público de postagens compartilhadas                          |
| Pesquisar conteúdo           | Todos os usuários             | Busca postagens por título, tema ou palavras-chave                            |
| Visualizar glossário         | Todos os usuários             | Acesso aos termos técnicos e definições                                       |
| Visualizar wiki de peixes    | Todos os usuários             | Consulta a informações técnicas de espécies                                   |
| Fazer login                  | Usuário Não Autenticado       | Autentica credenciais para liberar acesso restrito                            |
| Cadastrar-se                 | Usuário Não Autenticado       | Cria uma nova conta no sistema                                                |
| Criar postagem               | Usuário Autenticado           | Publica novo conteúdo com ou sem mídias                                       |
| Comentar postagem            | Usuário Autenticado           | Comenta em postagens de outros usuários                                       |
| Salvar postagem              | Usuário Autenticado           | Armazena postagens favoritas para consulta futura                             |
| Editar perfil                | Usuário Autenticado           | Altera informações pessoais                                                   |
| Fazer logout                 | Usuário Autenticado           | Finaliza a sessão do usuário                                                  |
| Gerenciar glossário          | Administrador                 | Adiciona, edita ou remove termos técnicos                                     |
| Gerenciar wiki de peixes     | Administrador                 | Atualiza a base de dados de espécies                                          |

---

## Relacionamentos entre Casos de Uso

| Origem               | Tipo de Relacionamento | Alvo                       | Observação                                                              |
|----------------------|------------------------|----------------------------|-------------------------------------------------------------------------|
| Criar postagem       | `<<include>>`          | Validar dados              | Validação obrigatória antes de publicar  |
| Comentar postagem    | `<<include>>`          | Validar comentário         | Comentário só é salvo após validação     |
| Editar perfil        | `<<include>>`          | Atualizar informações      | A edição exige verificação e atualização de dados |
| Salvar postagem      | `<<extend>>`           | Adicionar nota         | O usuário pode opcionalmente adicionar uma nota a postagem salva |

---

## Relacionamentos entre Atores e Casos de Uso

| Ator                    | Tipo de Relação        | Casos de Uso                             |
|-------------------------|------------------------|------------------------------------------|
| Usuário Não Autenticado | Associação             | Visualizar postagens, Pesquisar conteúdo, Visualizar glossário, Visualizar wiki, Fazer login, Cadastrar-se |
| Usuário Autenticado     | Associação             | Criar postagem, Comentar postagem, Salvar postagem, Editar perfil, Fazer logout  |
| Usuário Autenticado     | Generalização          | Herda de: Usuário Não Autenticado  |
| Administrador           | Associação             | Gerenciar glossário, Gerenciar wiki de peixes |

---

## Referências Bibliográficas

- UML-DIAGRAMS. The Unified Modeling Language - Use Case Diagrams. Disponível em: [https://www.uml-diagrams.org/use-case-diagrams.html](https://www.uml-diagrams.org/use-case-diagrams.html). Acesso em: 07 maio. 2025.

- DEVMEDIA. O que é UML e Diagramas de Caso de Uso: Introdução Prática à UML. Disponível em: [https://www.devmedia.com.br/o-que-e-uml-e-diagramas-de-caso-de-uso-introducao-pratica-a-uml/23408](https://www.devmedia.com.br/o-que-e-uml-e-diagramas-de-caso-de-uso-introducao-pratica-a-uml/23408). Acesso em: 08 maio. 2025.

- AUGUSTO, João. **Análise e Projeto de Sistemas Casos de Uso (Use case)**. [S. l.], 2025. 17 slides. Disponível em: [Slides sobre Casos de Uso](https://docente.ifsc.edu.br/joao.augusto/MaterialDidatico/2018-1/An%C3%A1lise%20e%20Projeto%20de%20Sistemas/Diagrama%20de%20Casos%20de%20Uso.pdf)

- SOUZA, Givanaldo. **Diagrama de Caso de Uso**. [S. l.], 2025. 24 slides. Disponível em: [Slides sobre Casos de Uso](https://docente.ifrn.edu.br/givanaldorocha/disciplinas/engenharia-de-software-licenciatura-em-informatica/diagrama-de-casos-de-uso)

---

## Histórico de Versão

| Versão | Alteração                                     | Responsável                                | Data       |
|--------|-----------------------------------------------|--------------------------------------------|------------|
| 1.0    | Criação do documento e estrutura base         | [Brenno Silva](https://github.com/brenno-silva01) | 08/05/2025 |
| 1.1    | Adição das explicações do diagrama            | [Brenno Silva](https://github.com/brenno-silva01) | 08/05/2025 |
| 2.0    | Adição da imagem do diagrama                  | [Brenno Silva](https://github.com/brenno-silva01) | 08/05/2025 |
| 2.1    | Atualização das referências bibliográficas    | [Brenno Silva](https://github.com/brenno-silva01) | 08/05/2025 |
