Matemágica

> **Transforme o ensino de matemática em uma aventura.**

A **Matemágica** é uma plataforma educacional gamificada, especialmente desenvolvida para auxiliar professores no ensino de matemática para crianças com **Transtorno do Espectro Autista (TEA)**. O projeto visa tornar o aprendizado inclusivo, lúdico e intuitivo através de uma interface amigável e mecânicas de jogos.

---

## 🚀 Funcionalidades

A plataforma divide-se em perfis de utilizador distintos (**Professores** e **Alunos**) e oferece as seguintes funcionalidades principais:

* **Gestão de Utilizadores:** Autenticação e perfis diferenciados para professores e alunos.
* **Salas de Aula (Classrooms):** Professores podem criar e gerir turmas, adicionando alunos e descrições personalizadas.
* **Gestão de Tarefas (Tasks):** Criação de exercícios de matemática com diferentes níveis de dificuldade e conteúdos.
* **Gamificação e Progresso:** Acompanhamento do desempenho dos alunos com pontuações (*scores*), número de tentativas e estados de conclusão (*"Not Started"*, *"Completed"*, etc.).
* **IA Generativa:** Integração com a **Google Gemini API** para funcionalidades avançadas.

---

## 🛠️ Tecnologias Utilizadas

O projeto utiliza uma arquitetura moderna baseada em microsserviços containerizados:

### Frontend (`matemagica-clientes`)
* **Framework:** Vue.js 3
* **Build Tool:** Vite
* **Estilização:** Tailwind CSS
* **Gestão de Estado:** Pinia
* **Requisições HTTP:** Axios

### Backend (`matemagica-servidor`)
* **Runtime:** Node.js
* **Framework:** Express.js
* **Base de Dados:** PostgreSQL (via `pg`)
* **Segurança:** Helmet, Cors, Bcrypt, JSON Web Token (JWT)
* **IA:** Google Generative AI (`@google/genai`)

### Infraestrutura
* **Docker & Docker Compose:** Orquestração dos serviços (DB, Backend, Frontend).

---

## 📦 Como Rodar o Projeto

### Pré-requisitos
* **Docker** e **Docker Compose** instalados na sua máquina.

### Passos

1.  **Clone o repositório:**
    ```bash
    git clone [https://github.com/seu-usuario/matemagica.git](https://github.com/seu-usuario/matemagica.git)
    cd matemagica
    ```

2.  **Variáveis de Ambiente:**
    O ficheiro `docker-compose.yml` espera uma variável de ambiente para a API do Gemini. Crie um ficheiro `.env` na raiz ou exporte a variável no terminal antes de rodar:

    ```bash
    export GEMINI_API_KEY=sua_chave_api_aqui
    ```

    > **Nota:** As credenciais da base de dados (`admin`/`password123`) já estão configuradas por defeito no `docker-compose` para ambiente de desenvolvimento.

3.  **Inicie os serviços:**
    ```bash
    docker-compose up -d
    ```
    Isto irá iniciar três contentores:
    * `matemagica-db`: Base de dados PostgreSQL (Porta **5432**)
    * `matemagica-backend`: Servidor Node.js (Porta **3000**)
    * `matemagica-frontend`: Aplicação Vue.js (Porta **8082**)

4.  **Aceder à Aplicação:**
    * **Frontend:** Aceda a [http://localhost:8082](http://localhost:8082) no seu navegador.
    * **Backend API:** Disponível em [http://localhost:3000](http://localhost:3000).

---

## 🗄️ Estrutura da Base de Dados

O banco de dados é inicializado automaticamente com o script `init.sql` e contém as seguintes tabelas principais:

* `users`: Armazena dados de login, tipo de utilizador (professor/aluno) e preferências visuais.
* `classroom`: Salas de aula geridas por professores.
* `tasks`: Tarefas e atividades criadas para as turmas.
* `task_progress`: Registo do progresso, tentativas e pontuação dos alunos em cada tarefa.

---

### Desenvolvido por
**Pedro Marineli**
