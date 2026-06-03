# 镜像构建

## 基本环境

- 框架：PyTorch 2.1.2
- Python：3.10
- CUDA：11.8
- 推荐 GPU：NVIDIA CUDA GPU，显存 8GB 及以上
- 推荐内存：16GB 及以上

## 构建过程

该镜像已预置远程 GPU 多媒体运行环境，创建 AutoDL 实例后即可使用。

无需手动执行代码 Clone 或依赖安装。

适用场景：

- 语音合成
- 视频同步处理
- 需要远程 GPU 参与的多媒体生成流程

## 环境验证

进入实例后，可使用以下命令查看 GPU 状态：

```bash
nvidia-smi
```

查看运行目录：

```bash
ls /root/flowlogic-remote-model
```

## 使用方法

1. 在 AutoDL 中使用该镜像创建实例。
2. 保持实例处于运行状态。
3. 在 AutoDL 实例页面复制 SSH 登录指令和密码。
4. 在需要连接该运行环境的本地程序中填写 SSH 信息。
5. 点击测试连接，确认远程运行环境可用。
6. 按照本地程序流程执行任务。

SSH 登录指令格式示例：

```bash
ssh -p 12345 root@connect.example.seetacloud.com
```

## 运行目录

远程运行环境位于：

```text
/root/flowlogic-remote-model/
```

主要目录：

```text
/root/flowlogic-remote-model/bin/          运行文件
/root/flowlogic-remote-model/resources/    运行资源
/root/flowlogic-remote-model/workspace/    临时任务文件和日志
```

## 说明

本地程序会通过 SSH 管理连接和端口转发，通常不需要手动开放公网 HTTP 服务端口。

如果连接失败，请检查：

- AutoDL 实例是否正在运行
- SSH 登录指令是否完整复制
- SSH 密码是否正确
- 本地网络是否可以连接 AutoDL SSH 服务
