# Manual de Usuario - WAN Network Design & IaC Engine (v3.9)

## 1. Requisitos Previos
Para ejecutar esta herramienta de automatización, asegúrese de contar con el siguiente entorno:
- **Python 3.8+** instalado en el sistema.
- Navegador web moderno (Chrome, Edge, Firefox).
- Instalación de las dependencias del backend. Ejecute en su terminal:
  `pip install fastapi uvicorn pydantic`

## 2. Ejecución de la Herramienta
La plataforma utiliza una arquitectura desacoplada (Backend en Python/FastAPI y Frontend en HTML/JS).

**Paso 1: Levantar el Backend**
1. Abra una terminal en la carpeta principal del proyecto.
2. Ejecute el servidor de FastAPI con el siguiente comando:
   `python -m uvicorn Backend_Actualizado_v2:app --host 0.0.0.0 --port 8000`
3. El motor quedará a la escucha en `http://localhost:8000`.

**Paso 2: Abrir el Frontend**
1. Navegue a la carpeta del frontend.
2. Haga doble clic en el archivo `Frontend_Actualizado_v2.html` para abrirlo en su navegador. No requiere un servidor web adicional para el frontend.

## 3. Guía de Uso Paso a Paso

### A. Configuración Individual de Equipo (Pestaña 1)
1. **Parámetros Globales:** Ingrese la Superred base (ej. `10.240.0.0/16`), el Hostname y la IP de Gestión.
2. **Selección de Fabricante y Rol:** Elija el tipo de dispositivo (Router WAN, Switch L3, Switch L2) y el fabricante objetivo (Cisco, Huawei, Fortinet o MikroTik). *Nota: Las opciones de la interfaz se adaptarán automáticamente a su selección.*
3. **Módulos de Hardware:** Añada las tarjetas o módulos físicos de su equipo. Defina la cantidad de puertos y el formato de los slots.
4. **Segmentación (VLANs / Subinterfaces):** Agregue los segmentos de red necesarios. Si seleccionó "Router WAN", se habilitará la configuración de subinterfaces (802.1Q). Si seleccionó un Switch, se habilitarán las interfaces virtuales (SVI).
5. **Asignación de Interfaces:** Asigne el rol (L3 Routed, Access, Trunk) a cada puerto físico y vincúlelo con su VLAN o IP.
6. **Políticas de Ciberdefensa:** Marque las casillas de seguridad según requiera (OSPF, DHCP Snooping, Dynamic ARP Inspection, deshabilitar CDP/LLDP o túneles VPN IPsec).
7. **Generar:** Haga clic en **"Generar Script CLI & Plan IP"**. El sistema validará la lógica, calculará el Subnetting (VLSM), cotizará el presupuesto (BOM) y mostrará el script listo para copiar o descargar en `.txt`.

### B. Topología de Red e Interconexiones (Pestaña 2)
1. **Agregar Dispositivos:** Haga clic en "+ Agregar Dispositivo al Mapa", defina su nombre, rol y densidad de puertos.
2. **Enlazar Equipos:** En la sección "Agregar Conexión", seleccione un dispositivo origen, un puerto disponible, el dispositivo destino y su puerto de recepción. Haga clic en "+ Agregar Conexión".
3. **Validación:** El sistema impedirá crear bucles (conectar un equipo consigo mismo) y descontará en tiempo real los puertos ocupados.
4. **Exportar/Importar:** Puede guardar su diseño topológico haciendo clic en "Guardar/Exportar JSON" o cargar uno existente desde su disco local.
