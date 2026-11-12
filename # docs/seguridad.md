En alineación con los requerimientos del proyecto, esta herramienta implementa seguridad en dos frentes: la protección del propio software (prevención de errores e inyecciones) y la seguridad de las configuraciones de red que genera (Hardening).

## 1. Seguridad del Software y Validación de Entradas
- **Validación Estricta de Direccionamiento IP:** El backend (FastAPI) inspecciona cada segmento IP ingresado. Si detecta superposiciones o direcciones IP duplicadas entre interfaces L3 y SVIs de VLAN, bloquea la generación del script para evitar caídas de red por colisión de IPs.
- **Prevención de Bucles Físicos:** El lienzo de topología impide la creación de enlaces de un equipo hacia sí mismo.
- **Gestión de Secretos:** La herramienta no almacena contraseñas, tokens de APIs externas ni configuraciones de bases de datos en texto plano. 

## 2. Hardening Automatizado en la Generación de Scripts
El motor de *Infraestructura como Código (IaC)* inyecta automáticamente comandos de seguridad en todos los equipos generados:
- **Criptografía y Accesos:** Generación de llaves RSA (2048 bits), forzado de SSH versión 2 y cifrado irreversible de contraseñas de servicio en todas las marcas.
- **Cierre de Brechas Administrativas:** Deshabilitación de los servicios vulnerables `http server` y `http secure-server` en routers y switches.
- **Ciberdefensa L2 (NUEVO):** Implementación de opciones dinámicas para activar **DHCP Snooping** (mitigación de servidores Rogue DHCP), **Dynamic ARP Inspection** (prevención de ataques *Man-in-the-Middle*) y desactivación de protocolos de descubrimiento (CDP/LLDP) para evitar fuga de información de la topología física.
- **Túneles Seguros WAN:** Soporte para configuración de VPN IPsec *Site-to-Site* (AES-256 / SHA-256) en la interconexión de las sedes.
