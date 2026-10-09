<p align="center">
  <a href="README.md">🇺🇸 English</a> · <a href="README_PTBR.md">🇧🇷 Português (Brasil)</a>
</p>

<p align="center">
  <img src="logo-horizontal.png" alt="Dub Vulpes" width="420">
</p>

<h1 align="center">Dub Vulpes</h1>

<p align="center">
  <strong>Dublagem com IA — 100% local, 100% grátis.</strong><br>
  Transcreva, gere vozes clonadas, converta timbres e exporte a dublagem completa —
  na sua máquina ou na nuvem, você escolhe.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/status-beta%20p%C3%BAblico%20em%20breve-orange" alt="Beta público em breve">
  <img src="https://img.shields.io/badge/license-GPL--3.0-green" alt="Licença GPL-3.0">
  <img src="https://img.shields.io/badge/platform-Windows%20%7C%20Web%20(self--hosted)-lightgrey" alt="Plataformas">
  <img src="https://img.shields.io/badge/languages-pt%20%7C%20en%20%7C%20es%20%7C%20fr%20%7C%20zh-orange" alt="Idiomas da interface">
</p>

> 🚧 **Em testes finais — o beta público chega em breve.** A aplicação está totalmente
> funcional e passando pela rodada final de validação em máquinas reais. O
> **instalador, o código-fonte (GPL-3.0) e a documentação serão publicados nesta
> página** junto com a versão beta. ⭐ **Deixe uma star no repositório para ser
> avisado.**

---

## O que é o Dub Vulpes?

O **Dub Vulpes** é um estúdio de dublagem open-source para vídeos e audiolivros. Ele
cobre o fluxo completo: você importa o vídeo (ou o SRT), o app **transcreve com
diarização**, organiza o conteúdo em um **editor de áudio multi-trilha**, gera as vozes
dubladas por IA (com **clonagem de voz** a partir de um clipe de referência), permite
**converter o timbre** de cada trilha, separa **stems** (música/efeitos/diálogo) e
faz o **mixdown** final em FLAC ou vídeo.

A grande diferença: **você escolhe onde a IA roda**.

- **Modo local** — motores de voz executam na **sua GPU** (Chatterbox, Qwen3, OmniVoice,
  Fish Speech, Seed-VC, WhisperX). Nenhum áudio sai da sua máquina.
- **Modo nuvem** — use sua própria chave de **Fish Audio** ou **ElevenLabs** para quem
  preferir qualidade de serviço gerenciado. As chaves são suas, salvas na sua aplicação.

A interface está disponível em **português, inglês, espanhol, francês e chinês**
(traduzidas por IA — revisões da comunidade são bem-vindas).

### Principais funcionalidades

- 🎬 Projetos → capítulos → trilhas/clipes, com editor multi-trilha estilo DAW (autosave, mover, dividir)
- 📝 Transcrição automática com diarização (**WhisperX**) e importação de SRT
- 🗣️ TTS com **clonagem de voz** por clipe de referência (nuvem ou local)
- 🎭 **Conversão de timbre (STS)** — inclusive com voz de referência por trilha
- ✨ Criação/design de vozes (Qwen3 VoiceDesign, Fish Audio, ElevenLabs)
- 🎚️ Separação de stems (**Demucs** / **MDX** via audio-separator)
- 🔊 Mixdown e exportação (FLAC, áudio, SRT e vídeo)
- 📚 Modo audiolivro (livros → capítulos → áudios ordenados)
- 😊 Biblioteca de emoções e descritores de voz
- ☁️ Backup por projeto no Google Drive (em desenvolvimento)
- 🖥️ App **desktop** para Windows ou **web self-hosted**

---

## Engines e modelos suportados

Todas as engines (nuvem e local) seguem o mesmo contrato interno — a troca é feita em
**Configurações → Engines**, sem código.

### Nuvem (chave de API do próprio usuário)

| Engine | Uso | Modelo | Observação |
|---|---|---|---|
| **Fish Audio** | TTS + clonagem | S2.1-Pro (configurável) | chave salva no app |
| **ElevenLabs** | TTS | `eleven_multilingual_v2` (configurável) | chave por usuário |

### Local (roda na sua GPU; pesos baixam no primeiro uso)

