# gprMax Workbench Workspace

本目录是 gprMax 服务型程序的多仓库工作区。前端采用 Vue，后端使用 Django；Django 获取运行配置后分发到运行机器，并通过 Docker 容器运行 gprMax。

## 新人初始化

推荐使用 `repo` 拉取整个工作区：

```bash
mkdir gpr
cd gpr
repo init -u https://github.com/sethome2/gpr_manifest.git -b main
repo sync -c -j8
```

如果本机没有 `repo`，Ubuntu/Debian 可以先安装：

```bash
sudo apt install repo
```

如果系统源没有 `repo`，可以按 Android repo 官方方式安装到用户目录：

```bash
mkdir -p ~/.local/bin
curl https://storage.googleapis.com/git-repo-downloads/repo > ~/.local/bin/repo
chmod a+x ~/.local/bin/repo
```

确认 `~/.local/bin` 已加入 `PATH` 后再执行 `repo init`。

## 日常更新

同步所有项目到 manifest 指定分支的最新提交：

```bash
repo sync -c -j8
```

开始开发分支：

```bash
repo start work --all
```

只在某个项目开开发分支：

```bash
repo start backend-work gprmax_backend
repo start frontend-work gprMax-Workbench
```

## 工作区结构

- `gpr_manifest`：工作区管理仓库，包含 `repo` manifest 和根目录说明文件源文件。
- `gprMax`：gprMax 软件本体，基于 FDTD 方法的电磁仿真程序，常用于探地雷达仿真。
- `gprmax_backend`：gprMax-Workbench 后端程序。
- `gprMax_docker`：封装 gprMax 的 Dockerfile 文件，包含 GPU 和 CPU 版本。
- `gprMax_worker`：连接 RabbitMQ 和后端内部 API、调用 CPU/GPU Docker 镜像执行仿真的节点 Agent。
- `gprMax-Workbench`：gprMax 前端程序，主要采用 Vue、Element Plus、Tailwind CSS 和 Three.js。
- `gprMax_in_doc`：内部文档，关于 gprMax `.in` 文件。
- `gprMax_doc`：外部使用说明文档，使用 Material for MkDocs/zensical 构建。

## 工作区元信息

`README.md` 和 `AGENTS.md` 的源文件由 `gpr_manifest` 管理：

- `gpr_manifest/README.md`
- `gpr_manifest/AGENTS.md`

`repo sync` 会通过 `default.xml` 中的 `copyfile` 把它们复制到工作区根目录。修改这些文件时，优先修改 `gpr_manifest` 里的源文件，再同步或手动复制到根目录。

`repo` 实际使用的 manifest 位于 `.repo/manifests/default.xml`；工作区中的 `gpr_manifest/default.xml` 是可见副本，便于查看、修改和提交。
