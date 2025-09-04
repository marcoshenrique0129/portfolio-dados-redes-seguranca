# Dia 02/09 — Redes (OSI/TCP/IP) + Packet Tracer + Wireshark

## Objetivos
- Montar **2 PCs + Switch + Roteador** e validar com `ping`.
- Capturar **HTTP local** no Wireshark (porta 8000) e identificar **GET / 200 OK**.

## Endereçamento (192.168.0.1/24)
- Router G0/0 → `192.168.0.1/24`
- PC0 → `192.168.1.02/24` (GW `192.168.1.1`)
- PC1 → `192.168.1.03/24` (GW `192.168.1.1`)

## Passos resumidos
1. Packet Tracer: montar topologia e configurar IPs; no router:
   ```plaintext
   enable
   conf t
   interface g0/0
    ip address 192.168.0.1 255.255.255.0
    no shutdown
   end
   write memory
   ```
2. Wireshark: rodar `python -m http.server 8000`, capturar na interface **Loopback**,
   filtrar `tcp.port == 8000`, abrir **Follow → TCP Stream**.
3. Salvar captura como `http-local.pcapng`.

## Evidências 
- ![Topologia] <img width="1183" height="868" alt="Rounter config" src="https://github.com/user-attachments/assets/3c480391-6905-4081-8a28-db0f932a8195" /><img width="694" height="700" alt="Router config 2" src="https://github.com/user-attachments/assets/4e710a71-f368-446b-a221-fec376951428" /><img width="1414" height="722" alt="VM config" src="https://github.com/user-attachments/assets/e46d3173-ccdd-420c-bd9e-3569d77c34b2" />



- ![Ping] <img width="1447" height="743" alt="Ping sucesso" src="https://github.com/user-attachments/assets/83a2453a-1108-4a7b-bf44-7c17b2b25a97" />
- ![Topologia]. <img width="1115" height="633" alt="Python HTTP Local" src="https://github.com/user-attachments/assets/744674d3-3d10-4407-afbd-abd0143de693" /><img width="1664" height="832" alt="WEB HTTP Local" src="https://github.com/user-attachments/assets/29637070-754e-4695-84c0-b42379deabae" /><img width="1309" height="199" alt="TCP Handshake" src="https://github.com/user-attachments/assets/7afb16be-7cf4-4e30-ab80-697c7179de32" />



- Captura: 

## Lições aprendidas
- Observei que ao realizar a requisição HTTP o protocolo TCP faz a verificação em 3 etapas e só depois da comunicação ter sido validada corretamente é liberado o acesso HTTP com o GET 200 ok 

## Próximos passos
- DHCP no roteador; VLANs; NAT.
