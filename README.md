# snotes

snotes is a small encrypted terminal notes app written in Python.

It is built for people who want private, local notes without a GUI, cloud account, or unnecessary complexity. Everything lives in a single encrypted file, and you interact with it through a fast terminal interface.

---

## Overview

snotes stores all notes in a local encrypted vault and only asks for your password once per session.

You browse and manage notes in a curses-based TUI, and edit them using your normal terminal editor (`$VISUAL` / `$EDITOR`, falling back to `vi`). This keeps things simple, fast, and very Unix-friendly.

---

## Encryption & Security

- AES-256-CTR for encryption  
- HMAC-SHA256 for authentication (tamper detection)  
- scrypt for password-based key derivation  
- fresh random salt and IV on every save  
- constant-time MAC verification  

The vault format stores:
- a **current snapshot**
- a **previous snapshot** (for basic recovery safety)

Writes are atomic and fsync’d to reduce risk of corruption.

---

## Features

- encrypted single-file vault  
- password unlock once per session  
- curses TUI interface  
- add, edit, duplicate, delete notes  
- live filter / search  
- title color tagging  
- immediate save after every modification  
- uses your normal terminal editor  
- no cloud, no account, no background services  

---

## Dependencies

- Python 3.10+  
- OpenSSL (`openssl` command)  
- standard Python libraries (curses, hashlib, etc.)  

No external Python packages required.

---

## Usage

```bash
snotes
```

On first run, it will create a new vault.

Basic controls:

- `Enter` – edit note  
- `a` – add note  
- `d` – delete note  
- `D` – duplicate note  
- `C` – cycle title color  
- `/` – live search  
- `q` – quit  

---

## Installation

snotes is a single Python script.

Download it, make it executable, and place it in your `$PATH`:

```bash
curl -fsSL https://raw.githubusercontent.com/HarderLemonade/snotes/main/snotes -o snotes
chmod +x snotes
sudo install snotes /usr/local/bin/snotes
```

Or install it locally without root:

```bash
curl -fsSL https://raw.githubusercontent.com/HarderLemonade/snotes/main/snotes -o snotes
chmod +x snotes
mkdir -p ~/.local/bin
mv snotes ~/.local/bin/
```

(make sure `~/.local/bin` is in your `$PATH`)

---

## Requirements

- Python 3.10+
- OpenSSL (`openssl` available in PATH)

---

## Run

```bash
snotes
```

## Philosophy

snotes is designed to be:

- simple  
- private  
- reliable  

No sync, no accounts, no hidden services. Just your notes, encrypted, in one file.

---

## License

This project is licensed under the **GNU General Public License v2.0 (GPL-2.0)**.

You are free to use, modify, and distribute this software under the terms of the GPLv2.
