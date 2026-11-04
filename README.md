<p align="center">
  <img src="assets/logo.svg" width="420" alt="BrickNext">
</p>

<h1 align="center">BrickNext</h1>

<p align="center">
  <b>NextUI para o TrimUI Brick, com o player de musica AnberTunes embutido.</b><br>
  <i>NextUI for the TrimUI Brick, with the AnberTunes music player built in.</i>
</p>

<p align="center">
  <a href="https://ko-fi.com/retrotiv">Ko-fi</a> ·
  <a href="https://github.com/retrotiv/BrickNEXT/releases">Releases</a>
</p>

---

## Portugues

BrickNext e uma adaptacao do **NextUI** para o **TrimUI Brick**, feita pela retrotiv.
Ele mantem tudo o que o NextUI faz e acrescenta o **AnberTunes**: um player de musica
que toca em segundo plano durante os jogos, com um cartao "tocando agora" que aparece
dentro do menu dos emuladores internos e por cima dos emuladores pesados (PSP, N64,
Dreamcast).

### O que vem junto
- **AnberTunes** integrado (musica no menu e nos jogos, com controle direto).
- Card do player no **menu in-game** dos emuladores internos e, por overlay, no
  **PSP** (OpenGL e Vulkan), **N64** (OpenGL) e **Dreamcast** (OpenGL).
- **Updates travados no repo da retrotiv**: o BrickNext so aceita atualizacoes que a
  gente publicar aqui, pra nada quebrar o que ja funciona.

### Como instalar
1. Baixe a release mais recente em **Releases**.
2. Extraia o conteudo na raiz do cartao de memoria (um cartao so pra isso; comece
   com um cartao vazio formatado em FAT32/exFAT).
3. Coloque o cartao no Brick e ligue: ele se instala sozinho no primeiro boot.
4. Depois, e so colocar suas **BIOS** em `Bios/` e suas **ROMs** em `Roms/`, cada
   uma na pasta do console. (BIOS e ROMs **nao** acompanham o BrickNext.)

> Dica: faca a instalacao num cartao vazio. Nao e preciso ter o NextUI antes.

Depois de instalado, para pegar versoes novas e so abrir **Tools -> BrickNext Update**
com o Wi-Fi ligado. Nao precisa regravar o cartao. Veja [docs/UPDATE.md](docs/UPDATE.md).

## English

BrickNext is a retrotiv adaptation of **NextUI** for the **TrimUI Brick**. It keeps
everything NextUI does and adds **AnberTunes**: a background music player with a
"now playing" card inside the built-in emulators' menu and over the heavy emulators
(PSP, N64, Dreamcast).

### What's included
- **AnberTunes** integrated (music in the menu and in games, with direct controls).
- The player card in the built-in emulators' **in-game menu** and, via overlay, on
  **PSP** (OpenGL and Vulkan), **N64** (OpenGL) and **Dreamcast** (OpenGL).
- **Updates locked to retrotiv's repo**: BrickNext only takes updates we publish
  here, so nothing breaks what already works.

### Install
1. Download the latest build from **Releases**.
2. Extract it to the root of a memory card (use a dedicated card; start from an
   empty FAT32/exFAT card).
3. Put the card in the Brick and power on: it installs itself on first boot.
4. Then add your **BIOS** to `Bios/` and your **ROMs** to `Roms/`, each under its
   console folder. (BIOS and ROMs are **not** included.)

> Tip: install onto an empty card. You do not need NextUI installed first.

Once installed, to get new versions just open **Tools -> BrickNext Update** with Wi-Fi on.
No need to re-flash the card. See [docs/UPDATE.md](docs/UPDATE.md).

---

## Creditos / Credits

BrickNext e construido sobre o **NextUI**, da **LoveRetro**
(<https://github.com/LoveRetro/NextUI>), que por sua vez vem do **MinUI**, de Shaun
Inman. Os emuladores e cores pertencem aos seus autores. Veja [NOTICE](NOTICE).

Licenca **PolyForm Noncommercial 1.0.0** (veja [LICENSE](LICENSE)) - projeto
**nao-comercial**, com os creditos preservados.
