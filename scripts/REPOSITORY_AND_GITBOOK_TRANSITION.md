# 仓库与 GitBook 过渡期协作说明

本文档用于说明 `nsclouds-api-docs` 在公司 GitHub 已启用、公司 GitBook 尚未切换期间的协作方式。

## 当前状态

- 个人 GitHub 仓库：`git@github.com:liujia-hbu/nsclouds-api-docs.git`
- 公司 GitHub 仓库：`git@github.com:ngaa-dev/nsclouds-api-docs.git`
- 当前 GitBook：继续使用已共享出来的个人 GitBook space。
- 公司 GitBook：暂未切换。
- 当前 GitBook OpenAPI raw URL：默认指向公司 GitHub 仓库。

当前阶段的边界是：GitBook space 暂时不迁移，但文档内容和 OpenAPI 文件来源应收敛到公司 GitHub。个人 GitHub 可以继续作为历史备份或个人调试远端，但不再作为默认 OpenAPI raw 来源。

## 当前过渡期原则

- 公司 GitHub 是正式内容源，OpenAPI raw URL 默认使用公司仓库。
- 当前共享 GitBook space 继续承载展示和验证，不替换 `app.gitbook.com/s/...` 页面地址。
- GitBook OpenAPI 同步脚本只让 GitBook 从 raw GitHub URL 拉取 `docs/bundled` 下的 YAML，不会上传本地文件。
- 同步 GitBook OpenAPI 前，必须先确保公司 GitHub 的 `main` 分支已经包含最新 `docs/bundled` 文件。
- 文档里的示例和 OpenAPI 展示必须按线上真实可用状态维护；未完成适配的能力可以保留 schema，但需要明确标注“建设中”或“适配中”，不要放入可执行示例。
- 所有接口验证使用环境变量传入密钥，禁止把密钥写入文档、提交记录、脚本默认值或命令输出。

## 目标状态

当前临时状态：

| GitHub 内容源 | GitBook space | 用途 |
| --- | --- | --- |
| `ngaa-dev/nsclouds-api-docs` | 已共享的个人 GitBook space | 临时正式展示、预览、验证 |

公司 GitBook 准备好后的最终状态：

| GitHub 内容源 | GitBook space | 用途 |
| --- | --- | --- |
| `ngaa-dev/nsclouds-api-docs` | 公司 GitBook space | 对外正式展示 |

GitBook OpenAPI 应从公司 GitHub raw URL 拉取：

```text
https://raw.githubusercontent.com/ngaa-dev/nsclouds-api-docs/main/docs/bundled
```

## 推荐 remote 配置

建议同时保留个人和公司两个 remote，并在命令中显式使用目标 remote，避免依赖临时记忆 `origin` 指向哪里。

如果当前 `origin` 是个人仓库，可以新增公司远端：

```bash
git remote add company git@github.com:ngaa-dev/nsclouds-api-docs.git
git remote -v
```

推荐含义：

- `origin` 或 `personal`：个人 GitHub，仅用于备份或个人调试。
- `company`：公司 GitHub，作为正式内容源。

如果团队决定让 `origin` 固定代表公司仓库，也可以采用：

```bash
git remote rename origin personal
git remote add origin git@github.com:ngaa-dev/nsclouds-api-docs.git
```

关键是团队内部统一命名，并在发布命令中明确目标远端。

## 过渡期开发流程

### 1. 开始修改前同步公司仓库

公司 GitHub 是正式内容源，因此每次修改前应先同步公司仓库最新提交：

```bash
git fetch company
git checkout main
git merge company/main
```

如果当前本地还没有 `company` remote，先按“推荐 remote 配置”新增。

### 2. 本地修改并构建

```bash
bash build-docs.sh
```

构建后重点检查：

- `docs/{cn,global}/{zh,en}/`
- `docs/{cn,global}/{zh,en}/openapi/`
- `docs/bundled/{cn,global}/{zh,en}/`

