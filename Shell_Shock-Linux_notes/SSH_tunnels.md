# SSH tunnels
SSH tunnels, also known as SSH port forwarding, allow you to securely access services on a remote server or create encrypted connections between two machines through an SSH connection. SSH tunnels are especially useful for accessing services that may not be directly accessible due to network restrictions or for securing your communications over untrusted networks. There are three main types of SSH tunneling:

1. **Local Port Forwarding**: This allows you to forward a port on your local machine to a port on a remote server. It's often used to access a service on the remote server that is only accessible locally on the server itself.

2. **Remote Port Forwarding**: This allows you to forward a port on the remote server to a port on your local machine. It's useful when you want to make a service running on your local machine accessible from the remote server.

3. **Dynamic Port Forwarding (SOCKS Proxy)**: This creates a dynamic tunnel that acts as a SOCKS proxy, allowing you to route traffic from your local machine through the remote server. It's useful for securing your web browsing or accessing services on a remote network.

Here are examples of how to use each type of SSH tunnel:

**1. Local Port Forwarding**:

```bash
ssh -L local_port:remote_server:remote_port username@remote_server
```

- `local_port`: The port on your local machine to which you want to forward traffic.
- `remote_server`: The hostname or IP address of the remote server.
- `remote_port`: The port on the remote server to which you want to forward traffic.

Example:
```bash
ssh -L 8080:localhost:80 username@remote_server
```

In this example, when you access `http://localhost:8080` on your local machine, the traffic is securely forwarded to port 80 on the remote server.

**2. Remote Port Forwarding**:

```bash
ssh -R remote_port:local_machine:local_port username@remote_server
```

- `remote_port`: The port on the remote server to which you want to forward traffic.
- `local_machine`: The hostname or IP address of your local machine.
- `local_port`: The port on your local machine to which you want to forward traffic.

Example:
```bash
ssh -R 2222:localhost:22 username@remote_server
```

In this example, when someone connects to port 2222 on the remote server, the traffic is securely forwarded to port 22 (SSH) on your local machine.

**3. Dynamic Port Forwarding (SOCKS Proxy)**:

```bash
ssh -D local_port username@remote_server
```

- `local_port`: The port on your local machine that acts as the SOCKS proxy server (commonly 1080).

Example:
```bash
ssh -D 1080 username@remote_server
```

After establishing this dynamic tunnel, you can configure your applications (e.g., web browser) to use a SOCKS proxy at `localhost:1080`. This routes your application's network traffic through the remote server, encrypting it in the process.

SSH tunneling is a powerful tool for enhancing security and accessing remote services. However, it's important to use it responsibly and adhere to any network or security policies in place. Additionally, keep in mind that SSH tunneling requires an active SSH connection to maintain the tunnel, so you should keep the SSH session open while using the tunnel.
