# project-profile Specification

## Purpose
登记 PhotoCraft 的项目身份与本工作区定位，作为进入该仓库的第一份结构化说明；
实现细节以上游文档为准，这里只写「是什么、归谁、在本工作区怎么用」。

## Requirements

### Requirement: 项目身份与许可
系统 SHALL 明确记录项目身份：Rust + WebAssembly 的专业照片调色器（ArtCraft 生态），上游仓库 `storytold/photocraft`，许可 MIT OR Apache-2.0（双许可）。
本仓库是上游的 fork/镜像，SHALL 保留上游许可与归属声明，不得移除 `LICENSE*`、
`ATTRIBUTION.md` 等文件。

#### Scenario: 能查到项目身份
WHEN 新成员进入本仓库
THEN 从本 spec 得知项目是什么、上游在哪、许可是什么。

#### Scenario: 保留上游归属
WHEN 修改或分发本仓库
THEN 上游许可与归属文件保持完整。

### Requirement: 本工作区中的角色
muyaya.world 的 `/photocraft/` 页面由前端仓库 `deploy-apps.yml` 的 `build-wasm` job **从上游 `storytold/photocraft` 拉源码**构建，构建时打 `ai-bridge.patch` 补丁，产物由 `photocraft-build.lock` 指纹锁与 `scripts/verify-photocraft-build.sh` 校验。**本 fork 不参与线上部署**，只作本地参考与试验；部署真相在前端仓库。

#### Scenario: 部署关系可查
WHEN 有人想知道这个仓库是否参与 muyaya 线上部署
THEN 本 spec 给出明确答案与部署真相所在位置。

### Requirement: 文档归属
文档权威来源 SHALL 以如下为准，本 `openspec/` 不得复制或替代上游文档：
上游 `README.md`、`AGENTS.md`、`ROADMAP.md`、`docs/` 为内部实现与行为的权威来源；本 `openspec/` 只记录本工作区的集成与差异，不重复上游文档。 上游 release 包的 wasm 不含 AI Bridge（约 98KB），自建构建约 26MB；低于体积下限说明被上游包覆盖。

#### Scenario: 不重复维护上游文档
WHEN 需要了解内部实现
THEN 去上游文档查，而不是在本 `openspec/` 里找（这里只记录工作区差异）。
