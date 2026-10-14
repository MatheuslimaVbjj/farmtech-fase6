# Roteiro do vídeo — PBL Fase 6

**Limite: 5 minutos. Alvo: 4min30.** YouTube, visibilidade **Não listado**.
Grave a tela com o notebook já aberto e executado — você vai **rolar e narrar**, não executar.

Legenda: **[TELA]** = o que aparece · **[FALA]** = o que você diz.

---

## 0:00 – 0:25 · Abertura

**[TELA]** Topo do notebook, com o cabeçalho FIAP e seu nome visível.

**[FALA]**
> Oi, sou o Matheus Tavares Lima, RM 572808, grupo 15. Esta é a Fase 6 do projeto
> FarmTech Solutions. A empresa expandiu para visão computacional, e o que eu construí
> aqui é um detector que reconhece dois objetos do contexto rural: trator e vaca.
> Escolhi essas duas classes porque uma representa o ativo mecânico e a outra o ativo
> biológico da fazenda — e porque um modelo que confunde as duas não serve pra nenhuma
> das aplicações.

---

## 0:25 – 1:10 · A base e a curadoria

**[TELA]** Role até a seção 2. Pare na tabela de descartes e depois na grade de imagens.

**[FALA]**
> A base tem 80 imagens do Open Images do Google, sob licença Creative Commons —
> 40 de cada classe, divididas em 32 de treino, 4 de validação e 4 de teste, como o
> enunciado pede.
>
> Essa etapa aqui foi a que mais mexeu no resultado. Eu baixei 150 candidatas e
> **descartei 45 na mão**. O rótulo de texto da base não garante que a imagem sirva:
> vinha búfalo e bisão rotulados como gado, empilhadeira rotulada como trator,
> ilustração, anúncio impresso, e até uma foto de feno sem nenhum animal.
>
> Se eu tivesse treinado com esse ruído, o modelo ia aprender que vaca é qualquer
> bicho de quatro patas no pasto.

---

## 1:10 – 1:45 · Rotulação e verificação

**[TELA]** Seção 3. Mostre a saída da célula de verificação e a figura com as caixas sobrepostas.

**[FALA]**
> Rotulei as 64 imagens de treino no Make Sense, exportando no formato YOLO: uma linha
> por objeto, com as coordenadas normalizadas de zero a um.
>
> Antes de treinar, eu rodo uma verificação automática — confere número de campos,
> intervalo das coordenadas, índice de classe e caixa de área zero. E depois desenho os
> rótulos por cima das imagens, que é a única checagem que pega caixa trocada de classe.
> Rótulo corrompido é a falha mais comum em detecção e a mais silenciosa: a métrica
> não denuncia.

---

## 1:45 – 3:00 · O treino e o resultado que não tem vencedor

**[TELA]** Seção 4, a célula de treino. Depois role até a **tabela comparativa 30 × 60** e deixe parado.

**[FALA]**
> Usei o yolov8n, o menor da família, porque com 64 imagens um modelo maior não acha
> mais sinal, ele decora. Treinei duas vezes: 30 e 60 épocas, sem early stopping, pra
> comparação ser honesta.
>
> E aqui está o resultado mais interessante do trabalho — **não tem vencedor.**
>
> Com 60 épocas a precisão subiu quase 10%, e o mAP de 50 a 95 subiu 15%. Mas o
> **recall caiu 20%**. O modelo ficou conservador: ele desenha caixa melhor, mas deixa
> de achar objeto difícil.
>
> E repara no mAP 50: praticamente não mudou. Se eu tivesse reportado só essa métrica,
> a conclusão seria "treinar mais não mudou nada" — e estaria errada. Por isso declarei
> o mAP de 50 a 95 como métrica principal antes de ver os resultados.
>
> A conclusão que eu entrego pro cliente é essa tabela: pra contar rebanho use o de 30
> épocas, porque perder animal é pior que contar a mais. Pra recorte automático use o
> de 60, porque a caixa é mais justa.

---

## 3:00 – 3:30 · Teste

**[TELA]** Seção 6, a grade com as 8 detecções.

**[FALA]**
> Essas são as 8 imagens de teste, que o modelo nunca viu e que não têm rótulo.
> Oito de oito com a classe correta, todas com caixa em cima do objeto.
> Essa é a demonstração visual pro cliente.

---

## 3:30 – 4:20 · Entrega 2 — as três abordagens

**[TELA]** Role até a tabela comparativa das três abordagens, seção 9.

**[FALA]**
> Na Entrega 2 eu comparei três caminhos sobre a mesma base.
>
> A YOLO padrão, com pesos COCO, acertou 8 de 8 também — **mas tem uma armadilha aqui.**
> Ela nunca disse "trator". Ela disse truck, car, motorcycle, e eu traduzi isso por fora
> somando confianças. Um caminhão de verdade na fazenda viraria trator com a mesma
> confiança. Serve como baseline de custo zero, não como produto.
>
> A CNN que treinei do zero acertou 87,5% e é dez vezes mais rápida — mas ela só diz
> **o que** é a imagem, não diz **onde** está o objeto. Pra esse problema, isso a elimina.
>
> E uma observação honesta: com 8 imagens de teste, cada acerto vale 12,5 pontos.
> Esses números não ordenam as três abordagens, e eu digo isso no notebook em vez de
> fingir uma precisão que não tenho.

---

## 4:20 – 4:45 · Fechamento

**[TELA]** Seção de limitações, depois volte ao topo do README no GitHub.

**[FALA]**
> As limitações estão declaradas: 64 imagens de treino é pouco, as fotos são de banco
> e não de campo, e nenhuma imagem tem trator e vaca juntos — que é justamente a cena
> real de uma fazenda.
>
> O que faria esse modelo ir pra produção, em ordem de impacto: mais dados do domínio
> real, cenas mistas, e validação cruzada.
>
> Está tudo no repositório. Obrigado.

---

## Checagem antes de publicar

- [ ] Duração **abaixo de 5:00**
- [ ] Áudio audível do começo ao fim (teste 30 s antes de gravar tudo)
- [ ] Texto do notebook legível na gravação — aumente o zoom do navegador para ~125%
- [ ] Publicado como **Não listado** (não "Privado" — privado o professor não abre)
- [ ] Link testado em **janela anônima**
- [ ] Link colado no README, no campo `COLE AQUI O LINK DO YOUTUBE`
