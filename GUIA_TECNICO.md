# 📘 Documentação Técnica

Este documento descreve as decisões técnicas, ferramentas, padrões e configurações utilizadas na construção deste repositório Laravel Profissional.

---

## 1. Estrutura Docker Moderna (`compose.yaml`)

Este projeto utiliza o arquivo **`compose.yaml`**, seguindo a especificação moderna recomendada pela Docker Inc.

- **Por que não `docker-compose.yml`?**  
  A nomenclatura antiga permanece funcional, mas o Docker adotou `compose.yaml` como padrão oficial e atualizado.
  
- **Impacto no projeto:**  
  As versões recentes do Laravel Sail (especialmente com PHP 8.4+) já geram automaticamente este formato.  
  A funcionalidade permanece a mesma, mas com maior aderência às convenções do ecossistema Docker.

---

## 2. Dependências e Comandos de Instalação

### ✔️ Criar o Projeto Laravel
```bash
composer create-project laravel/laravel:^11.0 laravel-v11
```

* **Motivo:**
  Garante a instalação da versão major (11.x), evitando versões instáveis (`dev`) ou versões antigas.

### ✔️ Instalar Ferramentas de Desenvolvimento

```bash
composer require --dev larastan/larastan barryvdh/laravel-ide-helper
```

* **Flag `--dev`:**
  As dependências serão usadas apenas no ambiente local, não indo para produção (mais segurança e eficiência).

#### Funções das Ferramentas:

* **Larastan (PHPStan):**
  Fornece análise estática, identificando bugs lógicos, inconsistências de tipagem e chamadas inválidas antes mesmo da execução.

* **Laravel IDE Helper:**
  Gera arquivos auxiliares para IDEs como VS Code compreenderem corretamente Facades, relacionamentos Eloquent, macros e métodos “mágicos”.

---

## 3. Arquivos de Padronização e Qualidade (QA)

### 📄 `.editorconfig`

* Garante padronização entre diferentes editores.
* Configura indentação padrão do projeto (4 espaços).
* Regras específicas para YAML (`compose.yaml`) usando 2 espaços.

### 📄 `pint.json`

* Configura o **Laravel Pint**, responsável pela padronização automática do código.
* Mantém o estilo de acordo com PSR-12 e convenções do Laravel.

### 📄 `phpstan.neon`

* Configurações do Larastan.
* **Level 5** aplicado propositalmente:

  * Rigor suficiente para detectar problemas reais.
  * Sem se tornar excessivamente burocrático.

---

## 4. Automação via `composer.json`

Foi adicionada uma automação via **scripts Composer**:

* Sempre que o comando `composer update` é executado, o **IDE Helper** é regenerado automaticamente.
* Benefícios:

  * Autocomplete sempre atualizado.
  * Melhoria significativa na Developer Experience (DX).
  * Evita erros comuns ao trabalhar com Models, Facades e rotas.

---

## 5. Integração Contínua (GitHub Actions)

O workflow `.github/workflows/laravel.yml` implementa uma pipeline sólida de CI que executa:

1. **Checkout:** Clona o repositório.
2. **Configuração do PHP:** Instala a versão necessária no runner.
3. **Qualidade (QA):**

   * Laravel Pint
   * Larastan
     *Se qualquer um falhar, o build é interrompido.*
4. **Testes Automatizados:**
   Executa toda a suíte (Pest ou PHPUnit).

### Benefícios:

* Evita regressões.
* Impede que código fora do padrão entre na branch `main`.
* Automatiza validação contínua do projeto.

---