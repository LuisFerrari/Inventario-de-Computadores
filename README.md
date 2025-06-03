# Inventario-de-Computadores# 

---

## Descrição do Projeto

Este é um sistema web simples desenvolvido em PHP e MySQL para gerenciar o inventário de computadores em um ambiente corporativo. Ele permite registrar, visualizar, editar e excluir informações sobre os equipamentos, incluindo dados como nome da máquina, departamento, usuário responsável, datas de manutenção e uma descrição. O sistema também possui um recurso de alerta visual para computadores que estão há mais de 6 meses sem manutenção.

## Funcionalidades

* **Listagem de Computadores:** Visualize todos os equipamentos cadastrados em uma tabela organizada.
* **Cadastro de Novos Equipamentos:** Adicione novos computadores ao inventário com facilidade.
* **Edição de Registros:** Atualize as informações de computadores existentes.
* **Exclusão de Registros:** Remova computadores do inventário.
* **Alerta de Manutenção:** Linhas destacadas na tabela para equipamentos com manutenção pendente (última manutenção há mais de 6 meses).
* **Funcionalidade de Busca:** Pesquise por máquina, departamento ou usuário para encontrar rapidamente um equipamento.

## Tecnologias Utilizadas

* **Backend:** PHP
* **Banco de Dados:** MySQL
* **Frontend:** HTML5, CSS3
* **Ícones:** Font Awesome

---

## Como Configurar e Rodar o Projeto

Siga os passos abaixo para configurar e executar este projeto em seu ambiente local.

### Pré-requisitos

Certifique-se de ter os seguintes softwares instalados:

* **Servidor Web:** Apache ou Nginx (com PHP instalado e configurado)
* **Banco de Dados:** MySQL / MariaDB
* **PHP:** Versão 7.4 ou superior

Recomendo o uso de um ambiente como **XAMPP**, **WAMP Server** ou **Laragon** para facilitar a configuração do ambiente PHP e MySQL.

### 1. Clonar o Repositório

```bash
git clone [https://github.com/SeuUsuario/NomeDoSeuRepositorio.git](https://github.com/SeuUsuario/NomeDoSeuRepositorio.git)
cd NomeDoSeuRepositorio


### 2. Configurar o Banco de Dados
Crie um banco de dados MySQL chamado inventario_ti (ou o nome que preferir) e importe o esquema inicial.

Você pode criar o banco de dados e as tabelas manualmente ou executar o seguinte script SQL:

SQL

-- Exemplo de script SQL para criar a tabela 'computadores'
-- Salve isso como 'database.sql' na raiz do seu projeto e importe.

CREATE DATABASE IF NOT EXISTS inventario_ti;

USE inventario_ti;

CREATE TABLE IF NOT EXISTS computadores (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nome_maquina VARCHAR(255) NOT NULL,
    departamento VARCHAR(255) NOT NULL,
    nome_usuario VARCHAR(255) NOT NULL,
    ultima_manutencao DATE NOT NULL,
    proxima_manutencao DATE NOT NULL,
    descricao TEXT,
    data_cadastro TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);



-- Exemplo de inserção de dados (opcional)
INSERT INTO computadores (nome_maquina, departamento, nome_usuario, ultima_manutencao, proxima_manutencao, descricao) VALUES
('CPU-001', 'TI', 'João Silva', '2024-01-15', '2024-07-15', 'Desktop principal do suporte'),
('NOTE-005', 'Vendas', 'Maria Santos', '2024-03-20', '2024-09-20', 'Notebook para apresentações'),
('SERV-WEB01', 'Infraestrutura', 'Pedro Costa', '2023-10-01', '2024-04-01', 'Servidor web da aplicação interna');


### 3. Configurar a Conexão com o Banco de Dados
Edite o arquivo php/conexao.php com suas credenciais do banco de dados:

PHP

<?php
$servername = "localhost"; // Geralmente 'localhost'
$username = "seu_usuario_mysql"; // Seu usuário do MySQL
$password = "sua_senha_mysql"; // Sua senha do MySQL
$dbname = "inventario_ti"; // O nome do banco de dados que você criou

// Cria a conexão
$conn = new mysqli($servername, $username, $password, $dbname);

// Verifica a conexão
if ($conn->connect_error) {
    die("Falha na conexão: " . $conn->connect_error);
}
?>
Lembre-se de substituir seu_usuario_mysql e sua_senha_mysql pelas suas credenciais reais.

### 4. Posicionar os Arquivos no Servidor Web
Mova a pasta NomeDoSeuRepositorio para o diretório raiz do seu servidor web (por exemplo, htdocs no XAMPP, www no WAMP ou public no Laragon).

### 5. Acessar o Sistema
Abra seu navegador e acesse:

http://localhost/NomeDoSeuRepositorio/index.php
