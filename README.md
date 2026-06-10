# NSP Mod Maker

> **Disclaimer / Aviso**
>
> This tool is intended for educational and personal use only. Users are solely responsible for complying with local laws and respecting intellectual property rights. Not affiliated with Nintendo Co., Ltd. Freeware — not for commercial use.
>
> Esta ferramenta destina-se apenas ao uso educacional e pessoal. Os usuários são os únicos responsáveis pelo cumprimento das leis locais e pelo respeito aos direitos de propriedade intelectual. Não possui afiliação com a Nintendo Co., Ltd. Freeware — não é para uso comercial.

---

## Português

**NSP Mod Maker** é um app Windows que aplica um mod LayeredFS diretamente dentro de um novo NSP reconstruído. O resultado é um único `.nsp` que você instala pelo DBI como qualquer outro título — sem depender de `atmosphere/contents` no SD.

### O que você precisa

| Item | Observações |
|---|---|
| Windows 10/11 (64-bit) | |
| `NSPModMaker.exe` | Baixe na página de releases |
| Base Game NSP ou XCI | Arquivo do jogo sem update aplicado |
| Update NSP | Versão mais recente do update do jogo |
| Pasta do mod LayeredFS | A pasta `romfs` e/ou `exefs` do mod |
| Arquivo `prod.keys` | Gerado pelo Lockpick_RCM no seu Switch |
| Nintendo Switch com CFW | Atmosphere ou CFW compatível |

> **Sobre o prod.keys:** O app não inclui, gera nem baixa chaves. Você precisa gerar o `prod.keys` no seu próprio Switch usando o homebrew **Lockpick_RCM**. O arquivo fica em `switch/prod.keys` no seu SD. Na primeira execução do app, você vai selecionar esse arquivo. O caminho fica salvo localmente em `%APPDATA%\NSPModMaker\config.json`.

### Espaço em disco e tempo de build

O app extrai, mescla e reconstrói o conteúdo completo do jogo. Para jogos grandes, isso exige bastante espaço e tempo:

| Tamanho do jogo | Espaço livre necessário | Tempo aproximado |
|---|---|---|
| até ~2 GB | ~10 GB | 5–15 min |
| ~5–8 GB | ~25 GB | 20–40 min |
| ~17 GB (ex: Zelda TotK) | ~55 GB | 3–5 horas |

Use uma pasta de trabalho em um SSD para reduzir o tempo de build.

### Como usar

**1. Abra o `NSPModMaker.exe`.**

Na primeira execução, o app vai pedir o arquivo `prod.keys`. Selecione o arquivo no seu SD ou em uma pasta local.

**2. Selecione o Base Game.**

Clique em **Base Game NSP/XCI** e selecione o arquivo `.nsp` ou `.xci` do jogo base (sem update).

**3. Selecione o Update.**

Clique em **Update NSP** e selecione o arquivo `.nsp` do update mais recente.

**4. Selecione a pasta do mod.**

Clique em **Mod LayeredFS** e selecione a pasta raiz do mod. O app aceita as estruturas mais comuns:

```
romfs/
exefs/
<TITLE_ID>/romfs/
<TITLE_ID>/exefs/
atmosphere/contents/<TITLE_ID>/romfs/
atmosphere/contents/<TITLE_ID>/exefs/
```

Se o mod tiver uma pasta ExeFS separada da pasta principal, use o campo **Mod ExeFS (opcional)** para indicá-la.

**5. Confirme o Title ID.**

O app tenta preencher o Title ID automaticamente pelo nome do arquivo. Confirme que está correto — é um número hexadecimal de 16 caracteres, como `0100F2C0115B6000`.

Se não aparecer, você pode encontrar o Title ID do jogo em sites como NSWDB ou consultando o próprio NSP.

**6. Escolha o nome do NSP de saída.**

Clique em **NSP de saída** para escolher onde salvar e o nome do arquivo gerado. Se o arquivo já existir, o app cria automaticamente o próximo nome disponível (`Mod (2).nsp`, etc.).

**7. Clique em Gerar NSP.**

O progresso aparece no log do app. Ao final, o arquivo `.nsp` estará no local escolhido.

### Como instalar no Switch

Use o **DBI** no seu Switch para instalar o NSP gerado. O DBI suporta instalação via USB (MTP) ou pelo SD. Após a instalação, o jogo aparece no menu normalmente.

### Prioridade dos arquivos no NSP final

```
Base Game  →  Update  →  Mod LayeredFS
```

O arquivo do mod tem prioridade máxima. Se o mesmo arquivo existir nos três, o do mod é usado. O NSP final contém o conteúdo completo mesclado — não usa BKTR delta, então é normal que o arquivo gerado seja maior que a base ou o update individualmente.

### Resolução de problemas

