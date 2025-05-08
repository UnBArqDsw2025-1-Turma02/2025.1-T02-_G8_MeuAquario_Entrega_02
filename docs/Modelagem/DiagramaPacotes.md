# Modelagem Organizacional — Diagrama de Pacotes

## Introdução

O diagrama de pacotes é uma diagramação UML usada para mostrar como as partes do sistema estão organizadas. Ele representa as pastas ou camadas do projeto e como elas se relacionam entre si.

No projeto **Meu Aquário**, o diagrama de pacotes foi utilizado para mostrar como é esperado a divisão e organização do sistema, usando como base o padrão **MVC** (Modelo-Visão-Controle). Também para a separação foi considerado que será utilizado as tecnologias Typescript (Linguagem) e Angular (Framework) no frontend  e no backend Java (Linguagem) e Spring (Framework), assim, com o diagrama visa facilitar o entendimento de como o sistema funciona por dentro.

Esse tipo de visualização ajuda muito a entender:
- Por onde os dados passam,
- Qual parte depende da outra,
- E onde cada funcionalidade está localizada.

---

## Métodologia

A estrutura do diagrama segue o que é esperado da organização das pastas do projeto. No backend, usamos as camadas típicas de projetos Spring (controller, service, repository e model). No frontend, mostramos as telas, componentes reutilizáveis e os serviços que conversam com o backend.

Para a elaboração do diagrama de pacotes, foi utilizada a ferramenta draw.io, que oferece recursos visuais intuitivos e compatibilidade com a notação UML, facilitando a criação e edição dos modelos.

Os diagramas elaborados têm como objetivo fornecer uma visão geral e principal da estrutura do sistema, destacando os principais pacotes e como eles se relacionam entre si. Eles não entram em detalhes sobre o que cada pacote contém internamente (como classes específicas, métodos ou atributos), mas sim em como as partes do sistema se comunicam e dependem umas das outras.

Assim é facilitado o entendimento darquitetura do sistema, mostrando como ele está dividido em camadas e como as diferentes partes do projeto interagem entre si. À medida que o projeto for caminhnado, os pacotes poderão ser refinados e detalhados.

---

## Diagrama de Pacotes

<h2 align="center">Visão Geral do Sistema</h2>

<div align="center">
    <img src="assets/DiagramaPacotes01.png" alt="Diagrama Geral de Pacotes">
</div>

<p align="center"><em>Imagem 01 - Pacote geral do sistema com frontend e backend</em></p>
<p align="center"><strong>Autor:</strong> Brenno Silva</p>

---

<h2 align="center">Pacotes Internos e Suas Dependências</h2>

<div align="center">
    <img src="assets/DiagramaPacotes02.png" alt="Diagrama Detalhado de Pacotes">
</div>

<p align="center"><em>Imagem 02 - Estrutura interna dos pacotes frontend e backend</em></p>
<p align="center"><strong>Autor:</strong> Brenno Silva</p>

---

## Detalhamento dos Pacotes

### FrontEnd

| Pacote               | O que faz                | Depende de...                                   |
|----------------------|--------------------------|-------------------------------------------------|
| `frontend.pages`     | Contém as telas principais do sistema, como a página inicial, perfil etc. |  `frontend.components`<br> `frontend.services` |
| `frontend.components`| Contém peças reutilizáveis como botões, caixas de texto, cards etc.       | `frontend.services`  |
| `frontend.services`  | Responsável por se conectar com o backend usando requisições HTTP         | `backend.controller`   |

#### Como o FrontEnd vai se conectar com o BackEnd

- O **frontend.services** faz chamadas HTTP para os **controladores do backend**, pegando e enviando dados como usuários, postagens, comentários etc. Assim temos a ligação `frontend.services` ---> `backend.controller`.

---

### BackEnd

| Pacote               | O que faz                                                                 | Depende de...                             |
|----------------------|---------------------------------------------------------------------------|-------------------------------------------|
| `backend.controller` | Responde às requisições que chegam do frontend                            | `backend.service`<br> `backend.model`  |
| `backend.service`    | Onde ficam as regras de negócio (como "quem pode postar?", "quem edita?") | `backend.repository`<br> `backend.model` |
| `backend.repository` | Cuida de salvar e buscar dados no banco                                   | `backend.model`                          |
| `backend.model`      | Define os dados principais do sistema (usuário, postagem, aquário etc.)   | -----                                    |

---

##  Fluxo de Dependência (do usuário até o banco)

O sistema funciona como uma sequência de interações entre diferentes pacotes. Abaixo, vemos como os pacotes se conectam e como as informações fluem do frontend até o banco de dados.

## Diagrama de Fluxo

```plaintext
[FrontEnd]
   │
   ▼
frontend.pages
   │
   ▼
frontend.components
   │
   ▼                        [BackEnd]
frontend.services  ──► [backend.controller]
                        │
                        ▼
                [backend.service] ──► [backend.repository] ──► [backend.model] ──► [Banco de Dados (PostgreSQL)]
```

## Passo a Passo:

#### 1. Frontend → Backend:
   - O **frontend** exibe as páginas (como a home, perfil, postagens).
   - Os **componentes** são usados para criar as interações da interface.
   - Os **serviços** fazem requisições HTTP para o **controller** no **backend**.

#### 2. Controller → Service:
   - O **backend.controller** recebe as requisições e as passa para o **backend.service**, que contém a lógica de negócios.

#### 3. Service → Repository:
   - O **backend.service** chama o **backend.repository** para acessar o banco de dados, buscando ou salvando dados.

#### 4. Repository → Model:
   - O **backend.repository** interage com o **backend.model**, que define a estrutura dos dados, como usuários, postagens, etc.

#### 5. Banco de Dados:
   - O **backend.repository** comunica-se com o banco de dados (PostgreSQL) para armazenar e recuperar os dados.

---

## Referências Bibliográficas

- UML-DIAGRAMS. The Unified Modeling Language. Disponível em: [https://www.uml-diagrams.org/](https://www.uml-diagrams.org/). Acesso em: 04 maio. 
2025.

- DEVMEDIA. Introdução ao padrão MVC. Disponível em: [https://www.devmedia.com.br/introducao-ao-padrao-mvc/29308](https://www.devmedia.com.br/introducao-ao-padrao-mvc/29308). Acesso em: 05 maio. 2025.

- SERRANO, Milene. **AULA - MODELAGEM UML ESTÁTICA**. [S. l.], 2025. 55 slides. Disponível em: [AULA-MODELAGEM UML ESTÁTICA.pdf](https://aprender3.unb.br/pluginfile.php/3070937/mod_page/content/1/Arquitetura%20e%20Desenho%20de%20Software%20-%20Aula%20Modelagem%20UML%20Est%C3%A1tica%20-%20Profa.%20Milene.pdf). Acesso em:  03 maio. 2025.

## Histórico de Versão
| Versão | Alteração | Responsável | Data       |
|------|--------|-----------|---------|
| 1.0 | Criação do arquivo | [Brenno Silva](https://github.com/brenno-silva01) | 06/05/2025 |
| 1.1 | Adição das descrições dos pacotes | [Brenno Silva](https://github.com/brenno-silva01) | 06/05/2025 |
| 1.2 |  Adição do fluxo de dependência | [Brenno Silva](https://github.com/brenno-silva01) | 06/05/2025 |
| 2.0 | Adição das imagens dos diagramas | [Brenno Silva](https://github.com/brenno-silva01) | 06/05/2025 |
| 2.1 | Ajuste na exibição das imagens | [Brenno Silva](https://github.com/brenno-silva01) | 07/05/2025 | 


