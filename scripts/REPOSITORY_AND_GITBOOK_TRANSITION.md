# 仓库与 GitBook 过渡期协作说明

本文档用于说明 `nsclouds-api-docs` 在公司 GitHub 暂不作为发布源期间的协作方式。

## 当前状态

- 个人 GitHub 仓库：`git@github.com:togear/another-nsclouds-api-docs.git`
- 公司 GitHub 仓库：`git@github.com:ngaa-dev/nsclouds-api-docs.git`
- 当前 GitBook：继续使用已共享出来的个人 GitBook space。
- 公司 GitBook：暂未切换。
- 当前 GitBook OpenAPI raw URL：默认指向个人 GitHub 仓库。

当前阶段的边界是：GitBook space 暂时不迁移，公司 GitHub 也暂不作为发布源。文档页面和 OpenAPI 文件都继续从个人 GitHub/GitBook 链路发布，避免 GitBook GitHub App 权限未就绪时出现双源同步问题。

## 当前过渡期原则

- 个人 GitHub 是当前发布源，OpenAPI raw URL 默认使用个人仓库。
- 当前共享 GitBook space 继续承载展示和验证，不替换 `app.gitbook.com/s/...` 页面地址。
- GitBook OpenAPI 同步脚本只让 GitBook 从 raw GitHub URL 拉取 `docs/bundled` 下的 YAML，不会上传本地文件。
- 同步 GitBook OpenAPI 前，必须先确保个人 GitHub 的 `main` 分支已经包含最新 `docs/bundled` 文件。
- 公司 GitHub 暂不参与当前 GitBook 发布链路；等公司 GitHub App/GitBook 权限就绪后再切换。
- 文档里的示例和 OpenAPI 展示必须按线上真实可用状态维护；未完成适配的能力可以保留 schema，但需要明确标注“建设中”或“适配中”，不要放入可执行示例。
- 所有接口验证使用环境变量传入密钥，禁止把密钥写入文档、提交记录、脚本默认值或命令输出。

## 当前发布链路

| GitHub 内容源 | GitBook space | 用途 |
| --- | --- | --- |
| `liujia-hbu/nsclouds-api-docs` | 已共享的个人 GitBook space | 当前展示、预览、验证 |


GitBook OpenAPI 应从个人 GitHub raw URL 拉取：

```text
https://raw.githubusercontent.com/liujia-hbu/nsclouds-api-docs/main/docs/bundled
```

公司 GitBook 和公司 GitHub 准备好后的最终状态：

| GitHub 内容源 | GitBook space | 用途 |
| --- | --- | --- |
| `ngaa-dev/nsclouds-api-docs` | 公司 GitBook space | 对外正式展示 |


## 推荐 remote 配置

当前建议让 `origin` 保持为个人 GitHub：

```bash
origin git@github.com:liujia-hbu/nsclouds-api-docs.git
```

如果需要保留公司远端用于后续切换，可以新增但暂不用于发布：

```bash
git remote add company git@github.com:ngaa-dev/nsclouds-api-docs.git
git remote -v

```

推荐含义：

- `origin`：个人 GitHub，当前发布源。
- `company`：公司 GitHub，暂不参与当前 GitBook 发布链路。

## 当前开发与发布流程

### 1. 开始修改前同步个人仓库

```bash
git fetch origin
git checkout main
git merge origin/main
```

### 2. 本地修改并构建

```bash
bash build-docs.sh
```

构建后重点检查：

- `docs/{cn,global}/{zh,en}/`
- `docs/{cn,global}/{zh,en}/openapi/`
- `docs/bundled/{cn,global}/{zh,en}/`

不要手工维护这些生成目录，应修改 `docs/templates/`、`scripts/data/` 或生成脚本后重建。

### 3. 推送个人 GitHub

由于 GitBook OpenAPI 默认从个人 GitHub raw URL 拉取，必须先把最新内容推到个人仓库：

```bash
git push origin main
```

### 4. 同步当前共享 GitBook OpenAPI

个人 GitHub 推送完成后，再同步当前共享出来的 GitBook space：

```bash
source ~/.bash_profile
python3 scripts/sync_gitbook_openapi.py --dry-run
python3 scripts/sync_gitbook_openapi.py --wait
```

当前脚本默认 raw base 是个人 GitHub：

```text
https://raw.githubusercontent.com/togear/another-nsclouds-api-docs/main/docs/bundled
```

dry-run 输出里的 URL 必须全部指向 `liujia-hbu/nsclouds-api-docs`。

## 公司 GitHub/GitBook 后续切换条件

切换到公司 GitHub/GitBook 前，需要先完成：

- 公司 GitHub `ngaa-dev/nsclouds-api-docs` 已安装并授权 GitBook GitHub App。
- GitBook 能选择公司 repo 和目标 branch 进行 Git Sync。
- 公司 GitBook token/org id 已准备好。
- 已确认公司 raw URL 可被 GitBook 访问。

切换时再把默认 raw base 改回：

```text
https://raw.githubusercontent.com/ngaa-dev/nsclouds-api-docs/main/docs/bundled
```

## 发布检查清单

每次准备发布前至少检查：

- 已同步个人 GitHub 最新提交。
- 已执行 `bash build-docs.sh`。
- `git diff --check` 通过。
- GitBook OpenAPI dry-run 输出全部指向 `liujia-hbu/nsclouds-api-docs`。
- GitBook 展示的请求示例已经真实 curl 验证。
- 密钥只通过环境变量使用，未写入文档、命令输出或提交。
- 个人 GitHub 已推送最新提交。
- 当前共享 GitBook space 已完成 OpenAPI 同步。

## 注意事项

- GitBook OpenAPI 同步脚本不是上传本地文件，而是让 GitBook 从 raw GitHub URL 拉取 `docs/bundled` 下的 YAML。
- 因此，必须先把对应分支推到个人 GitHub 仓库，再同步 GitBook。
- 当前阶段不替换 `app.gitbook.com/s/...` 链接。
- 当前阶段不使用 `ngaa-dev/nsclouds-api-docs` 作为 GitBook 发布源。
