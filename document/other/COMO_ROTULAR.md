# Dataset Fase 6 — trator x vaca

80 imagens do **Open Images Dataset V5** (Google), licenca CC BY 2.0.
Rastreabilidade completa em `MANIFESTO.csv` (classe, split, arquivo, ID original, resolucao).

## Estrutura

```
dataset/
  train/trator (32)   train/vaca (32)
  val/trator   (4)    val/vaca   (4)
  test/trator  (4)    test/vaca  (4)
```

## Passo 1 — subir para o Google Drive

Crie no seu Drive a pasta `FIAP/fase6/dataset` e suba as tres pastas
(`train`, `val`, `test`) mantendo exatamente essa estrutura. O Colab vai
procurar por esse caminho.

## Passo 2 — rotular no Make Sense (so as 64 de treino)

1. Abra https://www.makesense.ai -> **Get Started**
2. Arraste as **32 imagens de `train/trator`** + as **32 de `train/vaca`** (as 64 de uma vez)
3. Escolha **Object Detection**
4. Em "Create labels", crie exatamente dois rotulos, **nesta ordem**:
   - `0` -> `trator`
   - `1` -> `vaca`
   A ordem importa: ela define o indice da classe no arquivo YOLO.
5. Desenhe uma caixa em volta de cada objeto em cada imagem.
   Se houver varios tratores ou varias vacas na mesma foto, desenhe uma caixa por objeto.
6. **Actions -> Export Annotations -> A .zip package containing files in YOLO format**
7. Descompacte e suba os `.txt` para `FIAP/fase6/labels/train` no Drive.

Repita o processo para `val` (8 imagens) — o YOLO precisa dos rotulos de validacao
para calcular as metricas. As 8 de `test` ficam **sem rotulo**: sao a demonstracao
visual para o cliente.

> Tempo estimado: ~45 min para as 64 de treino, ~5 min para as 8 de validacao.

## Observacao sobre as imagens

A curadoria removeu manualmente imagens ambiguas da base original:
bufalos, bisoes, cabras, ovelhas, ilustracoes, empilhadeiras e fotos onde o
objeto era irreconhecivel. Esse descarte esta documentado no notebook como
parte da etapa de preparacao de dados.
