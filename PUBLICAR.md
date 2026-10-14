# Como subir no GitHub — passo a passo

> Estrutura conforme o template oficial da FIAP (`agodoi/templateFiapVfinal`).

---

## 1 · Criar o repositório no GitHub

1. Acesse https://github.com/new
2. **Repository name:** `farmtech-fase6`
3. **Visibility:** **Public** — o barema exige repositório público
4. **NÃO marque** "Add a README file", "Add .gitignore" nem "Choose a license" —
   esta pasta já traz todos eles
5. **Create repository**

## 2 · Gerar o token de acesso (só uma vez)

O GitHub não aceita mais a senha da conta no terminal. Você precisa de um
**Personal Access Token**:

1. https://github.com/settings/tokens
2. **Generate new token** → **Generate new token (classic)**
3. **Note:** `fiap` · **Expiration:** 90 days
4. **Marque o escopo `repo`** (a primeira caixa — ela seleciona as de baixo junto)
5. **Generate token**
6. Copie o token (começa com `ghp_`). **Ele só aparece uma vez.**

## 3 · Enviar

Abra o Terminal **dentro desta pasta** e rode:

```bash
git init -b main
git add .
git commit -m "PBL Fase 6 - FarmTech: visao computacional com YOLO"
git remote add origin https://github.com/MatheuslimaVbjj/farmtech-fase6.git
git push -u origin main
```

Quando pedir:

| Campo | O que digitar |
|---|---|
| Username | `MatheuslimaVbjj` |
| Password | o token `ghp_...` (o Terminal não mostra nada enquanto você cola — é normal) |

### Erros comuns

| Erro | Solução |
|---|---|
| `remote origin already exists` | `git remote set-url origin https://github.com/MatheuslimaVbjj/farmtech-fase6.git` e repita o push |
| `src refspec main does not match any` | o commit não passou — rode `git status` e confira |
| `Authentication failed` | o token está errado ou sem o escopo `repo` — gere outro |

---

## 4 · Conferir no navegador

- [ ] Repositório está **Public**
- [ ] **Logo da FIAP** aparece no topo do README
- [ ] As **quatro imagens** do README carregam (amostras, rótulos, detecções)
- [ ] `src/MatheusTavaresLima_rm572808_pbl_fase6.ipynb` abre e mostra **as 7 figuras**
- [ ] Tabelas do README renderizando certo

## 5 · Gravar o vídeo

Roteiro cronometrado em [`document/other/ROTEIRO_VIDEO.md`](./document/other/ROTEIRO_VIDEO.md).

- [ ] Duração **abaixo de 5:00**
- [ ] Publicado no YouTube como **Não listado** (não "Privado" — privado o professor não abre)
- [ ] Link testado em **janela anônima**

## 6 · Colar o link e entregar

Edite o `README.md` (pode ser pelo próprio GitHub, no ícone de lápis) e troque
`COLE AQUI O LINK DO YOUTUBE (não listado)` pelo link real.

Pelo terminal:

```bash
git add README.md
git commit -m "Adiciona link do video demonstrativo"
git push
```

Depois poste o link do repositório no portal da FIAP. Pode ser dentro de um PDF,
como você fez na Fase 5.

## 7 · Congelar

**Nenhum commit depois de entregar.** O barema penaliza explicitamente.

---

## O que vai e o que não vai no repositório

| | |
|---|---|
| **Vai** | notebook executado, README, pesos treinados, métricas, documentação |
| **Não vai** | as 80 imagens do dataset |

As imagens ficam fora porque o `.gitignore` do padrão FIAP ignora binários de dados.
Elas estão no zip `dataset_fase6_trator_vaca.zip` e devem ir para o seu Google Drive,
em `MyDrive/FIAP/fase6/dataset`, conforme pede o enunciado.

O `src/data/MANIFESTO.csv` mantém a rastreabilidade: cada imagem pode ser reconduzida ao
identificador original no Open Images. Academicamente isso é mais defensável do que
versionar cópias das imagens.
