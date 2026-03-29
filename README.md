# recon-automator 🔍

Script Bash para automatizar la fase de reconocimiento en entornos de laboratorio y CTFs.  
Ejecuta nmap, identifica servicios, hace banner grabbing y genera un informe en Markdown listo para pegar en un writeup.

> ⚠️ **Disclaimer:** Úsalo únicamente en sistemas que te pertenecen o en los que tienes autorización expresa. Diseñado para entornos de laboratorio (DockerLabs, HTB, etc.).

---

## ⚡ Qué hace

1. **Ping sweep** — comprueba que el objetivo está activo
2. **Escaneo de puertos** — nmap rápido + escaneo detallado de puertos abiertos
3. **Detección de servicios y versiones** — flags `-sV -sC`
4. **Banner grabbing** — conecta a SSH, FTP y SMB y captura el banner
5. **Genera un informe** — archivo `recon_FECHA.md` listo para el writeup

---

## 🛠️ Requisitos

```bash
# Herramientas necesarias (ya incluidas en Kali Linux)
nmap
netcat (nc)
```

---

## 🚀 Uso

```bash
# Dar permisos de ejecución (solo la primera vez)
chmod +x recon.sh

# Ejecutar contra un objetivo
sudo ./recon.sh 172.17.0.2

# El informe se guarda automáticamente en /output/
```

---

## 📄 Ejemplo de output

```markdown
# Recon Report
**Target:** 172.17.0.2
**Date:** 2025-06-01 18:32:04

## Open Ports
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 8.9p1
80/tcp open  http    Apache httpd 2.4.52

## SSH Banner
SSH-2.0-OpenSSH_8.9p1 Ubuntu-3ubuntu0.6

## Notas
- Puerto 80 activo → enumerar directorios (gobuster)
- SSH versión 8.9 → revisar CVEs conocidos
```

---

## 📁 Estructura del proyecto

```
recon-automator/
├── recon.sh          ← script principal
├── output/           ← informes generados (en .gitignore)
└── README.md
```

---

## 🗺️ Roadmap

- [ ] Añadir enumeración web automática con gobuster
- [ ] Soporte para escaneo de rangos de red (/24)
- [ ] Output en JSON además de Markdown
