# coturn-for-coolify

Servidor TURN/STUN (coturn) pronto para deploy na [Coolify](https://coolify.io).

## Variáveis de Ambiente

| Variável        | Descrição                 | Padrão             |
| --------------- | ------------------------- | ------------------ |
| `REALM`         | Domínio do servidor TURN  | `turn.example.com` |
| `TURN_USER`     | Usuário para autenticação | `user`             |
| `TURN_PASSWORD` | Senha para autenticação   | `password`         |
| `EXTERNAL_IP`   | IP público do servidor    | _(vazio)_          |

## Deploy na Coolify

1. Crie um novo serviço na Coolify usando **Docker Compose**.
2. Aponte para este repositório.
3. Configure as variáveis de ambiente (`REALM`, `TURN_USER`, `TURN_PASSWORD`, `EXTERNAL_IP`).
4. **Importante:** O `network_mode: host` é necessário para o range de portas UDP (49152-49252). Na Coolify, certifique-se de que o servidor tem essas portas abertas no firewall.
5. Faça o deploy!

## Portas

| Porta       | Protocolo | Uso                 |
| ----------- | --------- | ------------------- |
| 3478        | TCP/UDP   | TURN/STUN           |
| 5349        | TCP/UDP   | TURN/STUN sobre TLS |
| 49152-49252 | UDP       | Relay de mídia      |
