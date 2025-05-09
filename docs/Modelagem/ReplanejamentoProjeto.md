# 2.5. Reflexão e Replanejamento do Projeto

## Introdução

Inicialmente, o projeto *Meu Aquário* foi planejado para ser desenvolvido em grupo, com a colaboração de até 10 integrantes. Contudo, ao longo do semestre, o grupo acabou sendo desfeito. Diante disso, assumi o desenvolvimento do projeto de forma individual.

Esse acontecimento exigiu um reposicionamento completo do planejamento, com revisão de escopo, refinamento de requisitos e escolhas técnicas para facilitar e se alinhar aos conhecimentos tecnicos individual.

---

## Replanejamento e Revisão de Escopo

A transição de um projeto coletivo para um projeto individual implicou em ajustes fundamentais:

- **Redefinição das funcionalidades**, priorizando as mais relevantes para o funcionamento do sistema.
- **Organização pessoal do fluxo de desenvolvimento**, estruturando as entregas parciais para manter ritmo e coerência.
- **Refinamento dos requisitos**, eliminando ambiguidades e focando no essencial.

O sistema continua com a proposta de ser uma plataforma para aquaristas, porém com um escopo mais viável para execução individual, priorizando recursos como postagens, comentários, login, salvamento de conteúdos e consulta de glossário/wiki.

---

## Mudança das Tecnologias

As tecnologias do projeto passaram por mudanças:

- **Java + Spring (Backend)**  
  Spring oferece uma estrutura robusta e padronizada para aplicações RESTful, com suporte nativo à arquitetura MVC, injeção de dependência e integração com bancos relacionais. A escolha do Java também favorece clareza na modelagem orientada a objetos e sendo uma liguagem conhecida.

- **PostgreSQL (Banco de Dados)**  
  Foi escolhido um SGBD relacional, com boa aderência ao Spring, suporte a constraints e modelagem mais segura para integridade de dados.

- **Angular + TypeScript (Frontend)**  
  Angular permite componentização, roteamento nativo e integração eficiente com APIs REST. A estrutura também facilita a separação entre camadas visuais (componentes) e regras de exibição (serviços e páginas), alinhando com o padrão MVC.

- **Arquitetura MVC**  
  Adotada para garantir separação clara de responsabilidades, favorecendo a manutenção futura e a escalabilidade, mesmo em um projeto inicialmente individual.

  Apesar das escolhas e mudanças das tecnologias, continuará sendo um grande desafio, cheio de novos aprendizados, pois não há um dominio signifativo e conhecimento das mesmas.

---

## Requisitos Atuais do Projeto

Após o replanejamento, os requisitos foram refinados:

### Requisitos Funcionais

- RF01: Permitir que qualquer usuário visualize postagens.
- RF02: Permitir busca por tópicos ou termos específicos.
- RF03: Permitir que usuários autenticados criem postagens.
- RF04: Permitir que usuários autenticados comentem em postagens.
- RF05: Permitir que usuários salvem postagens para consulta posterior.
- RF06: Permitir autenticação de usuários (login e logout).
- RF07: Disponibilizar um glossário de termos técnicos do aquarismo.
- RF08: Disponibilizar uma wiki com informações sobre espécies de peixes.

### Requisitos Não Funcionais

- RNF01: Interface responsiva para dispositivos móveis.
- RNF02: A persistência de dados deve ser garantida com SGBD relacional.
- RNF03: A aplicação deve seguir a arquitetura MVC.
- RNF04: Deve haver separação entre backend (API) e frontend (interface).

---

## Considerações Finais

A decisão de continuar o projeto de forma individual foi desafiadora, mas também representou uma oportunidade de aprendizado profundo. As modelagens dos diagramas realizados, aliada à escolha das tecnologias e à revisão do escopo, mostra que é possível manter a qualidade mesmo diante de contratempos.

---

## Histórico de Versão

| Versão | Alteração                         | Responsável                                | Data       |
|--------|-----------------------------------|--------------------------------------------|------------|
| 1.0    | Criação da seção e escrita do documento | [Brenno Silva](https://github.com/brenno-silva01) | 08/05/2025 |
