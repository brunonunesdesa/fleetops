# FleetOps - Product Requirements Document (PRD)

## 📋 Visão Geral

**Nome do Produto:** FleetOps

**Versão:** MVP v1.0

**Status:** Em desenvolvimento

### Objetivo

O FleetOps é uma plataforma web para gerenciamento de frotas que permite controlar veículos, abastecimentos, manutenções e indicadores operacionais em uma única aplicação.

---

## 🚨 Problema

Empresas que possuem frotas frequentemente utilizam planilhas ou sistemas fragmentados para gerenciar suas operações.

Isso gera dificuldades em:

* Controle de custos operacionais
* Acompanhamento de manutenções
* Monitoramento dos veículos
* Geração de relatórios e indicadores

---

## 🎯 Público-Alvo

* Gestores de frota
* Supervisores operacionais
* Pequenas transportadoras
* Empresas com veículos próprios

---

## 🏆 Objetivos do MVP

O MVP deverá permitir que um usuário:

* Crie uma conta
* Faça login no sistema
* Cadastre veículos
* Registre abastecimentos
* Registre manutenções
* Visualize indicadores operacionais

---

# ⚙️ Funcionalidades

## 🔐 Autenticação

### Cadastro de Usuário

**Descrição:**

Permitir o cadastro de novos usuários.

**Campos:**

| Campo  | Tipo  | Obrigatório |
| ------ | ----- | ----------- |
| Nome   | Texto | Sim         |
| E-mail | Texto | Sim         |
| Senha  | Texto | Sim         |

### Login

**Descrição:**

Permitir autenticação utilizando e-mail e senha.

---

## 🚚 Gestão de Veículos

### Cadastro de Veículo

**Campos:**

| Campo         | Tipo   |
| ------------- | ------ |
| Placa         | Texto  |
| Fabricante    | Texto  |
| Modelo        | Texto  |
| Ano           | Número |
| Quilometragem | Número |
| Status        | Enum   |

### Status disponíveis

* Ativo
* Em manutenção
* Inativo

### Operações

* Criar veículo
* Editar veículo
* Excluir veículo
* Listar veículos

---

## ⛽ Gestão de Abastecimentos

### Campos

| Campo         | Tipo       |
| ------------- | ---------- |
| Veículo       | Referência |
| Data          | Data       |
| Litros        | Decimal    |
| Valor Total   | Decimal    |
| Quilometragem | Número     |

### Operações

* Registrar abastecimento
* Editar abastecimento
* Excluir abastecimento
* Consultar histórico

---

## 🔧 Gestão de Manutenções

### Campos

| Campo     | Tipo       |
| --------- | ---------- |
| Veículo   | Referência |
| Tipo      | Enum       |
| Data      | Data       |
| Descrição | Texto      |
| Custo     | Decimal    |

### Tipos de manutenção

* Preventiva
* Corretiva

### Operações

* Registrar manutenção
* Editar manutenção
* Excluir manutenção
* Consultar histórico

---

## 📊 Dashboard

### Indicadores

* Total de veículos
* Veículos ativos
* Veículos em manutenção
* Total gasto com combustível
* Total gasto com manutenção

### Gráficos

* Gastos por mês
* Status da frota
* Evolução dos custos

---

# 🔒 Requisitos Não Funcionais

## Segurança

* Autenticação JWT
* Senhas criptografadas com BCrypt

## Performance

* Paginação nas consultas
* Consultas otimizadas

## Escalabilidade

* Backend Stateless
* Arquitetura REST

## Infraestrutura

* Docker
* Docker Compose
* PostgreSQL

---

# 🛠️ Stack Tecnológica

## Backend

* Java 21
* Spring Boot 3
* Spring Security
* Spring Data JPA
* Flyway

## Frontend

* React
* TypeScript
* Vite
* Material UI

## Banco de Dados

* PostgreSQL

## DevOps

* Docker
* GitHub Actions

---

# 🚀 Roadmap

## Fase 1

* Autenticação
* Cadastro de usuários

## Fase 2

* Gestão de veículos

## Fase 3

* Gestão de abastecimentos

## Fase 4

* Gestão de manutenções

## Fase 5

* Dashboard

## Fase 6

* Deploy
* CI/CD
* Testes automatizados
