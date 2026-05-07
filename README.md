# Mod NSP Maker — Como Usar / How to Use

> ⚠️ **Disclaimer / Aviso**
>
> 🇺🇸 This tool is intended for **educational and personal use only**. Users are solely responsible for complying with local laws and respecting intellectual property rights. The developers are not responsible for any misuse of this software. This project is **not affiliated with Nintendo Co., Ltd.** or any game publisher. **Freeware — not for commercial use.**
>
> 🇧🇷 Esta ferramenta destina-se apenas ao **uso educacional e pessoal**. Os usuários são os únicos responsáveis pelo cumprimento das leis locais e pelo respeito aos direitos de propriedade intelectual. Os desenvolvedores não se responsabilizam por qualquer uso indevido deste software. Este projeto **não possui afiliação com a Nintendo Co., Ltd.** ou qualquer editora de jogos. **Freeware — não é para uso comercial.**

---

## 🇧🇷 Português

**Mod NSP Maker** é um app desktop para Windows que empacota mods de Nintendo Switch em arquivos `.nsp` auto-instaladores. Quando instalado no Switch, o NSP copia os arquivos do mod para os locais corretos no cartão SD automaticamente — sem gerenciamento manual de arquivos.

### Requisitos

| Item | Observações |
|---|---|
| Windows 10/11 (64-bit) | Necessário para rodar o `.exe` |
| Nintendo Switch com CFW | Atmosphere recomendado |
| Arquivos do mod | As pastas que você quer instalar |

### Configuração

1. Coloque `ModNSPMaker.exe` em qualquer pasta do PC.
2. Dê duplo clique para abrir.

### Guia Passo a Passo

#### Aba Configuração

| Campo | O que preencher |
|---|---|
| **Ícone do NSP** | Uma imagem JPG de 256×256 — será o ícone exibido no menu do Switch. Outros tamanhos são auto-convertidos ao importar. |
| **Nome** | Título que aparece no menu do Switch (ex: `Zelda Mod Pack`) |
| **Publicador** | Seu nome ou grupo (ex: `CostelaBR`) |
| **Versão** | Versão exibida no Switch (ex: `1.0.0`) |

#### Aba Mods

Clique em **➕ Adicionar** para criar uma entrada de mod. Cada mod possui:

| Campo | Descrição |
|---|---|
| **Nome do Mod** | Rótulo interno (não aparece no Switch) |
| **TID do Jogo** | Title ID hex de 16 caracteres do jogo (ex: `0100B2D023548000`) |
| **Pastas do Mod** | Um ou mais mapeamentos de pasta → destino no SD |
| **Update NSP** | *(Opcional)* Arquivo `.nsp` de update a instalar junto |
| **Instalar Update NSP** | Marque para instalar o update |
| **Auto-deletar installer** | Marque para remover o NSP do Switch após instalar |

#### Mapeamentos de Pasta — como os destinos funcionam

Cada mapeamento liga uma **pasta de origem no PC** a um **caminho de destino no SD** (`sdmc:/`).

| Destino no SD | O que acontece |
|---|---|
| *(vazio)* | Os **conteúdos** da pasta são copiados para a **raiz do SD** (`sdmc:/`) |
| `atmosphere/contents` | A pasta vai para `sdmc:/atmosphere/contents/<nome-da-pasta>/` |
| `atmosphere/exefs_patches` | Mesma lógica |
| Qualquer caminho | Relativo a `sdmc:/`, com barras normais |

**Exemplo — mod típico do Atmosphere:**
```
Pasta de origem:  C:\Mods\BotW\0100509005AF3000
Destino no SD:    atmosphere/contents
→ Resultado:      sdmc:/atmosphere/contents/0100509005AF3000/
```

**Exemplo — arquivos na raiz do SD:**
```
Pasta de origem:  C:\Mods\BotW\SaveFiles
Destino no SD:    (vazio)
→ Resultado:      sdmc:/ (conteúdo copiado diretamente)
```

Você pode adicionar **múltiplos mapeamentos por mod** — útil quando o mod tem arquivos que vão para locais diferentes.

#### Aba Compilar

1. Defina a **Pasta de Saída**.
2. Clique em **🚀 Compilar Mod NSP**.
3. Ao terminar, um diálogo mostra o caminho do `.nsp` gerado.

### Instalando no Switch

1. Copie o `.nsp` gerado para o SD do Switch (qualquer local).
2. Abra seu instalador de NSP preferido (ex: **Tinfoil**, **DBI**) e instale-o.
3. O novo título aparece no menu do Switch.
4. Abra-o — o instalador roda automaticamente, copia os arquivos e se deleta (se configurado).

### Dicas

