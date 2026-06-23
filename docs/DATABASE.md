# FleetOps - Database Modeling

## 📋 Visão Geral

Este documento descreve o modelo de dados inicial do sistema FleetOps.

---

# Entidades

## Role

Representa o perfil de acesso de um usuário.

### Campos

| Campo      | Tipo        | Restrições |
|------------|------------ |------------|
| id         | UUID        | PK         |
| name       | VARCHAR(50) | UNIQUE     |
| created_at | TIMESTAMP   | NOT NULL   |
| updated_at | TIMESTAMP   | NOT NULL   |

### Valores iniciais

- ADMIN
- USER

### Relacionamentos

- 1 perfil pode estar associado a N usuários

## User

Representa um usuário autenticado na plataforma.

### Campos

| Campo      | Tipo         | Restrições |
| ---------- | ------------ | ---------- |
| id         | UUID         | PK         |
| role_id    | UUID         | FK         |
| name       | VARCHAR(100) | NOT NULL   |
| email      | VARCHAR(255) | UNIQUE     |
| password   | VARCHAR(255) | NOT NULL   |
| created_at | TIMESTAMP    | NOT NULL   |
| updated_at | TIMESTAMP    | NOT NULL   |

### Relacionamentos

* 1 usuário pode possuir N veículos

---

## Vehicle

Representa um veículo gerenciado pela plataforma.

### Campos

| Campo        | Tipo         | Restrições |
| ------------ | ------------ | ---------- |
| id           | UUID         | PK         |
| user_id      | UUID         | FK         |
| plate        | VARCHAR(10)  | UNIQUE     |
| manufacturer | VARCHAR(100) | NOT NULL   |
| model        | VARCHAR(100) | NOT NULL   |
| year         | INTEGER      | NOT NULL   |
| mileage      | BIGINT       | NOT NULL   |
| status       | VARCHAR(30)  | NOT NULL   |
| created_at   | TIMESTAMP    | NOT NULL   |
| updated_at   | TIMESTAMP    | NOT NULL   |

### Status

* ACTIVE
* MAINTENANCE
* INACTIVE

### Relacionamentos

* N veículos pertencem a 1 usuário
* 1 veículo possui N abastecimentos
* 1 veículo possui N manutenções

---

## Fuel Record

Representa um abastecimento realizado.

### Campos

| Campo      | Tipo          | Restrições |
| ---------- | ------------- | ---------- |
| id         | UUID          | PK         |
| vehicle_id | UUID          | FK         |
| fuel_date  | DATE          | NOT NULL   |
| liters     | DECIMAL(10,2) | NOT NULL   |
| total_cost | DECIMAL(10,2) | NOT NULL   |
| mileage    | BIGINT        | NOT NULL   |
| created_at | TIMESTAMP     | NOT NULL   |
| updated_at | TIMESTAMP     | NOT NULL   |

### Relacionamentos

* N abastecimentos pertencem a 1 veículo

---

## Maintenance Record

Representa uma manutenção realizada.

### Campos

| Campo            | Tipo          | Restrições |
| ---------------- | ------------- | ---------- |
| id               | UUID          | PK         |
| vehicle_id       | UUID          | FK         |
| maintenance_type | VARCHAR(30)   | NOT NULL   |
| description      | TEXT          | NOT NULL   |
| cost             | DECIMAL(10,2) | NOT NULL   |
| maintenance_date | DATE          | NOT NULL   |
| created_at       | TIMESTAMP     | NOT NULL   |
| updated_at       | TIMESTAMP     | NOT NULL   |

### Tipos

* PREVENTIVE
* CORRECTIVE

### Relacionamentos

* N manutenções pertencem a 1 veículo

---

# Diagrama Conceitual

User (1)
|
+-- Vehicle (N)
|
+-- FuelRecord (N)
|
+-- MaintenanceRecord (N)

---

# Convenções

## Chaves Primárias

Todas as entidades utilizarão:

* UUID

## Auditoria

Todas as entidades possuirão:

* created_at
* updated_at

Futuramente poderão ser adicionados:
* deleted_at

## Nomenclatura

### Tabelas

* roles
* users
* vehicles
* fuel_records
* maintenance_records

### Colunas

Padrão:

snake_case

Exemplos:

* created_at
* maintenance_date
* total_cost
