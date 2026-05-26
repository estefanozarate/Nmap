# Nmap — Guias de Escaneo
#### Link: - [Redes de Computadoras - Tanenbaum 5ta Edicio](https://bibliotecavirtualapure.wordpress.com/wp-content/uploads/2015/06/redes_de_computadoras-freelibros-org.pdf)
Recursos de estudio sobre los principales tipos de escaneo de Nmap para hacking y pentesting. Dos documentos complementarios: uno detallado para aprender y uno visual para consulta rapida.

---

## Contenido

| Archivo | Descripcion | Paginas |
|---|---|---|
| `nmap_tipos_de_escaneo.pdf` | Guia detallada con explicacion a profundidad de cada tipo de escaneo | 13 paginas |
| `nmap_cheatsheet.pdf` | Cheatsheet visual en formato tarjetas para consulta rapida | 3 paginas |

---

## Que cubre

### Tipos de escaneo explicados

- **`-sU`** — UDP Scan: como funciona, por que es lento, que pasa al mandar UDP a un puerto TCP
- **`-Pn`** — Skip Host Discovery: cuando el host no responde ping
- **`-sn`** — Ping Scan: diferencia entre LAN y servidor remoto
- **`-sA`** — ACK Scan: como detecta firewalls y mapea sus reglas
- **`-sC`** — Default Scripts NSE: que scripts ejecuta por servicio
- **`-sN`** — NULL Scan: base teorica RFC 793
- **`-sF`** — FIN Scan: evasion de firewalls stateless
- **`-sX`** — Xmas Scan: por que no funciona en Windows
- **`-sO`** — Protocol Scan: deteccion de protocolos IP en capa 3

### Conceptos adicionales

- Respuestas TCP: `SYN/ACK`, `RST/ACK`, silencio y que significa cada una
- Diferencia entre `-sS` y `-sT`
- Combinaciones mas usadas en hacking real y CTFs
- Reglas de oro: `-T1` para sigilo, `-T4` para laboratorios, `2>/dev/null`

---

## Como usar estos documentos

**Para aprender:** empieza por `nmap_tipos_de_escaneo.pdf`. Cada seccion explica que hace el escaneo, como funciona a nivel de paquetes y para que sirve en hacking.

**Para consulta rapida:** usa `nmap_cheatsheet.pdf`. Cada tarjeta tiene el escaneo, su logica, cuando usarlo y el comando en una sola vista.

---

## Comandos de referencia rapida

```bash
# escaneo completo estandar
nmap -sS -sV -sC -O -p- -T4 192.168.1.1

# cuando el host no responde ping
nmap -sS -Pn -sV -p- 192.168.1.1

# descubrir hosts activos en la red
nmap -sn 192.168.1.0/24

# escaneo sigiloso y completo
nmap -sS -sV -O -Pn -n -T2 -p- 192.168.1.1

# mapear firewall antes de atacar
nmap -sA -p 80,443,22,8080,3306 192.168.1.1

# escaneo UDP servicios criticos
nmap -sU --top-ports 100 -T4 192.168.1.1

# buscar vulnerabilidades
nmap -sV --script=vuln 192.168.1.1

# evasion maxima
nmap -sX -T1 -n -Pn 192.168.1.1

# buscar binarios con SUID (post-explotacion)
find / -perm -4000 2>/dev/null
```

---

## Herramientas relacionadas

- [Nmap Official Docs](https://nmap.org/book/man.html)
- [NSE Scripts Library](https://nmap.org/nsedoc/)
- [Nmap Cheat Sheet - HackTricks](https://book.hacktricks.xyz/generic-methodologies-and-resources/pentesting-network/nmap-summary-esp)

---

## Disclaimer

Estos documentos son exclusivamente para fines educativos y uso en entornos controlados como laboratorios, CTFs y pentesting autorizado. El uso de estas tecnicas contra sistemas sin autorizacion explicita es ilegal.
