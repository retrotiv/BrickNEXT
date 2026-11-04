# Atualizar o BrickNext pelo proprio aparelho

A partir da primeira instalacao, voce **nao precisa regravar o cartao** para pegar uma
versao nova. O aparelho busca a atualizacao neste repositorio pelo Wi-Fi e aplica so na
parte do BrickNext do cartao.

> **O que a atualizacao nunca toca:** a **memoria interna** do aparelho. O atualizador se
> recusa a rodar se nao conseguir provar que esta escrevendo no cartao do BrickNext e em
> mais lugar nenhum.

## Como atualizar (para quem usa)

1. Conecte o aparelho ao **Wi-Fi**.
2. Abra **Tools -> BrickNext Update**.
3. Ele confere a ultima versao, baixa, confere o checksum e aplica. Leva um minuto.
4. Quando disser que atualizou, **reinicie** o aparelho. Pronto.

Se ja estiver na versao mais nova, ele avisa e nao faz nada. Se nao houver internet, ele
avisa e nao faz nada.

---

## Como publicar uma versao (para quem mantem o projeto)

Uma release do BrickNext pode ter **duas coisas**:

- **Pacote de atualizacao** (`bricknext-<tag>-update.tar` + `.tar.sha256`), o arquivo leve
  que o aparelho baixa. Contem so a camada do BrickNext (`.system/tg5040`, `Tools/tg5040`,
  `Emus/tg5040`, ou so os arquivos que mudaram). E um `.tar` de proposito: o aparelho abre
  com um busybox embutido, sem depender de `unzip`/`gzip` (que o Brick nao tem).
- **Distribuicao completa** (`BrickNext-<tag>.zip`), para quem vai instalar do zero: extrai
  na raiz de um cartao vazio (FAT32/exFAT) e o aparelho se instala no primeiro boot. Ver o
  [README](../README.md).

### 1. Gerar o pacote de atualizacao

A partir de um cartao (ou de uma arvore de build) que tenha a pasta `.system/tg5040`:

```bash
tools/make-update-package.sh v1.0.1 /caminho/para/o/cartao ./dist
```

Para uma correcao leve, liste so os caminhos que mudaram:

```bash
tools/make-update-package.sh v1.0.1 /caminho/para/o/cartao ./dist \
  .system/tg5040/bin/minarch.elf "Emus/tg5040/PSP.pak"
```

Isso gera em `./dist` o `bricknext-v1.0.1-update.tar` e o `.tar.sha256`. Dentro do tar vao
o `bricknext-release.txt` (a tag, que o aparelho confere) e o `MANIFEST.sha256` (checksum
de cada arquivo, que o aparelho tambem confere).

### 2. Criar a release no GitHub

```bash
gh release create v1.0.1 \
  ./dist/bricknext-v1.0.1-update.tar \
  ./dist/bricknext-v1.0.1-update.tar.sha256 \
  --repo retrotiv/BrickNEXT \
  --title "BrickNext v1.0.1" \
  --notes-file docs/release-notes/v1.0.1.md
```

> A distribuicao completa (`BrickNext-<tag>.zip`, ~316 MB) entra na mesma release quando a
> versao tambem muda o firmware que vive dentro do `MinUI.zip` - assim quem instala do zero
> ja pega a versao nova. Para uma correcao que so troca arquivos soltos (paks, launchers), o
> pacote `.tar` sozinho basta.

### 3. Rota de atualizacao

O aparelho olha **apenas** para `retrotiv/BrickNEXT` (configurado em
`Tools/tg5040/BrickNext Update.pak`). Nao usamos o auto-update de origem do NextUI; toda
atualizacao do BrickNext passa por aqui. Isso e de proposito: mantem tudo dentro da
estrutura do aparelho e evita conflito com o projeto de origem.

### Etiqueta de versao no aparelho

O aparelho guarda a versao instalada em `.system/tg5040/bricknext-release.txt` (ex.:
`v1.0.0`). O atualizador le esse arquivo para saber se ja esta atualizado, e o reescreve
ao aplicar uma versao nova. A distribuicao completa ja vem com essa etiqueta carimbada
dentro do `MinUI.zip`.
