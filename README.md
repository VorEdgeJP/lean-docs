# lean-docs

製品ドキュメントから、読者が画面を触れば学べる記述を削ぎ落とすための執筆スキルです(Claude Code 向け)。

> A Claude Code skill for trimming product documentation down to what the UI does not already tell the reader. Written in Japanese.

## これは何か

多くの製品ドキュメントは、画面の代弁になっています。ボタンの名前を言い換え、トーストの文言を転記し、
同じ事実を本文・表・手順・Callout で何度も繰り返します。読者はそれを読まず、書き手は更新しきれず、
やがてどこかの記述が古くなります。

このスキルは、**画面が黙っていることだけを書く**という一点に絞った判断基準と手順を提供します。

- 足切り: 知らずに損をしないなら、正しくても書かない
- 残す 3 条件: 画面に一度も現れない / 誤解のコストが高い / 参照データ
- 参照データの判定: 画面が見せるのは全体か、そのとき起きた 1 件か

## 収録物

| ファイル | 内容 |
| --- | --- |
| `SKILL.md` | 判定の階段・消す対象の分類・手順・例外 |
| `examples/` | 架空の題材での before / after |

## インストール

リポジトリをそのまま Claude Code のスキルのディレクトリに配置してください。

```bash
git clone https://github.com/VorEdgeJP/lean-docs.git ~/.claude/skills/lean-docs
```

プロジェクト単位で使う場合は、`<プロジェクト>/.claude/skills/lean-docs` に配置してください。

## 由来

実在の SaaS のドキュメント(85 ファイル / 約 21,000 行)の全面改稿で、利用者から受けた指摘と訂正を
基準として積み上げたものです。1 ページあたりの削減率は 5〜8 割でした。

## ライセンス

[MIT License](LICENSE) で公開しています。