- **Encontrando o TID do jogo:** Use o [SwitchBrew](https://switchbrew.org/wiki/Title_list) ou Tinfoil. Sempre o TID base (termina em `000`).
- **Auto-conversão de ícone:** Qualquer formato é aceito; o app converte para JPG 256×256.
- **Múltiplos mods em um NSP:** Adicione várias entradas — todos instalados por um único NSP.
- **Idioma:** Clique na bandeira (🇧🇷 / 🇺🇸) no canto superior direito para alternar.

### Resolução de Problemas

| Problema | Solução |
|---|---|
| Ícone rejeitado | Use JPG; PNG é auto-convertido ao importar |
| Switch mostra publicador desconhecido | Preencha o campo Publicador antes de compilar |
| Arquivos do mod no lugar errado | Verifique o Destino no SD no mapeamento |

### Licença

Freeware distribuído sob [CC BY-NC-ND 4.0](https://creativecommons.org/licenses/by-nc-nd/4.0/) — gratuito para uso e compartilhamento na forma original; sem modificações, sem uso comercial. Não possui afiliação com a Nintendo Co., Ltd. Veja [LICENSE.md](LICENSE.md).

---

## 🇺🇸 English

**Mod NSP Maker** is a Windows desktop app that packages Nintendo Switch mods into self-installing `.nsp` files. Once installed on the Switch, the NSP copies mod files to the correct SD card locations automatically — no manual file management needed.

### Requirements

| Item | Notes |
|---|---|
| Windows 10/11 (64-bit) | Required to run the `.exe` |
| Nintendo Switch with CFW | Atmosphere recommended |
| Mod files | The folders you want to install |

### Setup

1. Place `ModNSPMaker.exe` anywhere on your PC.
2. Double-click to launch.

### Step-by-Step Guide

#### Settings tab

| Field | What to fill |
|---|---|
| **NSP Icon** | A 256×256 JPG image — becomes the icon on the Switch home screen. Other sizes are auto-converted on import. |
| **Name** | Title shown on the Switch home menu (e.g. `Zelda Mod Pack`) |
| **Publisher** | Your name or group (e.g. `CostelaBR`) |
| **Version** | Version string shown on the Switch (e.g. `1.0.0`) |

#### Mods tab

Click **➕ Add** to create a mod entry. Each mod has:

| Field | Description |
|---|---|
| **Mod Name** | Internal label (not shown on Switch) |
| **Game TID** | 16-character hex Title ID of the game (e.g. `0100B2D023548000`) |
| **Mod Folders** | One or more folder → SD destination mappings |
| **Update NSP** | *(Optional)* An `.nsp` update file to install alongside the mod |
| **Install Update NSP** | Check to install the update |
| **Auto-delete installer** | Check to remove the NSP from the Switch after install |

#### Folder Mappings — how destinations work

Each mapping links a **source folder on your PC** to a **destination path on the SD card** (`sdmc:/`).

| SD Destination | What happens |
|---|---|
| *(empty)* | **Contents** of the source folder are copied to the **SD root** (`sdmc:/`) |
| `atmosphere/contents` | The folder is placed at `sdmc:/atmosphere/contents/<folder-name>/` |
| `atmosphere/exefs_patches` | Same logic |
| Any custom path | Relative to `sdmc:/`, forward slashes |

**Example — a typical Atmosphere mod:**
```
Source folder:  C:\Mods\BotW\0100509005AF3000
SD Destination: atmosphere/contents
→ Result on SD: sdmc:/atmosphere/contents/0100509005AF3000/
```

**Example — copying files to SD root:**
```
Source folder:  C:\Mods\BotW\SaveFiles
SD Destination: (leave empty)
→ Result on SD: sdmc:/ (contents copied directly)
```

You can add **multiple mappings per mod** — useful when a mod has files going to different locations.

#### Build tab

1. Set the **Output Folder**.
2. Click **🚀 Build Mod NSP**.
3. When done, a dialog shows the path to the generated `.nsp`.

### Installing on the Switch

1. Copy the generated `.nsp` to your Switch SD card (any location).
2. Open your NSP installer (e.g. **Tinfoil**, **DBI**) and install it.
3. The new title appears on the Switch home menu.
4. Launch it — the installer runs automatically, copies the files, and deletes itself (if configured).

### Tips

- **Finding a game's Title ID:** Use [SwitchBrew](https://switchbrew.org/wiki/Title_list) or Tinfoil's title list. Always use the base game TID (ends in `000`).
- **Icon auto-conversion:** Any format is accepted; the app converts to 256×256 JPG automatically.
- **Multiple mods in one NSP:** Add more than one entry — all installed by a single NSP.
- **Language:** Click the flag button (🇺🇸 / 🇧🇷) in the top-right corner to toggle.

### Troubleshooting

| Problem | Solution |
|---|---|
| Icon rejected | Use a JPG; PNG is auto-converted on import |
| Switch shows unknown publisher | Fill the Publisher field before building |
| Mod files not in the right place | Double-check the SD Destination path in the mapping |

### License

Freeware distributed under [CC BY-NC-ND 4.0](https://creativecommons.org/licenses/by-nc-nd/4.0/) — free to use and share in original form; no modification, no commercial use. Not affiliated with Nintendo Co., Ltd. See [LICENSE.md](LICENSE.md).

---

*Mod NSP Maker — CostelaBR 2026*
