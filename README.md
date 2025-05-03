# Red Simulada en EVE-NG con Múltiples AS y Salida a Internet  
*(Simulated Network in EVE-NG with Multiple AS and Internet Access)*

Este proyecto presenta una topología de red compleja simulada en EVE-NG, integrando múltiples sistemas autónomos (AS) con protocolos IGP distintos (OSPF, RIP, EIGRP) y conectados mediante BGP. Se configura salida a Internet con NAT desde routers internos.

*(This project showcases a complex simulated network in EVE-NG, integrating multiple Autonomous Systems (AS) with different IGPs—OSPF, RIP, and EIGRP—interconnected via BGP. Internet access is provided to internal routers using NAT.)*

---

## 📷 Captura de la Topología / Network Diagram

![Topología de red](diagramas/topologia.png)

---

## 🧩 Componentes de la Red / Network Components

- **AS100** – Router Intermedio (BGP)
- **AS200** – R1, R2, R3 (OSPF + BGP)
- **AS250** – R4, R5, R6 (RIP + BGP)
- **AS300** – R7, R8, R9 (EIGRP + BGP)
- **NAT + DHCP** – Configurado en el Router Intermedio para salida a Internet

---

## 📁 Archivos de Configuración / Configuration Files

Los archivos `.cfg` de configuración están organizados en la carpeta `routers/`:

- `R_INTERMEDIO.cfg`: Router central con BGP y NAT
- `AS200.cfg`: Routers R1-R3 con OSPF + BGP
- `AS250.cfg`: Routers R4-R6 con RIP + BGP
- `AS300.cfg`: Routers R7-R9 con EIGRP + BGP
- `NAT_Config.cfg`: Configuración NAT y acceso a Internet

---

## 🧪 Pruebas Recomendadas / Recommended Tests

Desde R8 o R9:

```bash
ping 8.8.8.8
ping www.google.com
```

Desde cualquier AS:

```bash
show ip bgp
show ip route
```

---

## 🛠️ Notas Técnicas / Technical Notes

- Se corrigieron advertencias de `duplex mismatch` en interfaces FastEthernet con `duplex full` y `speed 100`.
- Redistribución implementada entre BGP ↔ OSPF, BGP ↔ RIP, y BGP ↔ EIGRP.
- Verificada conectividad entre todos los AS y salida a Internet desde hosts internos.
- Proyecto probado en entorno EVE-NG.

---

## 📂 Estructura del Repositorio / Repository Structure

```
/
├── README.md
├── diagramas/
│   └── topologia.png
├── routers/
│   ├── R_INTERMEDIO.cfg
│   ├── AS200.cfg
│   ├── AS250.cfg
│   ├── AS300.cfg
│   └── NAT_Config.cfg
```

---

## 👨‍💻 Autor / Author

Creado por santsavila  

---

🔒 Este repositorio es público solo para fines educativos. No se aceptan modificaciones externas.  
*(This repository is public for educational purposes only. External modifications are not accepted.)*