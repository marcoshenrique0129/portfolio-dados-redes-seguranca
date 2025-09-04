# Dia 02/09 — Redes (OSI/TCP/IP) + Packet Tracer + Wireshark

## Objetivos
- Montar **2 PCs + Switch + Roteador** e validar com `ping`.
- Capturar **HTTP local** no Wireshark (porta 8000) e identificar **GET / 200 OK**.

## Endereçamento (sugestão /24)
- Router G0/0 → `192.168.1.1/24`
- PC0 → `192.168.1.10/24` (GW `192.168.1.1`)
- PC1 → `192.168.1.11/24` (GW `192.168.1.1`)

## Passos resumidos
1. Packet Tracer: montar topologia e configurar IPs; no router:
   ```plaintext
   enable
   conf t
   interface g0/0
    ip address 192.168.1.1 255.255.255.0
    no shutdown
   end
   write memory
   ```
2. Wireshark: rodar `python -m http.server 8000`, capturar na interface **Loopback**,
   filtrar `tcp.port == 8000`, abrir **Follow → TCP Stream**.
3. Salvar captura como `http-local.pcapng`.

## Evidências (adicione seus arquivos aqui)
- ![Topologia](evidencias/topologia.png)
- ![Ping](evidencias/ping_sucesso.png)
- Captura: [`evidencias/http-local.pcapng`](evidencias/http-local.pcapng)

## Lições aprendidas
- (escreva 2–3 bullets)

## Próximos passos
- DHCP no roteador; VLANs; NAT.
