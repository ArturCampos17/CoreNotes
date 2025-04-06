
# Core Notes App

O **Core Notes App** é uma aplicação para gerenciar tarefas pessoais ou profissionais. Ele permite criar, editar, excluir, marcar como favorita e alterar o status de tarefas. O sistema também oferece recursos de personalização, como cores para categorizar tarefas, e uma interface responsiva para melhor experiência em dispositivos móveis.

[**Repositorio Back-End**](https://github.com/ArturCampos17/corenotes-backend)

[**Repositorio Front-End** ](https://github.com/ArturCampos17/corenotes-frontend)

## Tecnologias Utilizadas

- **Backend:**
  - Node.js: v22.11.0
  - Express: v4.18.2

- **Frontend:**
  - React: v18.2.0
  - React Router: v6.14.0
  - Axios: v1.5.0

- **Banco de Dados:**
  - MySql 8.0


## Demonstração do Projeto

Assista ao vídeo de demonstração:

[Assistir Video Completo](https://drive.google.com/drive/folders/1JHy8PQoBNVEB2uu-uPDE63wcInSnyDj2?usp=sharing)

Ou veja o GIF abaixo para uma prévia rápida:

![Demonstração](corenote.gif)

## Funcionalidades Principais

1. **Criação de Tarefas:**
   - Adicione tarefas com título e descrição.
   - Marque tarefas como favoritas.
   - Personalize a cor da tarefa.

2. **Gerenciamento de Tarefas:**
   - Edite títulos e descrições.
   - Altere o status da tarefa (pendente, finalizada, cancelada).
   - Exclua tarefas indesejadas.

3. **Interface Responsiva:**
   - Layout adaptável para telas menores (smartphones e tablets).
   - Efeito de hover desativado em dispositivos móveis para melhor usabilidade.

4. **Color Picker:**
   - Escolha entre uma paleta de cores para categorizar visualmente suas tarefas.
   - O color picker é exibido acima de outros elementos e ajusta-se automaticamente em telas menores.

5. **Filtro de tarefas:**
    - As tarefas sempre são filtras na sequencia, Favoritas, Pendentes, Finalizadas e Canceladas, pode utilizar filtro para ver o status desejado.
    - Filtro com Search All, podendo buscar por nome do titulo ou pela descrição da tarefa

6. **Validações de Negócio:**
   - Garante que as regras de negócio sejam seguidas para manter a integridade dos dados.

---

## Regras de Negócio e Validações

As seguintes validações foram implementadas para garantir que o sistema funcione de acordo com as regras de negócio:

### 1. **Título Obrigatório**
   - **Regra:** O título da tarefa é obrigatório.
   - **Validação:** 
     - Um alerta é exibido ao usuário caso o título esteja vazio ao tentar salvar uma tarefa.
     - A submissão do formulário é bloqueada até que o título seja preenchido.

### 2. **Estado de Favorito**
   - **Regra:** Uma tarefa pode ser marcada ou desmarcada como favorita.
   - **Validação:**
     - O estado de "favorito" é armazenado localmente e enviado ao backend no formato `is_favorite` (snake_case) para compatibilidade.
     - O ícone de estrela muda dinamicamente entre preenchido (`FaStar`) e vazio (`FaRegStar`) para refletir o estado atual.

### 3. **Status da Tarefa**
   - **Regra:** Uma tarefa pode ter três estados principais:
     - **Pendente:** Tarefa ativa, permitindo edição, exclusão e outras ações.
     - **Finalizada:** Tarefa concluída, bloqueando edições e outras ações.
     - **Cancelada:** Tarefa cancelada, bloqueando edições e outras ações.
   - **Validação:**
     - Botões de edição, exclusão e marcação como favorita são desabilitados para tarefas com status "finalizada" ou "cancelada".
     - É possível reabrir uma tarefa finalizada ou cancelada, retornando-a ao estado "pendente".


### 4. **Responsividade do Formulário**
   - **Regra:** O formulário deve ser totalmente funcional em dispositivos móveis.
   - **Validação:**
     - O efeito de hover é desativado em dispositivos móveis para evitar conflitos visuais.

### 7. **Persistência de Dados**
   - **Regra:** Os dados devem ser enviados ao backend no formato correto.
   - **Validação:**
     - Todos os campos obrigatórios são validados antes do envio.

---

## Estrutura do Projeto Front - End

```
src/
├── components/
├── FilterBar/
│   │   ├── FilterBar.module.scss
│   │   └── FilterBar.tsx
│   ├── TaskForm/
│   │   ├── TaskForm.tsx
│   │   └── TaskForm.module.scss
│   ├── TaskItem/
│   │   ├── TaskItem.tsx
│   │   └── TaskItem.module.scss
│   └── TaskList/
│       └── TaskList.tsx
├── hooks/
│       └── useTasks.ts
├── App.tsx
├── index.tsx
└── styles/
    └── global.scss
```

### Componentes Principais

- **TaskForm:** Formulário para adicionar ou editar tarefas.
- **TaskItem:** Card individual para exibir e gerenciar uma tarefa.
- **App:** Componente principal que renderiza a lista de tarefas e o formulário.

---

## Tecnologias Utilizadas

- **React:** Framework JavaScript para construção da interface.
- **TypeScript:** Tipagem estática para maior segurança e manutenibilidade.
- **CSS Modules:** Estilização modular para evitar conflitos de classes.
- **React Icons:** Ícones interativos para ações como favoritar, editar e excluir.

---

## Estrutura do Projeto Back - End

```
backend/
  ├── config/
  │   ├── connection.js
  │   └── db.js
  ├── controllers/
  │   └── taskController.js
  ├── models/
  │   └── Task.js
  ├── routes/
  │   └── taskRoutes.js
  └── server.js
```


## **Modo de Execução do Projeto**

Este projeto é composto por duas partes principais: **Backend** e **Frontend**. Ambas precisam ser configuradas e executadas para que o sistema funcione corretamente. Siga as instruções abaixo:

---

### **1. Clonar o Repositório**

Clone o repositório completo para sua máquina local:

```bash
git clone https://github.com/ArturCampos17/corenotes-backend.git
git clone https://github.com/ArturCampos17/corenotes-frontend.git
```

O repositório contém dois diretórios principais:
- `BackEnd`: Contém o código-fonte do backend.
- `frontend`: Contém o código-fonte do frontend.

---

### **2. Configurar o Backend**

#### **a. Navegue até o Diretório `BackEnd`**
```bash
cd BackEnd
```

#### **b. Instale as Dependências**
Instale as dependências necessárias para o backend:
```bash
npm install
```

#### **c. Configure as Variáveis de Ambiente**
- Renomeie o arquivo `.env.example` para `.env`.
- Preencha as variáveis de ambiente conforme necessário (ex.: URL do banco de dados, portas, etc.).

#### **d. Inicie o Servidor**
Inicie o servidor backend:
```bash
npm start
```
O servidor estará disponível em [http://localhost:3001](http://localhost:3001).

---

### **3. Configurar o Frontend**

#### **a. Navegue até o Diretório `frontend`**
Volte ao diretório raiz e entre no diretório `frontend`:
```bash
cd ../frontend
```

#### **b. Instale as Dependências**
Instale as dependências necessárias para o frontend:
```bash
npm install
```

#### **c. Configure a Conexão com o Backend**
Certifique-se de que o frontend esteja configurado para se conectar ao backend. Geralmente, isso é feito em um arquivo de configuração ou diretamente no código do frontend. Por exemplo:
- Verifique o arquivo `src/api.ts` ou similar para garantir que a URL base aponte para [http://localhost:3001](http://localhost:3001).

#### **d. Inicie o Servidor de Desenvolvimento**
Inicie o servidor de desenvolvimento do frontend:
```bash
npm start
```
O frontend estará disponível em [http://localhost:3000](http://localhost:3000).

---

### **4. Acessar o Projeto**

Após iniciar ambos os servidores:
- O frontend estará disponível em [http://localhost:3000](http://localhost:3000).
- O backend estará rodando em [http://localhost:3001](http://localhost:3001).

---

### **5. Testar a Integração**

Para garantir que tudo está funcionando corretamente:
1. Acesse o frontend em [http://localhost:3000](http://localhost:3000).
2. Realize operações básicas (ex.: criar uma tarefa, listar tarefas, etc.) e verifique se o frontend está comunicando-se corretamente com o backend.

---

### **6. Parar os Servidores**

Para parar os servidores:
- No terminal onde o backend está rodando, pressione `Ctrl + C`.
- No terminal onde o frontend está rodando, pressione `Ctrl + C`.

---

### **Dicas Adicionais**

- **Portas Personalizadas:** Se as portas padrão (`3000` para o frontend e `3001` para o backend) estiverem ocupadas, você pode alterá-las nos arquivos de configuração de cada componente.
- **Banco de Dados:** Certifique-se de que o banco de dados (se aplicável) esteja instalado e configurado corretamente no backend.

---

### **Pronto!**
