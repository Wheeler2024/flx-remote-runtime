# FLX Remote Runtime

这是一个用于 AutoDL 社区镜像的远程 GPU 运行环境说明仓库。

镜像本体由 AutoDL 提供，本仓库只保留公开说明文档，不包含运行二进制文件、模型文件、凭据或用户数据。

## 用途

该镜像提供一个已经配置好的 GPU 运行环境，可在 AutoDL 实例中启动，并通过本地桌面端使用 SSH 连接调用。

适用场景：

- 语音合成
- 视频同步处理
- 需要远程 GPU 参与的多媒体生成流程

## 使用方式

1. 在 AutoDL 中使用该社区镜像创建实例。
2. 保持 AutoDL 实例处于运行状态。
3. 在 AutoDL 实例页面复制 SSH 登录指令和密码。
4. 打开本地桌面端。
5. 开启远程服务器模式。
6. 填入 SSH 登录指令和密码。
7. 保存远程 SSH 配置。
8. 点击“测试连接”，确认远程运行环境可用。
9. 按照本地桌面端的正常流程执行任务。

SSH 登录指令示例：

```bash
ssh -p 12345 root@connect.example.seetacloud.com
```

## 运行目录

镜像中的远程运行环境位于：

```text
/root/flowlogic-remote-model/
```

主要目录：

```text
/root/flowlogic-remote-model/bin/          运行文件
/root/flowlogic-remote-model/resources/    运行资源
/root/flowlogic-remote-model/workspace/    临时任务文件和日志
```

`workspace` 目录用于保存任务执行过程中的临时文件。发布或更新镜像前，可以清理该目录下的运行态内容。

## 网络连接

本地桌面端通过 SSH 连接 AutoDL 实例，并自动建立所需的本地转发。

用户通常不需要手动开放公网 HTTP 服务端口。

如果连接测试失败，请检查：

- AutoDL 实例是否正在运行。
- SSH 登录指令是否完整复制。
- SSH 密码是否正确。
- 本地网络是否允许访问 AutoDL SSH 服务。

## 镜像说明

- 该镜像适用于支持 CUDA 的 AutoDL GPU 实例。
- 远程运行环境由本地桌面端负责启动和调用。
- 发布镜像前不要保留用户输入文件。
- 发布镜像前不要保留日志、临时文件、API Key、凭据或其他敏感信息。

## 问题排查

如遇到运行或连接问题，请准备以下信息：

- AutoDL GPU 型号
- AutoDL 镜像名称
- SSH 登录指令，注意不要包含密码
- 本地桌面端错误提示
- “测试连接”是否成功
