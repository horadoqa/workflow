# Workflow no GitHub Actions

O objetivo de criar um workflow no GitHub Actions é automatizar tarefas do seu projeto sempre que algum evento acontecer (push, pull request, schedule, release, etc).

Em outras palavras:

> ⚙️ Você ensina o GitHub a trabalhar automaticamente para você.

Evita o clássico:

> “Na minha máquina funciona 🤡”

## Como criar ???

Aqui está um exemplo simples de como criar um **workflow básico no GitHub Actions** para rodar um script Python com:

```python
print("Hello World !!!")
```

---

## 📁 1️⃣ Estrutura do projeto

Seu repositório deve ter esta estrutura:

```
meu-projeto/
│
├── hello.py
└── .github/
    └── workflows/
        └── python-app.yml
```

---

## 🐍 2️⃣ Criando o script Python

Crie o arquivo **`hello.py`**:

```python
print("Hello World !!!")
```

---

## ⚙️ 3️⃣ Criando o Workflow do GitHub Actions

Crie o arquivo:

```
.github/workflows/python-app.yml
```

Com o seguinte conteúdo:

```yaml
name: Python Hello World

on:
  push:
    branches: [ "main" ]

  pull_request:
    branches: [ "main" ]

  schedule:
    - cron: "0 12 * * *"  # 09:00 BRT (12:00 UTC)

jobs:
  run-python:
    runs-on: ubuntu-latest

    steps:
    - name: Checkout do código
      uses: actions/checkout@v4

    - name: Configurar Python
      uses: actions/setup-python@v5
      with:
        python-version: "3.11"

    - name: Executar script
      run: python hello.py
```

---

## 🚀 4️⃣ Como funciona

* `on:` → Define quando o workflow será executado (push, PR na branch main ou com schedule)
* `runs-on:` → Define o sistema operacional (Ubuntu Linux)
* `actions/checkout` → Baixa o código do repositório
* `actions/setup-python` → Instala a versão do Python
* `run:` → Executa o comando no terminal

---

## ▶️ 5️⃣ Executando

1. Faça commit e push para o GitHub.
2. Vá na aba **Actions** do seu repositório.
3. Você verá o workflow rodando.
4. Ao abrir o job, verá o log com:

```
Hello World !!!
```

---

## 🧠 Resumindo

Criar um workflow serve para:

| Sem GitHub Actions       | Com GitHub Actions         |
| ------------------------ | -------------------------- |
| Fazer tudo manualmente   | Automático                 |
| Esquecer de rodar testes | Testes sempre rodam        |
| Deploy manual            | Deploy automático          |
| Erros em produção        | Problemas detectados antes |

---

## Mesmo sendo simples, aprendemos:

* Como configurar ambiente
* Como rodar script automaticamente
* Como agendar execução
* Como integrar com eventos do repositório

Isso já é a base de CI/CD.

---