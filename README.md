# PROYECTO2TELE
proyecto 2 telematica

Informe Técnico: Instalación y Configuración de Conectividad de Red
1. Objetivo del Informe
Este informe tiene como finalidad documentar la instalación, configuración y prueba de conectividad entre los distintos dispositivos de una red de área local segmentada por VLANs y enlaces punto a punto. Se verificó que los dispositivos pudieran comunicarse correctamente según la topología definida y se solucionaron problemas encontrados en la fase inicial.

2. Topología y Asignación de Direcciones IP
2.1. Dispositivos y Direccionamiento IP
Dispositivo	Dirección IP	VLAN/Subred
PC-A	192.168.20.10	VLAN LAN (192.168.20.0/24)
PC-B	192.168.20.11	VLAN LAN
PC-C	192.168.20.12	VLAN LAN
PC-01	40.0.20.10	VLAN 40 (40.0.20.0/24)
PC-02	50.0.20.10	VLAN 50 (50.0.20.0/24)
PC-03	40.0.20.11	VLAN 40
PC-04	50.0.20.11	VLAN 50
Server-WEB	192.168.100.3	VLAN DATA (192.168.100.0/24)
Server-MAIL	192.168.100.4	VLAN DATA
Server-DNS	192.168.100.2	VLAN DATA
WEB (Router)	13.0.0.2	Enlace p2p WEB-R1
R1	11.0.20.2 / 12.0.20.1 / 13.0.0.1	Core router
R2	12.0.20.2 / 14.0.20.2 / 15.0.20.1	Router de distribución
LAN	192.168.20.1 / 11.0.20.1	Enlaces LAN-R1
DATA	192.168.100.1 / 15.0.20.2	Enlace DATA-R2

3. Análisis de Conectividad
3.1. Resultados de pruebas
Conexión	Resultado
PC-A ↔ PC01	Éxito
PC-A ↔ PC04	Éxito
PC-B ↔ Server-WEB	Éxito
PC-C ↔ Server-MAIL	Éxito
PC01 ↔ PC02	Éxito
PC01 ↔ Server-MAIL	Éxito
PC02 ↔ PC04	Éxito
PC02 ↔ Server-DNS	Éxito
PC03 ↔ PC01	Éxito
PC04 ↔ Server-DNS	Éxito
Server-WEB ↔ R1	 Fallido 


4. Diagnóstico y Corrección del Error
4.1. Posibles causas del fallo
Falta de ruta estática o dinámica entre las redes 192.168.100.0 (Server-WEB) y 13.0.0.0 (interfaz R1).

Interfaz 13.0.0.2 del servidor WEB mal configurada o inactiva.

Interfaces físicas no habilitadas (no shutdown).

Subred mal definida o sin máscara correcta.

4.2. Soluciones implementadas
Verificación y habilitación de interfaces en el router R1 y en el dispositivo WEB.

Revisión de las rutas estáticas entre R1 y WEB.

Validación de la conectividad con comandos ping y traceroute.

Asignación correcta de IPs y máscaras de subred.

Confirmación de que las VLANs estén correctamente enrutadas mediante subinterfaces en R2.

5. Conclusión y Recomendaciones
Se logró configurar exitosamente la mayoría de las conexiones de red, lo que valida el correcto diseño de subredes, VLANs y enlaces punto a punto.

El único fallo detectado (Server-WEB ↔ R1) se solucionó aplicando buenas prácticas de troubleshooting: verificación de interfaces, enrutamiento y configuración IP.

Es recomendable mantener un mapa lógico actualizado y usar herramientas de monitoreo como Wireshark o comandos de diagnóstico para prevenir futuros problemas de conectividad.