| Engine | Uso | Licença do modelo | Requisito |
|---|---|---|---|
| **Chatterbox Multilingual V3** | TTS (23 idiomas) | MIT | sidecar ai-runner |
| **Qwen3-TTS 0.6B** (+ VoiceDesign 1.7B) | TTS + design de voz | Apache 2.0 | sidecar ai-runner |
| **OmniVoice** | TTS zero-shot (600+ idiomas) | Apache 2.0 | sidecar dedicado |
| **Fish Speech V1 — S1-mini** (~0.5B) | TTS | CC-BY-NC-SA (**uso pessoal**) | servidor dedicado |
| **Fish Speech V2 — S2-Pro** (4B) | TTS | modelo oficial | ⚠️ **em desenvolvimento** |
| **Chatterbox VC** | STS (conversão de timbre) | MIT | sidecar ai-runner |
| **Seed-VC V2** | STS (conversão de timbre) | modelo oficial | sidecar dedicado |

> **Mais modelos estão por vir.** O Dub Vulpes é um projeto open-source **sem fins
> lucrativos**: novas engines e modelos de voz entram **gradualmente**, conforme
> se tornam viáveis para a comunidade (licença dos pesos, requisitos de hardware,
> qualidade). Sugestões são muito bem-vindas.

### Transcrição e stems (pipeline Python local)

| Tarefa | Ferramenta | Observação |
|---|---|---|
| Transcrição + diarização | **WhisperX** | SRT pronto para dublagem |
| Separação de stems | **Demucs** / **MDX** (audio-separator) | música / efeitos / diálogo |

---

## Disponibilidade — o que chega com o beta

- 🖥️ **App desktop (Windows 10+)** — instalador com assistente de 4 passos
  (idioma → termos → pasta). Sem admin; o app configura sozinho o banco local e o
  runtime embutido: sem terminal, sem banco de dados para instalar.
- 🌐 **Web self-hosted** — o **código-fonte completo** será publicado neste
  repositório sob **GPL-3.0** junto com o beta (PHP, Laravel + React e o pipeline
  Python local de WhisperX/Demucs/engines).
- 📥 Os anúncios de versão saem na página de **Releases** deste repositório —
  ⭐ star e 👁️ watch para ser notificado.

### Hardware (referência prática)

| Perfil | Requisito | O que roda acelerado |
|---|---|---|
| **CUDA** (recomendado) | NVIDIA, driver ≥ 12.4 | tudo: TTS/STS local, transcrição (`float16`), stems |
| **DirectML** | AMD/Intel | stems MDX; restante em CPU |
| **CPU** | qualquer máquina | tudo roda (`int8`), só mais devagar |

Uma **RTX 3060 12 GB** roda tranquilamente o pipeline local completo (S1-mini,
Chatterbox, Qwen3-TTS, OmniVoice, WhisperX e separação de stems). O app é
**preparado para GPU dupla**: você escolhe uma placa prioritária e uma de apoio, e os
modelos são carregados conforme a VRAM disponível. Modelos maiores (como o Fish
Speech S2-Pro, ≥ 24 GB de VRAM) estão no roteiro — veja **Apoio** abaixo.

---

## 💖 Apoio

O Dub Vulpes é um **projeto comunitário sem empresa por trás**: sem CNPJ, sem
assinatura, **grátis para sempre** — a filosofia é 100% local e a liberdade do usuário.

A forma de apoio mais impactante neste momento é o
**[GitHub Sponsors](https://github.com/sponsors/jcdark)** 💰: a meta atual é a
**aquisição de uma nova placa de vídeo**, que libera diretamente a implementação de
**modelos de voz mais robustos e avançados** (clonagem de maior qualidade e modelos
locais maiores) para toda a comunidade.

Você também pode ajudar:

- ⭐ **Dando star e divulgando** — visibilidade é o que faz a comunidade crescer
- 🐞 **Reportando problemas** quando o beta abrir (bugs, hardware variado, sugestões)
- 💻 **Contribuindo com código** — PRs são bem-vindos assim que o fonte for publicado
  (correções, novas engines, traduções para os 5 idiomas da interface)

---

## Licença

O Dub Vulpes é e será distribuído sob a
**GNU General Public License v3.0 (GPL-3.0)** — software livre, **grátis para
sempre**: usar, estudar, modificar e redistribuir são liberdades garantidas pela
licença. O texto completo acompanha o código-fonte na versão beta.

**Atenção aos pesos dos modelos**: cada engine carrega a licença do projeto que a
mantém — **Chatterbox** (MIT), **Qwen3-TTS** e **OmniVoice** (Apache 2.0) são
permissivas; os pesos do **Fish Speech V1 (S1-mini)** são **CC-BY-NC-SA** (**uso
pessoal / não comercial**). Os pesos nunca são incluídos no pacote: são baixados de
fontes oficiais no primeiro uso, sob suas respectivas licenças.

---

<p align="center">
  <strong>Dub Vulpes</strong> · GPL-3.0 · feito pela comunidade, para a comunidade 🦊
</p>
