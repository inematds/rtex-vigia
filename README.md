# rtex-vigia

[![rtex-vigia](guia/assets/banner.jpg)](https://inematds.github.io/rtex-vigia/guia/)

**🇧🇷 [Português](README.md) · 🇺🇸 [English](README.en.md) · 🇪🇸 [Español](README.es.md)**

## O que é

O rtex-vigia, ou rtexv, é um formato de vídeo curto e vertical para contar uma notícia ou descoberta em cerca de 2 minutos. Ele serve para quem cria conteúdo e quer explicar algo importante sem perder a pessoa no meio. Aqui você encontra as regras, um modelo de roteiro e exemplos já publicados. Ele não produz o vídeo sozinho: você copia um pedido para a sua IA, recebe o roteiro e depois grava e edita. Para gravar, use o celular ou um avatar, a versão digital de uma pessoa falando.

## 📖 Guia de uso

Guia completo: **https://inematds.github.io/rtex-vigia/guia/**

## Comece pedindo à sua IA

Cole este pedido no Claude, no ChatGPT ou em outra IA que consiga ler páginas da internet:

```text
Quero um roteiro de reel no formato rtex-vigia.

Regras do formato:
- Cerca de 2 minutos no meu ritmo de fala, em 7 a 10 blocos curtos.
- Sequência: gancho com o fato mais forte, falando com "você"; uma prova logo no início; a história, com como começou e o que estava travado; a virada, explicada com uma comparação simples; o limite do assunto, quando houver; e o fecho, com uma moral, o convite para o meu site ou perfil e uma pergunta de verdade.
- Visual: manchete curta, legenda de 2 ou 3 palavras por vez, imagens realistas e números grandes. Nas imagens, nunca gere com IA o rosto de outra pessoa real.

Se conseguir abrir, veja estes exemplos. Se não conseguir, me avise e siga só as regras acima:
https://github.com/inematds/rtex-vigia/blob/main/exemplos/cirurgia-raio-x/roteiro.md
https://github.com/inematds/rtex-vigia/blob/main/exemplos/so-tres-ferramentas/roteiro.md
https://github.com/inematds/rtex-vigia/blob/main/exemplos/ia-sem-internet/roteiro.md

Antes de escrever, me pergunte e espere as respostas:
1. Qual é o assunto?
2. Quais fatos eu já apurei e de onde vieram?
3. Para quem é o vídeo?
4. Para qual site ou perfil quero levar as pessoas?
5. Vou falar em ritmo normal ou acelerado?
6. Tenho um texto meu ou a transcrição de um áudio para você copiar meu jeito de falar?

Depois escreva o roteiro com palavras próprias e na minha voz, em texto corrido, bloco por bloco, e diga o tempo estimado de leitura.
Em cada bloco, liste as telas: a manchete, o número em destaque, se houver, e uma imagem que eu possa usar legalmente, dizendo onde buscar.
Confira números e datas em fontes confiáveis e me mostre os links. Se não conseguir pesquisar na internet, avise e não invente fontes nem links. O que eu apurei e não estiver na internet, mantenha e marque como "apuração própria" para eu confirmar. Se algo for contrariado por uma fonte, me avise antes de mudar.
Não publique nada e não altere nenhum arquivo sem o meu sim.
```

## O formato em três partes

| Parte | O que define |
|---|---|
| **Técnico** | Vídeo vertical 1080 x 1920, cerca de 2 minutos, fala rápida e algo mudando na tela a cada 2 ou 3 segundos |
| **Visual** | Abertura com manchete e pessoa em meia tela, depois imagem cheia com rosto no canto, legenda curta e números grandes |
| **Roteiro** | Gancho, prova cedo, história, virada, pé no chão e fecho com pergunta |

Detalhes e medidas: [formato/FORMATO.md](formato/FORMATO.md).

## Exemplos publicados

| Vídeo | Roteiro |
|---|---|
| [Cirurgião com visão de raio-x](https://www.youtube.com/shorts/kqNiaEvGtTQ) | [roteiro](exemplos/cirurgia-raio-x/roteiro.md) |
| [Só 3 ferramentas de IA](https://www.youtube.com/shorts/r5FoW7NjTqE) | [roteiro](exemplos/so-tres-ferramentas/roteiro.md) |
| [IA mesmo sem internet](https://www.youtube.com/shorts/KHcn1nvT_g0) | [roteiro](exemplos/ia-sem-internet/roteiro.md) |

---

## O processo, do início ao fim

🧠 = sessão com pessoa e IA · ⚙️ = script · 🤖 = IA executando sozinha

| # | Passo | Comando ou ação | Quem |
|---|---|---|---|
| 1 | Escolher o fato e o público | Definir a dor ou o desejo de quem vai assistir | 🧠 |
| 2 | Criar o roteiro | `bin/rtexv novo roteiros/meu-tema.json` | ⚙️ |
| 3 | Escrever os blocos | Preencher o arquivo seguindo `formato/FORMATO.md` | 🧠 |
| 4 | Conferir os fatos | Checar cada número e data em fonte confiável | 🧠 |
| 5 | Conferir o formato | `bin/rtexv checar roteiros/meu-tema.json` | ⚙️ |
| 6 | Gravar | Câmera ou avatar. Na INEMA, o [explicavideos](https://github.com/inematds/explicavideos) cuida do avatar | 🧠 |
| 7 | Montar | Na INEMA, o explicavideos no perfil viral, em 9:16 | 🤖 |
| 8 | Publicar | Na INEMA, a fila do [yt-pub-x3](https://github.com/inematds/yt-pub-x3) | ⚙️ |

## Instalação técnica

Precisa de Python 3.9 ou mais novo, sem outras dependências.

```bash
git clone https://github.com/inematds/rtex-vigia.git
cd rtex-vigia
bin/rtexv novo roteiros/meu-tema.json
bin/rtexv checar roteiros/meu-tema.json
bin/rtexv checar roteiros/meu-tema.json --destino meusite.com
```

`checar` sai com `0` quando aprova, `1` quando reprova e `2` quando não consegue ler o arquivo. Ele confere de 7 a 10 blocos, 1.800 a 2.700 caracteres de fala, duração estimada, gancho no início, virada no meio e site citado no fecho.

| Caminho | Conteúdo |
|---|---|
| `formato/FORMATO.md` | Regras completas e medidas |
| `formato/regras.json` | Limites usados pelo `rtexv` |
| `modelo/roteiro.json` | Modelo para copiar, com versão em texto em `roteiro.md` |
| `exemplos/` | Roteiros de vídeos publicados, em JSON e em texto |
| `bin/rtexv` | Conferidor de roteiros |
| `tests/` | Testes |
| `guia/` | Guia em português, inglês e espanhol |

Testes: `python3 -m unittest discover -s tests`

## Licença

[MIT](LICENSE)
