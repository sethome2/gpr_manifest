这个是gprMax的服务型程序，前端采用Vue，后端使用Django，Django获取到运行配置后，分发到运行机器上，用Docker容器运行。

项目按以下结构分配:
- `gprMax` gprMax软件本体，基于FDTD方法的电磁方法，常用于探底雷达仿真
- `gprmax_backend` gprMax-Workbench的后端程序
- `gprMax_docker` 封装gprMax的docker file文件，包含GPU和CPU版本
- `gprMax-Workbench` gprMax的前端程序，主要采用Vue, ElementPlus, Tailwind CSS和ThreeJS作为可视化。
- `gprMax_in_doc` 内部文档，关于gprmax的in文件
- `gprMax_doc` 外部文档，关于gprMax-Workbench的使用说明，使用Material for MkDocs搭建。环境为miniconda的gpr环境。

项目都包含README.md，做修改时提前查看，每个文件夹下面都有可能有，如果有不同的地方，及时修改。

环境默认打开了代理，如果使用curl命令查看本地项目结果，需要取消代理。
