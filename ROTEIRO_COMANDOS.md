# Roteiro de Comandos — Manual de Sobrevivência (Gitflow)

> **Autor:** Victor E. Pereira — 1º DS — ETEC Boituva
>
> **Objetivo:** Reproduzir do zero um repositório modelo demonstrando o fluxo completo de Gitflow (feature branches, merge com `--no-ff`, publicação em `main`, hotfix).
>
> **Pré-requisitos:** Git instalado, conta no GitHub, terminal aberto.

> **Observação:** Neste repositório, o fluxo foi executado individualmente para simular o trabalho de uma equipe usando Gitflow.

---

## 📁 PASSO 1 — Configuração Inicial

```bash
# Criar a pasta do projeto e entrar nela
mkdir manual-sobrevivencia
cd manual-sobrevivencia

# Iniciar o repositório Git
git init

# Criar o arquivo guia.md com o título principal
echo "# Manual de Sobrevivência do 1º Ano Técnico" > guia.md

# Adicionar e fazer o primeiro commit
git add guia.md
git commit -m "chore: commit inicial do manual"

# Criar o repositório no GitHub (GitHub CLI)
gh repo create manual-sobrevivencia --public --source=. --remote=origin

# Enviar para o GitHub
git branch -M main
git push -u origin main
```

> Sem `gh`? Crie no site e execute:
> ```bash
> git remote add origin https://github.com/SEU_USUARIO/manual-sobrevivencia.git
> git push -u origin main
> ```

---

## 🌿 PASSO 2 — Criação da Branch develop

```bash
git checkout -b develop
git push -u origin develop
```

---

## 🚀 PASSO 3 — Capítulo 1 (feature/dicas-prazos)

```bash
git checkout develop
git checkout -b feature/dicas-prazos
```

Editar `guia.md` e adicionar:

```markdown
## Capítulo 1: Dicas para não esquecer os prazos das tarefas

- Use um aplicativo de agenda (Google Calendar, Notion) para registrar prazos.
- Anote tudo no caderno assim que o professor falar a data de entrega.
- Coloque alarmes no celular 2 dias antes de cada prova ou trabalho.
```

```bash
git add guia.md
git commit -m "feat: adicionado capitulo 1 - dicas de prazos"
git push -u origin feature/dicas-prazos

git checkout develop
git merge --no-ff feature/dicas-prazos -m "Merge pull request: feature/dicas-prazos -> develop"
git push origin develop
```

---

## 🚀 PASSO 4 — Capítulo 2 (feature/mochila-aula-tecnica)

```bash
git checkout develop
git pull origin develop
git checkout -b feature/mochila-aula-tecnica
```

Editar `guia.md` e adicionar:

```markdown
## Capítulo 2: O que levar na mochila nos dias de aula técnica

- Pendrive ou HD externo para salvar projetos do laboratório.
- Fone de ouvido para assistir tutoriais sem atrapalhar os colegas.
- Caderno de anotações para rascunhar lógica antes de programar.
```

```bash
git add guia.md
git commit -m "feat: adicionado capitulo 2 - mochila aula tecnica"
git push -u origin feature/mochila-aula-tecnica

git checkout develop
git merge --no-ff feature/mochila-aula-tecnica -m "Merge pull request: feature/mochila-aula-tecnica -> develop"
git push origin develop
```

---

## 🚀 PASSO 5 — Capítulo 3 (feature/lanches-perto)

```bash
git checkout develop
git pull origin develop
git checkout -b feature/lanches-perto
```

Editar `guia.md` e adicionar (versão original — antes do hotfix):

```markdown
## Capítulo 3: Onde encontrar os melhores salgados perto da escola

- Cantina da Dona Maria: coxinha por R$5,00 e pastel por R$4,50.
- Padaria do Zé (50m da escola): pão de queijo quentinho a R$3,00.
- Trailer do Carlos: misto quente grande por R$7,00 no intervalo.
```

```bash
git add guia.md
git commit -m "feat: adicionado capitulo 3 - lanches perto da escola"
git push -u origin feature/lanches-perto

git checkout develop
git merge --no-ff feature/lanches-perto -m "Merge pull request: feature/lanches-perto -> develop"
git push origin develop
```

---

## 🚀 PASSO 6 — Capítulo 4 (feature/regras-trabalho-equipe)

```bash
git checkout develop
git pull origin develop
git checkout -b feature/regras-trabalho-equipe
```

Editar `guia.md` e adicionar:

```markdown
## Capítulo 4: Regras de ouro para trabalhar em equipe sem treta

- Divida as tarefas de forma justa logo no primeiro dia do trabalho.
- Use um grupo no WhatsApp só para avisos do projeto (sem memes!).
- Se alguém não fizer a parte, converse antes de reclamar pro professor.
```

```bash
git add guia.md
git commit -m "feat: adicionado capitulo 4 - regras de trabalho em equipe"
git push -u origin feature/regras-trabalho-equipe

git checkout develop
git merge --no-ff feature/regras-trabalho-equipe -m "Merge pull request: feature/regras-trabalho-equipe -> develop"
git push origin develop
```

---

## 🏁 PASSO 7 — Publicação: develop → main

```bash
git checkout main
git merge --no-ff develop -m "release: publicacao do manual v1.0"
git tag -a v1.0 -m "Versao 1.0 do manual"
git push origin main --tags
```

---

## 🚑 PASSO 8 — Hotfix (ajuste-cantina)

O professor avisou: a cantina mudou de dono e os preços subiram!

```bash
git checkout main
git checkout -b hotfix/ajuste-cantina
```

Editar `guia.md` no Capítulo 3, trocando:

```
- Cantina da Dona Maria: coxinha por R$5,00 e pastel por R$4,50.
```

por:

```
- Cantina da Dona Ana: coxinha por R$6,50 e pastel por R$5,00.
```

```bash
git add guia.md
git commit -m "fix: atualiza nome e precos da cantina (hotfix)"
git push -u origin hotfix/ajuste-cantina

# Merge do hotfix para main
git checkout main
git merge --no-ff hotfix/ajuste-cantina -m "Merge hotfix/ajuste-cantina -> main"
git tag -a v1.0.1 -m "Hotfix v1.0.1 - ajuste cantina"
git push origin main --tags

# Merge do hotfix para develop (para não perder a correção)
git checkout develop
git merge --no-ff hotfix/ajuste-cantina -m "Merge hotfix/ajuste-cantina -> develop"
git push origin develop
```

---

## ✅ Resultado esperado

- `main` contém o manual completo com a cantina corrigida.
- `develop` está alinhada com `main`.
- As branches `feature/*` e `hotfix/ajuste-cantina` ficam no histórico do repositório como registro do processo.
- O histórico exibe merges com `--no-ff`, deixando visível o fluxo Gitflow.
