# Herramienta de Redes WAN — Jean Devans Franco Fonseca (trabajo individual)
Materia: Interconexión de Redes WAN
Repositorio (público): [https://github.com/jeanDfranco/redes-wan-Franco](https://github.com/jeanDfranco/redes-wan-Franco)

## Qué hace esta herramienta
Es una plataforma web interactiva de automatización de infraestructura como código (IaC) y orquestación para redes WAN. Permite realizar el cálculo automático de direccionamiento IP mediante VLSM, el modelado gráfico e interactivo de topologías físicas con gestión de interfaces y la generación de scripts de configuración CLI multi-proveedor (Cisco, Huawei, Fortinet y MikroTik).

## Funciones
- Subnetting / IP Planning (IPv4 con cálculo dinámico de subredes, máscaras, wildcards y rangos VLSM).
- Carga de la topología (diseño de diagramas interactivos SVG, validación de densidad de puertos y exportación/importación en formato JSON).
- Generación de configuraciones: Cisco IOS-XE, Huawei VRP, Fortinet FortiOS y MikroTik RouterOS (Hardening, VLANs, SVIs, OSPF e IPsec VPN).
- Estimación automática de presupuesto de red y bill of materials (BOM).

## Cómo ejecutarla
1. **Iniciar Backend (FastAPI):**
   - Asegurarse de tener Python 3.10+ instalado.
   - Instalar dependencias: `pip install fastapi uvicorn pydantic`
   - Ejecutar el servidor: `Backend.py` abriendolo con Visual Studio (se iniciará en `http://localhost:8000`).
2. **Ejecutar Frontend:**
   - Abrir el archivo `Frontend.html` en cualquier navegador web moderno (Chrome, Edge, Firefox).

## Documentos
- docs/informe-corte2.pdf
- docs/capturas/ (01-subnetting.png ... 05-github-commits.png)

## Autoevaluación (marca Sí/No)
| Criterio                          | ¿Cumplido? | Evidencia            |
|-----------------------------------|------------|----------------------|
| Subnetting funciona               | Sí         | 01-subnetting.png    |
| Carga de topología                | Sí         | 02-topologia.png     |
| Config Cisco y Huawei             | Sí         | 03 / 04              |
| Config Fortinet y MikroTik (C3)   | Sí         | 06 / 07              |
| Ciberdefensa (politicas-ia.md)    | Sí         | 08-ciberdefensa.png  |
| Pruebas con % de confianza (C3)   | Sí         | docs/pruebas.md      |