不要手工维护这些生成目录，应修改 `docs/templates/`、`scripts/data/` 或生成脚本后重建。

### 3. 推送公司 GitHub

由于 GitBook OpenAPI 默认从公司 GitHub raw URL 拉取，必须先把最新内容推到公司仓库：

```bash
git push company main
```

如果团队已把 `origin` 固定为公司仓库，则使用：

```bash
git push origin main
```

个人 GitHub 可按需作为备份推送，但它不再是默认 OpenAPI source。

### 4. 同步当前共享 GitBook OpenAPI

公司 GitHub 推送完成后，再同步当前共享出来的 GitBook space：

```bash
source ~/.bash_profile
python3 scripts/sync_gitbook_openapi.py --dry-run
python3 scripts/sync_gitbook_openapi.py --wait
```

当前脚本默认 raw base 是公司 GitHub：

```text
https://raw.githubusercontent.com/ngaa-dev/nsclouds-api-docs/main/docs/bundled
```

dry-run 输出里的 URL 必须全部指向 `ngaa-dev/nsclouds-api-docs`。

## 角色分工建议

- 日常修改者：先合并公司仓库最新代码，再在本地修改和构建。
- 内容发布者：负责把验证通过的提交推送公司 GitHub。
- GitBook 同步者：使用当前共享 GitBook 的 token/org id，同步 OpenAPI spec。
- 验收者：按 GitBook 展示的请求示例做真实 curl 验证，尤其关注多模态 `image_url`、文件上传、`file_id` 等容易和协议适配状态不一致的内容。

如果同一个人承担多个角色，也建议按这个顺序执行，避免 GitBook 从旧的 raw 文件拉取 OpenAPI。

## 公司 GitBook 准备好后的切换流程

公司 GitBook 就绪后，需要完成以下动作。

### 1. 准备公司 GitBook token 和 org id

需要公司 GitBook 的：

- `GITBOOK_TOKEN`
- `GITBOOK_ORG_ID`

不要复用个人 GitBook token 作为正式发布凭据。

### 2. 同步公司 GitBook

默认 raw base 已经是公司 GitHub，因此切换公司 GitBook 时重点是替换 token/org id：

```bash
GITBOOK_TOKEN="$COMPANY_GITBOOK_TOKEN" \
GITBOOK_ORG_ID="$COMPANY_GITBOOK_ORG_ID" \
python3 scripts/sync_gitbook_openapi.py --wait
```

如果需要临时确认 raw base，也可以显式指定：

```bash
GITBOOK_TOKEN="$COMPANY_GITBOOK_TOKEN" \
GITBOOK_ORG_ID="$COMPANY_GITBOOK_ORG_ID" \
GITBOOK_RAW_BASE=https://raw.githubusercontent.com/ngaa-dev/nsclouds-api-docs/main/docs/bundled \
python3 scripts/sync_gitbook_openapi.py --wait
```

## 发布检查清单

每次准备发布前至少检查：

- 已同步公司 GitHub 最新提交。
- 已执行 `bash build-docs.sh`。
- `git diff --check` 通过。
- GitBook OpenAPI dry-run 输出全部指向 `ngaa-dev/nsclouds-api-docs`。
- GitBook 展示的请求示例已经真实 curl 验证。
- 密钥只通过环境变量使用，未写入文档、命令输出或提交。
- 公司 GitHub 已推送最新提交。
- 当前共享 GitBook space 已完成 OpenAPI 同步。

## 注意事项

- GitBook OpenAPI 同步脚本不是上传本地文件，而是让 GitBook 从 raw GitHub URL 拉取 `docs/bundled` 下的 YAML。
- 因此，必须先把对应分支推到公司 GitHub 仓库，再同步 GitBook。
- 如果 raw base 仍指向个人仓库，GitBook 即使同步成功，也会展示个人仓库内容。
- 当前阶段不替换 `app.gitbook.com/s/...` 链接；这些链接等公司 GitBook space 正式切换时再处理。
