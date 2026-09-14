#  Sistema de Gerenciamento de Funcionários (PHP + MySQL + Tailwind CSS)

Um sistema **CRUD** (Create, Read, Update, Delete) completo e responsivo para gerenciamento de funcionários, construído em PHP nativo utilizando declarações preparadas (`MySQLi`), banco de dados relacional e interface estilizada com **Tailwind CSS**.

---

## Funcionalidades

* **Gerenciamento Completo de Funcionários:** Criar, listar, visualizar, editar e remover registros.
* **Upload de Fotos de Perfil:** Envio e armazenamento de fotos no formulário de cadastro/edição, com substituição automática de arquivos antigos e suporte a formatos de imagem (`jpg`, `jpeg`, `png`, `webp`).
* **Relacionamento no Banco de Dados:** Vinculação entre Funcionários e Setores da empresa por meio de **Chave Estrangeira** (`FOREIGN KEY`) e consultas otimizadas com `INNER JOIN`.
* **Segurança:** Utilização de *Prepared Statements* (Instruções Preparadas) para prevenção contra ataques de **SQL Injection** e sanitização com `htmlspecialchars`.
* **Interface Moderna:** Design limpo, responsivo e intuitivo utilizando **Tailwind CSS** e **FontAwesome**.

---

##  Tecnologias Utilizadas

* **Linguagem:** PHP 8.x
* **Banco de Dados:** MySQL / MariaDB
* **Conexão de Dados:** MySQLi (Procedural / Prepared Statements)
* **Estilização:** Tailwind CSS (via CDN)
* **Ícones:** FontAwesome 6

---

##  Estrutura do Banco de Dados

 O sistema utiliza duas tabelas relacionadas:

1. **`setores`**: Armazena os departamentos da empresa.
2. **`funcionarios`**: Armazena os dados do funcionário, caminho da foto de perfil e possui a chave estrangeira `setor_id`.

```sql
CREATE TABLE setores (
    id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(100) NOT NULL
);

CREATE TABLE funcionarios (
    id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(100) NOT NULL,
    endereco VARCHAR(255) NOT NULL,
    salario INT(10) NOT NULL,
    foto VARCHAR(255) DEFAULT 'default-avatar.png',
    setor_id INT NOT NULL,
    FOREIGN KEY (setor_id) REFERENCES setores(id)
);
