**Blue Team** e **Red Team** são conceitos de **segurança da informação / cibersegurança** usados para simular ataques e melhorar a defesa de sistemas de TI.

A ideia vem do mundo militar: um time ataca e o outro defende.

---

# Blue Team vs Red Team

## 🔵 Blue Team (Time de Defesa)

O **Blue Team** é responsável por **defender** a empresa contra ataques.

Eles trabalham com:

* Monitoramento de logs
* SIEM
* Firewalls
* EDR / Antivírus
* Hardening de servidores
* Detecção de intrusão
* Resposta a incidentes
* Gestão de vulnerabilidades
* Patches de segurança
* Compliance (ex: PCI, LGPD)

**Resumo:**
O Blue Team tenta **impedir, detectar e responder** ataques.

Exemplo de ferramentas:

* Splunk
* QRadar
* Sentinel
* CrowdStrike
* Wazuh
* Zabbix
* Elastic
* Imperva
* Zscaler

---

## 🔴 Red Team (Time de Ataque)

O **Red Team** simula **hackers atacando a empresa** para encontrar falhas antes que hackers reais encontrem.

Eles fazem:

* Pentest (teste de invasão)
* Engenharia social
* Phishing
* Exploração de vulnerabilidades
* Movimentação lateral
* Escalada de privilégio
* Ataques a Active Directory
* Ataques a Cloud
* Exploração de APIs

**Resumo:**
O Red Team tenta **invadir** a empresa como um hacker faria.

Ferramentas comuns:

* Metasploit
* Nmap
* Burp Suite
* Cobalt Strike
* BloodHound
* Mimikatz
* Kali Linux

---

# 🟣 Purple Team

Existe também o **Purple Team**, que é quando os dois trabalham juntos.

| Team        | Função                                 |
| ----------- | -------------------------------------- |
| Red Team    | Atacar                                 |
| Blue Team   | Defender                               |
| Purple Team | Melhorar a defesa com base nos ataques |

O Purple Team pega o que o Red Team conseguiu invadir e ajuda o Blue Team a corrigir.

---

# Exemplo prático

Imagine uma empresa com servidores no GCP:

1. Red Team tenta invadir
2. Blue Team tenta detectar
3. Red Team consegue acesso
4. Blue Team não detectou
5. Purple Team analisa o que aconteceu
6. Criam alertas no SIEM
7. Atualizam firewall
8. Criam regras de segurança

Isso melhora a segurança da empresa.

---

# Salários e carreira (bem resumido)

| Área        | Perfil                            |
| ----------- | --------------------------------- |
| Blue Team   | Infra, Cloud, Logs, Monitoramento |
| Red Team    | Hacker, Pentest, Exploit          |
| Purple Team | Segurança avançada                |
| GRC         | Auditoria, Compliance, PCI        |

**Normalmente:**

* Infra / Cloud → Blue Team
* Programador / Hacker → Red Team
* Senior → Purple Team

---
