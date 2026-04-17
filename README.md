# kansai-style

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Agents](https://img.shields.io/badge/agents-Claude%20Code%20%7C%20Codex%20CLI%20%7C%20Copilot%20%7C%20Cursor-blue)](#supported-agents--対応エージェント)
[![Platforms](https://img.shields.io/badge/platforms-Windows%20%7C%20macOS%20%7C%20Linux-lightgrey)](#install--インストール)

Make your AI coding assistant talk in **Kansai-ben (Osaka dialect)**. Drops keigo (敬語) and cushion phrases — roughly **30–60% shorter** Japanese output.

AI コーディング支援エージェントに**関西弁・タメ口**で喋らせるスタイル集やで。敬語とクッション言葉を削って、日本語出力を **30〜60% 短く**する。

---

## Demo / 紹介動画

<video src="https://github.com/user-attachments/assets/7a182ade-7f36-4a4b-8984-61abc7e2016a" controls width="100%"></video>

---

## English

### Why

Japanese keigo (敬語) uses 30–60% more tokens than casual speech for the same meaning. `kansai-style` is a drop-in style sheet that:

- switches any Japanese output into Kansai-ben (Osaka dialect, タメ口)
- bans 12 common keigo / cushion phrases
- keeps code, identifiers, and English technical terms untouched
- ships configs for Claude Code skills, Cursor rules, Copilot instructions, and `AGENTS.md`

### Supported agents

| Agent | Config file | Platforms |
| --- | --- | --- |
| Claude Code | `.claude/skills/kansai-style/SKILL.md` | Windows / macOS / Linux |
| Cursor | `.cursorrules` | Windows / macOS / Linux |
| GitHub Copilot | `.github/copilot-instructions.md` | Windows / macOS / Linux |
| Codex CLI & other `AGENTS.md` readers | `AGENTS.md` | Windows / macOS / Linux |

### Install

Clone the repo, then copy the files you need:

```bash
git clone https://github.com/kurpsaki/kansai-style.git
cd kansai-style
```

#### Claude Code

```bash
# project-local — macOS / Linux
cp -r .claude/skills/kansai-style YOUR_PROJECT/.claude/skills/

# project-local — Windows PowerShell
Copy-Item -Recurse .claude\skills\kansai-style YOUR_PROJECT\.claude\skills\

# user-global — macOS / Linux
cp -r .claude/skills/kansai-style ~/.claude/skills/

# user-global — Windows PowerShell
Copy-Item -Recurse .claude\skills\kansai-style $env:USERPROFILE\.claude\skills\
```

Claude Code auto-loads skills whose `description` matches the user request. Trigger with `関西弁で応答して` or `タメ口で`.

#### Cursor

```bash
# macOS / Linux
cp .cursorrules YOUR_PROJECT/

# Windows PowerShell
Copy-Item .cursorrules YOUR_PROJECT\
```

Cursor reads the file at the project root automatically.

#### GitHub Copilot

```bash
# macOS / Linux
mkdir -p YOUR_PROJECT/.github
cp .github/copilot-instructions.md YOUR_PROJECT/.github/

# Windows PowerShell
New-Item -ItemType Directory -Force YOUR_PROJECT\.github
Copy-Item .github\copilot-instructions.md YOUR_PROJECT\.github\
```

#### Codex CLI (and other `AGENTS.md` readers)

```bash
# macOS / Linux
cp AGENTS.md YOUR_PROJECT/

# Windows PowerShell
Copy-Item AGENTS.md YOUR_PROJECT\
```

### Always-on activation (no trigger word needed)

To get Kansai-ben replies in **every** project without typing "関西弁で応答して" each time, add this to your global user `CLAUDE.md` (`~/.claude/CLAUDE.md` on macOS/Linux, `%USERPROFILE%\.claude\CLAUDE.md` on Windows):

````markdown
## Style (always on)
日本語の応答は常に `kansai-style` スキルを適用する。語尾ルール・禁止ワード・簡潔置換ルールを常時使用し、トリガーワードなしで発火する。
````

Make sure `kansai-style` lives in the user-global skills directory (`~/.claude/skills/kansai-style/`) so the skill is discoverable from any CWD.

### Token reduction example

| Style | Text | Chars | ≈ tokens |
| --- | --- | --- | --- |
| 敬語 (keigo) | 承知いたしました。こちらの件について説明させていただきます。関数は以下のように定義することが可能です。 | 48 | ~44 |
| 関西弁 (kansai) | 了解やで。関数はこう定義できるわ。 | 17 | ~18 |
| **Saving** | | **−65%** | **~−59%** |

### License

MIT — see [LICENSE](LICENSE).

---

## 日本語

### なんで作ったか

日本語の敬語は同じ意味をカジュアル表現より 30〜60% 多いトークンで書くで。`kansai-style` はそれを削るスタイル集やねん：

- 日本語出力を全部、関西弁・タメ口に切替
- 敬語・クッション言葉 12 個を禁止
- コード・識別子・英語技術用語は触らへん
- Claude Code / Cursor / Copilot / Codex CLI（AGENTS.md）に対応

### 対応エージェント

| エージェント | 設定ファイル | OS |
| --- | --- | --- |
| Claude Code | `.claude/skills/kansai-style/SKILL.md` | Windows / macOS / Linux |
| Cursor | `.cursorrules` | Windows / macOS / Linux |
| GitHub Copilot | `.github/copilot-instructions.md` | Windows / macOS / Linux |
| Codex CLI ほか `AGENTS.md` 準拠ツール | `AGENTS.md` | Windows / macOS / Linux |

### インストール

このリポジトリをクローンして、必要なファイルをあんたのプロジェクトにコピーするだけやで。

```bash
git clone https://github.com/kurpsaki/kansai-style.git
cd kansai-style
```

#### Claude Code の場合

```bash
# プロジェクト単位（macOS / Linux）
cp -r .claude/skills/kansai-style YOUR_PROJECT/.claude/skills/

# プロジェクト単位（Windows PowerShell）
Copy-Item -Recurse .claude\skills\kansai-style YOUR_PROJECT\.claude\skills\

# ユーザー全体（macOS / Linux）
cp -r .claude/skills/kansai-style ~/.claude/skills/

# ユーザー全体（Windows PowerShell）
Copy-Item -Recurse .claude\skills\kansai-style $env:USERPROFILE\.claude\skills\
```

「関西弁で応答して」「タメ口で」と指示したら自動で発火する。

#### Cursor の場合

```bash
# macOS / Linux
cp .cursorrules YOUR_PROJECT/

# Windows PowerShell
Copy-Item .cursorrules YOUR_PROJECT\
```

Cursor がプロジェクトルートの `.cursorrules` を自動で読む。

#### GitHub Copilot の場合

```bash
# macOS / Linux
mkdir -p YOUR_PROJECT/.github
cp .github/copilot-instructions.md YOUR_PROJECT/.github/

# Windows PowerShell
New-Item -ItemType Directory -Force YOUR_PROJECT\.github
Copy-Item .github\copilot-instructions.md YOUR_PROJECT\.github\
```

#### Codex CLI（AGENTS.md 読み込みツール）の場合

```bash
# macOS / Linux
cp AGENTS.md YOUR_PROJECT/

# Windows PowerShell
Copy-Item AGENTS.md YOUR_PROJECT\
```

### 常時適用（トリガーワード不要）

どのプロジェクトでも毎回「関西弁で応答して」と言わずに関西弁応答させたい場合、グローバルユーザー `CLAUDE.md`（macOS/Linux は `~/.claude/CLAUDE.md`、Windows は `%USERPROFILE%\.claude\CLAUDE.md`）に以下を追記してや：

````markdown
## スタイル（常時適用）
日本語の応答は常に `kansai-style` スキルを適用する。語尾ルール・禁止ワード・簡潔置換ルールを常時使用し、トリガーワードなしで発火する。
````

併せて、`kansai-style` をユーザーグローバルのスキルディレクトリ（`~/.claude/skills/kansai-style/`）に置いてや。どの CWD からも見つけられるようになる。

### トークン削減例（敬語 → 関西弁）

| スタイル | テキスト | 文字数 | ≈ トークン |
| --- | --- | --- | --- |
| 敬語 | 承知いたしました。こちらの件について説明させていただきます。関数は以下のように定義することが可能です。 | 48 | 約44 |
| 関西弁 | 了解やで。関数はこう定義できるわ。 | 17 | 約18 |
| **削減** | | **−65%** | **約−59%** |

さらに2例：

| スタイル | 例 | 文字数 |
| --- | --- | --- |
| 敬語 | エラーが発生しているようですので確認させていただきます。恐らく型の不一致が原因かと思われます。 | 47 |
| 関西弁 | エラー出とるな、確認するわ。型が合ってへんのかもしれへん。 | 28 |
| 敬語 | ご指摘いただいた箇所について修正させていただきました。ご確認のほどよろしくお願いいたします。 | 41 |
| 関西弁 | 指摘もろた分、直したで。確認してや。 | 18 |

### ライセンス

MIT — [LICENSE](LICENSE) を見てな。
