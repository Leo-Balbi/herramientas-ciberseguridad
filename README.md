# 🛡️ Pentesting Básico

Este repositorio contiene scripts, recursos y ejemplos para iniciarse en el mundo del pentesting y la ciberseguridad.  
Incluye ejemplos de escaneo de puertos, análisis de vulnerabilidades y automatización de tareas con Python.

## Contenido
- Escaneo de puertos con Nmap
- Scripts de automatización con Python
- Recursos y enlaces útiles

import socket

def scan_ports(target, ports):
    print(f"Escaneando {target}...")
    open_ports = []
    for port in ports:
        sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        sock.settimeout(0.5)
        result = sock.connect_ex((target, port))
        if result == 0:
            print(f"Puerto abierto: {port}")
            open_ports.append(port)
        sock.close()
    if not open_ports:
        print("No se encontraron puertos abiertos.")
    else:
        print(f"Puertos abiertos encontrados: {open_ports}")

if __name__ == "__main__":
    objetivo = input("Introduce la IP o dominio a escanear: ")
    # Puedes modificar la lista de puertos según tus necesidades
    puertos_comunes = [21, 22, 23, 25, 53, 80, 110, 139, 143, 443, 445, 3389]
    scan_ports(objetivo, puertos_comunes)
