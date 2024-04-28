---
title: 約定式提交 Conventional Commits
tags: git, commit, conventional
---

# 約定式提交 Conventional Commits

```
<type>[optional scope]: <description>

[optional body]

[optional footer(s)]
```

1. fix: fix 類型的 commit 表示修正了某個 bug；對應到 [SemVer](http://semver.org/) 的 `PATCH`。
2. feat: feat 類型的 commit 表示增加了一個功能；對應到 [SemVer](http://semver.org/) 的 `MINOR`。
3. BREAKING CHANGE: 表示重大變更並且在 commit 的 `footer` 註記 `BREAKING CHANGE` 且一定要全部大寫或是再 type/scope 之後加上 `!` 標記；`BREAKING CHANGE` 可以是任何類型的 commit 的一部分；對應到 [SemVer](http://semver.org/) 的 `MAJOR`。
4. 除了 `fix`、`feat` 也可以有其他類型的 commit，例如：

- build: 與建置系統或外部依賴項有關的更改。
- ci: 對 CI 配置文件或 script 的更改。
- docs: 文檔相關的更改。
- refactor: 代碼重構。
- perf: 效能相關的改進。
- style: coding style 的調整。
- test: 新增或修改測試。
- revert: 回復之前的 commit。
- chore: 雜項更改，不包含任何 source code 或 test 的更改。

1. scope: 用於描述 commit 影響的範圍，例如：`router`、`component`、`item ui`...。
2. description: 用於描述 commit 的目的，最好簡潔且清楚。
3. body: 用於描述 commit 的詳細內容，可以包含更多的資訊。
4. footer: 用於描述一些額外的資訊，例如：`BREAKING CHANGE`、`Issue number`...。

Ref:

- [conventional-commits](https://github.com/conventional-commits/conventionalcommits.org)
- [SemVer](https://semver.org/)
- [封面圖來源](https://www.ghibli.jp/info/013772/?ref=seanmars.dev)