| Problema | O que verificar |
|---|---|
| Title ID não preenchido automaticamente | Verifique se o nome do arquivo NSP contém um hex de 16 caracteres |
| Falha na extração do Base ou Update | Confirme se o `prod.keys` é do mesmo Switch que originou o conteúdo |
| Crash no Switch após instalar | Certifique-se de que o Update NSP corresponde ao update mais recente instalado no Switch |
| Erro de espaço em disco | Libere espaço — veja tabela acima para estimativas por tamanho de jogo |
| Jogo instalado mas não aparece no menu | Tente reiniciar o Switch após a instalação pelo DBI |

### Licença

Freeware distribuído sob CC BY-NC-ND 4.0 — gratuito para uso e compartilhamento na forma original; sem modificações, sem uso comercial.

---

## English

**NSP Mod Maker** is a Windows app that applies a LayeredFS mod directly inside a newly rebuilt NSP. The result is a single `.nsp` you install via DBI like any other title — no need for `atmosphere/contents` on the SD card.

### What you need

| Item | Notes |
|---|---|
| Windows 10/11 (64-bit) | |
| `NSPModMaker.exe` | Download from the releases page |
| Base Game NSP or XCI | The game file without any update applied |
| Update NSP | The latest game update |
| LayeredFS mod folder | The mod's `romfs` and/or `exefs` folder |
| `prod.keys` file | Generated by Lockpick_RCM on your Switch |
| Nintendo Switch with CFW | Atmosphere or compatible CFW |

> **About prod.keys:** The app does not include, generate, or download keys. You need to generate `prod.keys` on your own Switch using the **Lockpick_RCM** homebrew. The file is saved to `switch/prod.keys` on your SD card. On first run, the app asks you to select this file. The path is saved locally at `%APPDATA%\NSPModMaker\config.json`.

### Disk space and build time

The app extracts, merges, and rebuilds the full game content. For large games this requires significant disk space and time:

| Game size | Free space needed | Approximate time |
|---|---|---|
| up to ~2 GB | ~10 GB | 5–15 min |
| ~5–8 GB | ~25 GB | 20–40 min |
| ~17 GB (e.g. Zelda TotK) | ~55 GB | 3–5 hours |

Use a working folder on an SSD to reduce build time.

### How to use

**1. Open `NSPModMaker.exe`.**

On first run, the app will ask for your `prod.keys` file. Select the file from your SD card or a local folder.

**2. Select the Base Game.**

Click **Base Game NSP/XCI** and select the base game `.nsp` or `.xci` file (no update applied).

**3. Select the Update.**

Click **Update NSP** and select the latest update `.nsp` file.

**4. Select the mod folder.**

Click **Mod LayeredFS** and select the mod's root folder. The app accepts the most common structures:

```
romfs/
exefs/
<TITLE_ID>/romfs/
<TITLE_ID>/exefs/
atmosphere/contents/<TITLE_ID>/romfs/
atmosphere/contents/<TITLE_ID>/exefs/
```

If the mod has a separate ExeFS folder, use the **Optional Mod ExeFS** field to point to it.

**5. Confirm the Title ID.**

The app tries to fill the Title ID automatically from the filename. Confirm it is correct — it is a 16-character hex number like `0100F2C0115B6000`.

If it is not filled, you can find the Title ID on sites like NSWDB or by inspecting the NSP.

**6. Choose the output NSP name.**

Click **Output NSP** to choose where to save the file and its name. If the file already exists, the app automatically creates the next available name (`Mod (2).nsp`, etc.).

**7. Click Generate NSP.**

Build progress appears in the app log. When done, the `.nsp` file is at the chosen location.

### Installing on the Switch

Use **DBI** on your Switch to install the generated NSP. DBI supports installation via USB (MTP) or from the SD card. After installation, the game appears in the home menu normally.

### File priority in the final NSP

```
Base Game  →  Update  →  LayeredFS Mod
```

The mod has the highest priority. If the same file exists in all three, the mod file is used. The final NSP contains the fully merged content — it does not use BKTR delta, so it is normal for the output file to be larger than either the base or update individually.

### Troubleshooting

| Problem | What to check |
|---|---|
| Title ID not filled automatically | Make sure the NSP filename contains a 16-character hex string |
| Base or Update extraction failed | Confirm that `prod.keys` came from the same Switch that owns the content |
| Game crashes on Switch after install | Make sure the Update NSP matches the latest update version installed on the Switch |
| Disk space error | Free up space — see the table above for estimates by game size |
| Game installed but not showing in menu | Try restarting the Switch after DBI installation |

### License

Freeware distributed under CC BY-NC-ND 4.0 — free to use and share in original form; no modification, no commercial use.

---

*NSP Mod Maker — CostelaBR 2026*
