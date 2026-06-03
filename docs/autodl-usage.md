# AutoDL Usage Guide

This guide describes how to use the FLX remote runtime image on AutoDL.

## Create An Instance

1. Open the AutoDL console.
2. Choose the published community image.
3. Select a CUDA-capable GPU instance.
4. Create and start the instance.

Recommended baseline:

- NVIDIA GPU with CUDA support
- 8 GB GPU memory or higher
- 16 GB system memory or higher

Higher GPU memory is recommended for longer tasks.

## Connect From The Desktop Client

After the AutoDL instance is running:

1. Copy the SSH login command from AutoDL.
2. Copy the SSH password from AutoDL.
3. Open the desktop client.
4. Open the model runtime settings.
5. Enable remote server mode.
6. Paste the SSH login command and password.
7. Save the remote SSH settings.
8. Click "Test connection".

The desktop client manages the SSH tunnel and remote runtime startup.

## Runtime State

Temporary task files are stored under:

```text
/root/flowlogic-remote-model/workspace/
```

These files can be cleared before saving or publishing an image. They are not
part of the required runtime environment.

## Troubleshooting

### Connection Failed

Check that:

- The AutoDL instance is running.
- The SSH login command includes the correct host and port.
- The SSH password is correct.
- The local machine can connect to AutoDL over SSH.

### Task Failed

Check that:

- The instance has enough GPU memory.
- The remote runtime directory exists.
- The desktop client is using the intended SSH settings.
- The AutoDL instance has not been stopped or recycled.

### Image Publishing Checklist

Before publishing or updating the image:

- Stop the remote runtime service.
- Clear logs.
- Clear temporary task inputs and outputs.
- Remove build artifacts and caches.
- Confirm no API keys or activation files are present.
