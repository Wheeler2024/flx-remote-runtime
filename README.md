# FLX Remote Runtime

Remote GPU runtime environment for AutoDL deployment.

This repository is the public description shell for an AutoDL community image.
The runnable environment is provided by the AutoDL image itself. This repository
does not contain model weights, private application code, activation data, API
keys, or customer assets.

## Purpose

The image provides a prepared GPU runtime that can be started on AutoDL and used
by a local desktop client through SSH. It is intended for users who want to run
GPU-heavy tasks on a remote AutoDL instance while keeping the desktop workflow on
their local machine.

## AutoDL Image Usage

1. Create an AutoDL instance from the published community image.
2. Keep the instance running while using the local desktop client.
3. Copy the SSH login command and password from the AutoDL instance page.
4. In the desktop client, enable remote server mode.
5. Paste the SSH login command and password.
6. Save the SSH settings.
7. Use "Test connection" to verify that the remote runtime is reachable.
8. Run the normal desktop workflow.

Example SSH command format:

```bash
ssh -p 12345 root@connect.example.seetacloud.com
```

## Runtime Layout

The image expects the runtime files to be available at:

```text
/root/flowlogic-remote-model/
```

Important paths:

```text
/root/flowlogic-remote-model/bin/          Runtime binaries
/root/flowlogic-remote-model/resources/    Runtime resources
/root/flowlogic-remote-model/workspace/    Temporary task files and logs
```

The `workspace` directory is used for temporary files generated during remote
tasks. These files are not required for image publication.

## Networking

The desktop client connects through SSH and creates the required local tunnel
automatically. Users do not need to manually expose a public HTTP service port.

If the connection test fails, check:

- The AutoDL instance is running.
- The SSH login command is copied exactly from AutoDL.
- The SSH password is correct.
- The local network allows outbound SSH connections.

## Image Notes

- The image is designed for CUDA-capable AutoDL GPU instances.
- The runtime should be started and controlled by the desktop client.
- Do not store customer input files in the image before publishing.
- Do not publish logs, temporary files, API keys, activation files, or secrets.

## Security Notes

This repository intentionally contains only public usage documentation. Private
runtime implementation, model files, secrets, customer data, and desktop client
code are not part of this repository.

## Support

For runtime setup or connection issues, provide the following information to the
support team:

- AutoDL GPU type
- AutoDL image name
- SSH login command, with password omitted
- Desktop client error message
- Whether "Test connection" succeeds
