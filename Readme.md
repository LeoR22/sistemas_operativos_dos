# Proyecto 2 - Sistemas Operativos: Infraestructura con Vagrant, Nginx, Prometheus y Grafana

## 📌 Descripción
Este proyecto implementa dos máquinas virtuales usando **Vagrant + VirtualBox**:
- **web**: Servidor Nginx que despliega una página HTML personalizada.
- **monitor**: Servidor de monitoreo con **Prometheus** y **Grafana**.

El objetivo es aprender a provisionar servicios básicos en entornos virtualizados y validar su funcionamiento desde el host.

---

## ⚙️ Requisitos previos
- [VirtualBox](https://www.virtualbox.org/) instalado.
- [Vagrant](https://www.vagrantup.com/) instalado.
- Carpeta del proyecto con el `Vagrantfile` y los playbooks de Ansible.

---

## 🚀 Levantar las máquinas
Desde la carpeta del proyecto:
```
vagrant up
```

Esto creará dos VMs:

web → Nginx en el puerto 8080 del host.

monitor → Prometheus en el puerto 9090 y Grafana en el puerto 3000.

🖥️ Acceso a las VMs
powershell
vagrant ssh web
vagrant ssh monitor
🌐 Validación de servicios
Nginx (VM web)
Dentro de la VM:

```
systemctl status nginx --no-pager
curl http://localhost/
```
Desde el host:

Código
```
http://localhost:8080
```
👉 Debe mostrar tu index.html personalizado.

Prometheus (VM monitor)
Dentro de la VM:

```
systemctl status prometheus --no-pager
curl http://localhost:9090
```
Desde el host:

Código
```
http://localhost:9090
```
👉 Debe mostrar la interfaz web de Prometheus.

Grafana (VM monitor)
Dentro de la VM:

```
systemctl status grafana-server --no-pager
```
Desde el host:

Código

http://localhost:3000

👉 Interfaz de Grafana (usuario: admin, contraseña: admin).

### 📂 Estructura del proyecto

```
proyectoSO_dos_VMS/
├── Vagrantfile
├── ansible-web/
│   ├── playbook_web.yml
│   └── files/index.html
└── ansible-monitor/
    ├── playbook_monitor.yml
    └── inventory.ini
```

✅ Evidencias sugeridas
Captura de systemctl status para cada servicio.

Salida de curl http://localhost/ en la VM web.

### Navegador mostrando:

http://localhost:8080 → Nginx.

http://localhost:9090 → Prometheus.

http://localhost:3000 → Grafana.



### ✨ Conclusión
Este proyecto demuestra cómo levantar servicios web y de monitoreo en entornos virtualizados con Vagrant, asegurando reproducibilidad y facilidad de validación.