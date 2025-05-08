# Modelagem Dinâmica - Diagramas de Atividades

## Introdução

O diagrama de atividades é um artefato da UML utilizado para representar o fluxo de controle de processos, destacando as ações, decisões e a sequência lógica das operações realizadas em um sistema. Ele é ideal para ilustrar a dinâmica das funcionalidades, mostrando tanto o comportamento do sistema quanto as interações do usuário de forma clara e sequencial.

No projeto *Meu Aquário*, a modelagem de atividades foi realizada com o objetivo de representar as principais funcionalidades interativas do sistema, com foco nas ações mais relevantes para os usuários, que são as funções de realizar postagem, fazer um comentário e login. Por meio dos diagramas, é possível visualizar os passos necessários para executar uma ação, as validações envolvidas e os caminhos alternativos, facilitando o entendimento e a implementação dos requisitos.

## Metodologia

A construção dos diagramas de atividades foi baseada na análise direta dos fluxos funcionais do sistema, levando em consideração os requisitos identificados nas fases iniciais de desenvolvimento. Para isso, descrevemos passo a passo as interações mais relevantes realizadas pelos usuários, bem como os comportamentos esperados do sistema em resposta a essas ações.

Foi utilizado a notação UML padrão com os elementos:
- **Nós de início e fim**
- **Ações** (em forma de verbos no infinitivo)
- **Decisões** (condições com caminhos “Sim” e “Não”)
- **Fluxo sequencial** com setas direcionais

Os diagramas foram elaborados na ferramenta draw.io, mantendo o alinhamento com a notação formal da UML e prezando pela clareza visual e didática.

---

## Diagramas de Atividades

<h2 align="center">Criar Postagem</h2>

<div align="center">
    <img src="./assets/DiagramaAtividadePostagem.png" alt="Diagrama de Atividade - Criar Postagem">
</div>

<p align="center"><em>Imagem 01 - Fluxo de criação de postagem</em></p>
<p align="center"><strong>Autor:</strong> Brenno Silva</p>

Este diagrama representa o fluxo da funcionalidade "criar postagem". Ele demosntra que para realizar uma postagem o usuário deve estar logado no sistema, e se durante o processo tudo estiver correto é exibido a confirmação de publicação. Há também ramificações opcionais (como o anexo de mídias) e condicionais (como validação dos dados). O fluxo demonstra claramente os caminhos alternativos, como a ausência de login.

**Fluxo da Atividade:**

1. Início  
2. Criar postagem
3. Verificar se o usuário está logado
    - Se não estiver logado: É redirecionado para a tela de login
    - se estiver logado: Irá para a tela de criação de postagem   
4. Exibir tela de criação de postagem  
5. Preencher título e conteúdo da postagem  
6. Verificar se o usuário deseja anexar mídias  
    - Se sim: Selecionar imagens ou vídeos 
    - se não: Já pode enviar a postagem 
7. Enviar a postagem  
8. Validar os dados preenchidos  
    - Se inválidos: Exibir mensagem de erro e depois é redirecionado para o tópico 5.  
    - Se válidos: É exibido a confimação da postagem    
9. Exibir confirmação da postagem  
10. Fim

---

<h2 align="center">Comentar em Postagem</h2>

<div align="center">
    <img src="./assets/DiagramaAtividadeComentario.png" alt="Diagrama de Atividade - Comentar">
</div>

<p align="center"><em>Imagem 02 - Fluxo de comentário em uma postagem</em></p>
<p align="center"><strong>Autor:</strong> Brenno Silva</p>

O diagrama descreve o processo em que um usuário interage com uma postagem existente através de um comentário. Mostra a verificação de login, entrada de texto, envio, validação e exibição. Também cobre os fluxos alternativos em caso de erro de validação ou ausência de login.

**Fluxo da Atividade:**

1. Início
2. Realizar comentário
3. Verificar se o usuário está logado  
   - Se não estiver logado: redirecionar para tela de login 
   - Se estiver logado: O usário tem permição para fazer comentários
