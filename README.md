<p align="center"><a href="https://laravel.com" target="_blank"><img src="https://raw.githubusercontent.com/laravel/art/master/logo-lockup/5%20SVG/2%20CMYK/1%20Full%20Color/laravel-logolockup-cmyk-red.svg" width="400" alt="Laravel Logo"></a></p>

# Boilerplate Profissional

![Laravel](https://img.shields.io/badge/Laravel-11-FF2D20?style=for-the-badge&logo=laravel&logoColor=white)
![PHP](https://img.shields.io/badge/PHP-8.2%2B-777BB4?style=for-the-badge&logo=php&logoColor=white)
![PostgreSQL 16](https://img.shields.io/badge/PostgreSQL-16-336791?style=for-the-badge&&logo=postgresql&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)

[![Build Status](https://github.com/angelluzk/laravel-v11/actions/workflows/laravel.yml/badge.svg)](https://github.com/angelluzk/laravel-v11/actions)
![Code Style](https://img.shields.io/badge/Code%20Style-Laravel%20Pint-blue)
![Static Analysis](https://img.shields.io/badge/Static%20Analysis-Larastan-yellow)

> **Starter moderno e “Enterprise-Ready” com Docker Compose V2, ferramentas de QA, análise estática, testes e CI/CD configurados.**

---

## 📋 Sobre o Projeto

Este repositório fornece uma fundação sólida para projetos em **Laravel 11**, com foco em qualidade, padronização, testes e automação.  
Tudo já configurado para um ambiente profissional e escalável, ideal tanto para estudos quanto para uso corporativo.

---

## 🛠️ Tecnologias e Recursos

- **Framework:** Laravel 11  
- **Linguagem:** PHP 8.2+  
- **Banco de Dados:** PostgreSQL 16 (Docker)  
- **Ambiente de Desenvolvimento:** Laravel Sail (Docker Compose V2)  
- **Code Style:** Laravel Pint (PSR-12)  
- **Análise Estática:** Larastan (PHPStan – Level 5)  
- **CI/CD:** GitHub Actions  
- **Extras:** IDE Helper, Redis, Mailpit

---

## 🚀 Instalação

### ⚙️ Requisitos do Ambiente (php.ini)

Caso você opte por rodar o projeto **sem Docker** (instalação nativa), garanta que as seguintes extensões estejam habilitadas no seu arquivo `php.ini`:

- `ctype`
- `curl`
- `dom`
- `fileinfo`
- `filter`
- `hash`
- `mbstring`
- `openssl`
- `pcre`
- `pdo`
- `pdo_pgsql` (Driver do Banco de Dados)
- `session`
- `tokenizer`
- `xml`

> **Nota:** Se você estiver usando **Laravel Sail (Docker)**, pode ignorar esta lista. O container já vem com todas essas extensões configuradas e otimizadas automaticamente.

---

### 1. Clone o Repositório
```bash
git clone https://github.com/SEU-USUÁRIO/laravel-v11.git
cd laravel-v11
```

### 2. Instale as Dependências

#### Opção A — Composer Local

```bash
composer install
```

#### Opção B — Composer via Docker

```bash
docker run --rm -u "$(id -u):$(id -g)" \
  -v "$(pwd):/var/www/html" -w /var/www/html \
  laravelsail/php82-composer:latest \
  composer install --ignore-platform-reqs
```

### 3. Configure o Ambiente

```bash
cp .env.example .env
./vendor/bin/sail up -d
```

Garanta no `.env`:

```
DB_CONNECTION=pgsql
DB_PORT=5432
```

### 4. Setup Final

```bash
./vendor/bin/sail artisan key:generate
./vendor/bin/sail artisan migrate
```

Aplicação disponível em:
**[http://localhost](http://localhost)**

---

## 🛡️ Qualidade e Ferramentas de QA

### 🎨 Formatação — Laravel Pint

```bash
./vendor/bin/sail bin pint
```

### 🔎 Análise Estática — Larastan

```bash
./vendor/bin/sail bin phpstan analyse
```

### 🧪 Testes Automatizados

```bash
./vendor/bin/sail artisan test
```

### 🧠 Atualizar IDE Helper

```bash
./vendor/bin/sail artisan ide-helper:generate
```

---

## 🤖 CI/CD — GitHub Actions

O workflow `laravel.yml` executa automaticamente:

1. Verificação de padrão de código (Pint)
2. Análise estática (Larastan)
3. Testes completos

Tudo isso ao enviar alterações para a branch `main`.

---

## 📂 Arquivos Importantes

* **compose.yaml** — Serviços Docker (App, DB, Redis, Mailpit)
* **phpstan.neon** — Regras do PHPStan / Larastan
* **pint.json** — Configurações do Laravel Pint
* **.editorconfig** — Padronização entre editores

---

## 📚 Documentação Adicional
Quer entender profundamente as ferramentas usadas neste projeto?  
Leia a [Documentação de Conceitos Técnicos](./CONCEITOS_TECNICOS.md).

---

## 👩‍🎓 Autoria

<img src="https://github.com/angelluzk.png" width="100px;" alt="Foto de Angel Luz"/>

> Desenvolvido com 💛 por **Angel Luz**.

Se quiser conversar, colaborar ou oferecer uma oportunidade:

📬 E-mail: [contatoangelluz@gmail.com](mailto:contatoangelluz@gmail.com)  
🐙 GitHub: [@angelluzk](https://github.com/angelluzk)  
💼 LinkedIn: [linkedin.com/in/angelitaluz](https://www.linkedin.com/in/angelitaluz/)  
🗂️Website / Portfólio: [meu_portfolio/](https://angelluzk.github.io/meu_portfolio/) 

-----

<div align="center">

> “Transformando código em fluxo, e ideias em movimento.”

</div>