4. Permitir o usuário realizar comentários  
5. Digitar o conteúdo do comentário  
6. Enviar o comentário  
7. Validar o conteúdo do comentário  
   - Se inválido: Exibir mensagem de erro e depois redirecionado para o tópico 5.
   - se válido: É publicado o comentário
8. Publicar comentário  
9. Exibir o novo comentário na postagem  
10. Fim

---

<h2 align="center">Realizar Login</h2>

<div align="center">
    <img src="./assets/DiagramaAtividadeLogin.png" alt="Diagrama de Atividade - Login">
</div>

<p align="center"><em>Imagem 03 - Fluxo de autenticação de usuário</em></p>
<p align="center"><strong>Autor:</strong> Brenno Silva</p>

Este diagrama apresenta o fluxo completo da autenticação de um usuário. Inclui desde o preenchimento do formulário até a verificação das credenciais e o redirecionamento em caso de sucesso. Também faz a verifcação se os campos preenchidos estão corretos.

**Fluxo da Atividade:**

1. Início  
2. Exibir tela de login  
3. Usuário preenche e-mail e senha  
4. Usuário envia o formulário  
5. O sistema valida os campos preenchidos  
   - Se inválidos: Exibir mensagem de erro e redireciona para o tópico 2.
   - se válidos: Passa para a verificação das credenciais  
6. O sistema verifica se as credenciais estão corretas  
   - Se incorretas: exibir erro de autenticação e redireciona para o tópico 2. 
   - Se corretas: autenticar o usuário e criar sessão/token  
7. Redirecionar para a página principal  
8. Fim

---

## Referências Bibliográficas

- UML-DIAGRAMS. The Unified Modeling Language. Disponível em: [https://www.uml-diagrams.org/activity-diagrams-overview.html](https://www.uml-diagrams.org/activity-diagrams-overview.html). Acesso em: 06 maio. 2025.

- SERRANO, Milene. **AULA - MODELAGEM UML DINÂMICA**. [S. l.], 2025. 28 slides. Disponível em: [AULA-MODELAGEM UML DINÂMICA.pdf](https://aprender3.unb.br/pluginfile.php/3070938/mod_page/content/1/Arquitetura%20e%20Desenho%20de%20Software%20-%20Aula%20Modelagem%20UML%20Din%C3%A2mica%20-%20Profa.%20Milene.pdf). Acesso em:  03 maio. 2025.

- LUCIDCHART. O que é diagrama de atividades UML?. Disponível em: [https://www.lucidchart.com/pages/pt/o-que-e-diagrama-de-atividades-uml](https://www.lucidchart.com/pages/pt/o-que-e-diagrama-de-atividades-uml). Acesso em: 07 maio. 2025.

- IBM. Criando Diagramas de Atividades. Disponível em: [https://www.ibm.com/docs/pt-br/rational-soft-arch/9.7.0?topic=diagrams-creating-activity](https://www.ibm.com/docs/pt-br/rational-soft-arch/9.7.0?topic=diagrams-creating-activity). Acesso em: 07 maio. 2025.

---

## Histórico de Versão

| Versão | Alteração                                    | Responsável                                | Data       |
|--------|-----------------------------------------------|--------------------------------------------|------------|
| 1.0    | Criação do documento                          | [Brenno Silva](https://github.com/brenno-silva01) | 07/05/2025 |
| 2.0    | Adição do conteúdo textual da página    | [Brenno Silva](https://github.com/brenno-silva01) | 07/05/2025 |
| 2.1    | Adição das imagens do diagrama    | [Brenno Silva](https://github.com/brenno-silva01) | 08/05/2025 |
| 2.2    | Ajustando referências bibliográficas    | [Brenno Silva](https://github.com/brenno-silva01) | 08/05/2025 |
| 3.0    | Adição de descrição do fluxo das atividades    | [Brenno Silva](https://github.com/brenno-silva01) | 08/05/2025 |

