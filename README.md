# 🐧 Trabajo Práctico Final - Administración de Sistemas Linux con Vagrant

![Ubuntu](https://img.shields.io/badge/Ubuntu-22.04-E95420?style=for-the-badge&logo=ubuntu&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)
![Apache](https://img.shields.io/badge/Apache-D22128?style=for-the-badge&logo=apache&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white)
![PHP](https://img.shields.io/badge/PHP-777BB4?style=for-the-badge&logo=php&logoColor=white)
![Grafana](https://img.shields.io/badge/Grafana-F46800?style=for-the-badge&logo=grafana&logoColor=white)
![Prometheus](https://img.shields.io/badge/Prometheus-E6522C?style=for-the-badge&logo=prometheus&logoColor=white)

**Asignatura:** Arquitectura y Sistemas Operativos
**Integrantes del Equipo:**
- Zarymar Ronderos
- Angel Farina

---

## 📋 Índice

1. [Descripción del Proyecto](#descripción-del-proyecto)
2. [Objetivos Cumplidos](#objetivos-cumplidos)
3. [Estructura del Repositorio](#estructura-del-repositorio)
4. [Ejercicios Realizados](#ejercicios-realizados)
5. [Ejercicio Bonus - Servidor LAMP](#ejercicio-bonus---servidor-lamp)
6. [Tecnologías Utilizadas](#tecnologías-utilizadas)
7. [Capturas de Evidencia](#capturas-de-evidencia)
8. [Comandos Principales](#comandos-principales)
9. [Problemas Encontrados y Soluciones](#problemas-encontrados-y-soluciones)
10. [Conclusiones](#conclusiones)

---

## 📖 Descripción del Proyecto

Este trabajo práctico implementa un entorno Linux virtualizado con Vagrant para practicar administración de sistemas, gestión de usuarios, volúmenes lógicos (LVM), contenedores Docker y servicios web.

El proyecto simula un entorno de trabajo colaborativo donde tres roles diferentes (Administrador, Desarrollador y Operador) trabajan en conjunto utilizando Git como sistema de control de versiones.

---

## ✅ Objetivos Cumplidos

- ✅ **Virtualización:** Configuración de VM con Vagrant y VirtualBox
- ✅ **Control de Versiones:** Uso colaborativo de Git (clone, add, commit, push, pull)
- ✅ **Gestión de Usuarios:** Creación de usuarios, grupos y permisos en Linux
- ✅ **LVM:** Configuración de Physical Volumes, Volume Groups y Logical Volumes
- ✅ **Gestión de Archivos:** Operaciones avanzadas con archivos y directorios
- ✅ **Contenedores:** Implementación de stack Docker con Docker Compose
- ✅ **Monitoreo:** Configuración de Grafana, Prometheus y Loki
- ✅ **Debugging:** Identificación y corrección de errores en archivos de configuración
- ✅ **BONUS:** Implementación completa de servidor LAMP (Linux + Apache + MySQL + PHP)

---

## 📁 Estructura del Repositorio
```
proyecto/
├── README.md                          # Este archivo
├── Vagrantfile                        # Configuración de la VM
├── informacion/
│   ├── ip_vm.txt                     # IPs de las VMs de cada alumno
│   └── system_info.txt               # Información del sistema (fastfetch)
├── permisos/
│   ├── usuarios_[apellido].txt       # Info de usuarios por alumno
│   └── verificacion_permisos.txt     # Verificación de permisos configurados
├── lvm/
│   └── lvm-[apellido].txt           # Verificación de LVM por alumno
├── archivos/
│   └── verificacion_archivos.txt    # Verificación de gestión de archivos
├── contenedores/
│   ├── docker-compose.yml           # Configuración Docker Compose (CORREGIDO)
│   ├── prometheus.yml               # Configuración Prometheus (CORREGIDO)
│   ├── errores_encontrados.md       # Documentación de errores y soluciones
│   ├── logs_completos.txt           # Logs de todos los contenedores
│   └── verificacion_contenedores.txt # Verificación de servicios Docker
├── lamp/                            # EJERCICIO BONUS
│   ├── verificacion_lamp.txt        # Verificación del servidor LAMP
│   ├── comandos_ejecutados.md       # Documentación de comandos
│   └── capturas/
│       ├── index_html.png
│       ├── info_php.png
│       └── test_db_php.png
└── evidencias/
    ├── history_[apellido].txt       # Historial de comandos ejecutados
    └── capturas/                    # Capturas de pantalla organizadas
        ├── docker/
        ├── lamp/
        ├── lvm/
        ├── permisos/
        └── general/
```

---

## 🔧 Ejercicios Realizados

### 0️⃣ Descubrimiento de IP de la VM

**Objetivo:** Identificar la dirección IP de la máquina virtual en modo bridge.

**Comandos utilizados:**
```bash
ip addr show
hostname -I
ping -c 4 8.8.8.8
```

**Resultado:** IP identificada y documentada en `informacion/ip_vm.txt`

---

### 1️⃣ Configuración Inicial y Repositorio

**Objetivo:** Configurar Git y crear estructura del proyecto.

**Tareas realizadas:**
- Clonación del repositorio desde GitHub
- Configuración de credenciales Git
- Creación de estructura de directorios

**Comandos principales:**
```bash
git clone https://github.com/angel-farina/practica-linux--Ronderos_Farina-equipo_4-
git config --global user.name "Nombre"
git config --global user.email "email@example.com"
mkdir -p informacion permisos lvm archivos contenedores
```

---

### 2️⃣ Fastfetch Colaborativo

**Objetivo:** Documentar información del sistema de cada alumno.

**Comando utilizado:**
```bash
fastfetch >> informacion/system_info.txt
```

**Resultado:** Archivo con información detallada del sistema de cada integrante.

![Fastfetch Output](evidencias/capturas/fastfetch.jpg)

---

### 3️⃣ Gestión de Permisos (Rol A - Administrador)

**Objetivo:** Configurar usuarios, grupos y permisos en Linux.

**Tareas realizadas:**
- Creación de directorio personal con archivos privados y públicos
- Creación de usuarios locales (estudiante1, estudiante2, estudiante3)
- Creación del grupo `equipotrabajo`
- Configuración de directorio colaborativo con permisos 770

**Comandos clave:**
```bash
mkdir /home/vagrant/[farina]_espacio
chmod 600 privado.txt
chmod 644 publico.txt
sudo groupadd equipotrabajo
sudo chmod 770 /tmp/colaborativo
```

**Conceptos aplicados:**
- Permisos: lectura (r), escritura (w), ejecución (x)
- Notación octal: 600, 644, 770
- Grupos y colaboración entre usuarios

---

### 4️⃣ Operaciones con LVM (Rol A - Administrador)

**Objetivo:** Gestionar volúmenes lógicos con LVM para almacenamiento flexible.

**¿Qué es LVM?**  
LVM (Logical Volume Manager) permite gestionar discos de forma más flexible que las particiones tradicionales, permitiendo redimensionar, crear snapshots y agregar discos sin perder datos.

**Pasos realizados:**
1. Identificación del disco adicional (`/dev/sdc`)
2. Creación de Physical Volume (PV)
3. Creación de Volume Group (VG)
4. Creación de Logical Volume (LV) de 1.5GB
5. Formateo con ext4
6. Montaje y configuración en `/etc/fstab`

**Comandos ejecutados:**
```bash
sudo pvcreate /dev/sdc
sudo vgcreate vg_datos_[farina] /dev/sdc
sudo lvcreate -L 1.5G -n lv_storage_[farina] vg_datos_[farina]
sudo mkfs.ext4 /dev/vg_datos_[farina]/lv_storage_[farina]
sudo mount /dev/vg_datos_[farina]/lv_storage_[farina] /mnt/lvm_storage_[farina]
```

![Disk Space](evidencias/capturas/df_h.jpg)

---

### 5️⃣ Gestión de Archivos y Directorios (Rol A - Administrador)

**Objetivo:** Realizar operaciones avanzadas con archivos y directorios.

**Estructura creada:**
```
/mnt/lvm_storage_[farina]/
├── proyectos/
│   ├── activos/          # Archivos 1-5
│   └── archivados/       # Archivos 6-8
├── respaldos/            # Backup archivos 9-10
└── temporal/             # Directorio vacío final
```

**Operaciones realizadas:**
- Creación de 10 archivos de prueba
- Copia de archivos 1-5 a `activos/`
- Movimiento de archivos 6-8 a `archivados/`
- Backup de archivos 9-10 a `respaldos/`
- Limpieza del directorio temporal

![Estructura de Archivos](evidencias/capturas/tree.jpg)

---

### 6️⃣ Contenedores y Monitoreo (Rol B - Desarrollador)

**Objetivo:** Implementar stack de contenedores Docker con servicios de monitoreo.

**Servicios implementados:**
1. **Nginx** - Servidor web (puerto 8081)
2. **Redis** - Base de datos en memoria (puerto 6379)
3. **PostgreSQL** - Base de datos relacional (puerto 5432)
4. **Prometheus** - Recolección de métricas (puerto 9090)
5. **Loki** - Agregación de logs (puerto 3100)
6. **Grafana** - Visualización (puerto 3000)

**Errores encontrados y corregidos:**

#### Error 1: Red inconsistente
- **Problema:** Redis usaba `monitoring-network` mientras otros servicios usaban `monitoring`
- **Solución:** Unificar todas las redes a `monitoring`

#### Error 2: Volumen con nombre inconsistente
- **Problema:** Grafana declaraba `grafana-data` pero se definía `grafana-storage`
- **Solución:** Unificar nombres de volúmenes

#### Error 3: Target de Prometheus
- **Problema:** Nginx no expone métricas en puerto 9113 por defecto
- **Solución:** Comentar job de nginx o agregar exporter

**Comandos de debugging:**
```bash
docker-compose config          # Validar sintaxis
docker-compose logs           # Ver errores
docker ps                     # Verificar contenedores
docker-compose up -d          # Levantar servicios
```

![Docker PS](evidencias/capturas/docker_ps.jpg)
![Grafana Datasources](evidencias/capturas/grafana_data_sources.jpg)
![Prometheus Targets](evidencias/capturas/grafana_dashboard1.jpg)
![Grafana Dashboard](evidencias/capturas/grafana_dashboard2.jpg)

---

## 🚀 Ejercicio Bonus - Servidor LAMP

**Objetivo:** Implementar un servidor web completo con Linux, Apache, MySQL y PHP.

### Componentes Instalados

#### 🐧 Linux (Ubuntu 22.04)
Sistema operativo base proporcionado por Vagrant.

#### 🌐 Apache 2.4
Servidor web HTTP que sirve las páginas.

**Configuración:**
```bash
sudo apt-get install -y apache2
sudo a2enmod rewrite
sudo a2enmod php8.1
sudo systemctl enable apache2
```

#### 🗄️ MySQL 8.0
Sistema de gestión de bases de datos relacional.

**Configuración:**
```bash
sudo apt-get install -y mysql-server
sudo mysql_secure_installation

# Creación de base de datos
CREATE DATABASE tp_final_db;
CREATE USER 'alumno'@'localhost' IDENTIFIED BY 'practica123';
GRANT ALL PRIVILEGES ON tp_final_db.* TO 'alumno'@'localhost';
```

#### 🐘 PHP 8.1
Lenguaje de programación del lado del servidor.

**Módulos instalados:**
- php
- libapache2-mod-php
- php-mysql

### Archivos Web Creados

#### 1. index.html
Página principal con diseño moderno usando gradientes CSS.

**Características:**
- Diseño responsive
- Gradiente púrpura-azul
- Grid de componentes tecnológicos
- Animaciones hover

![Index HTML](evidencias/capturas/index_html.jpg)

#### 2. info.php
Muestra información completa de PHP usando `phpinfo()`.

![Info PHP](evidencias/capturas/info_php.jpg)

#### 3. test_db.php
Prueba la conexión a la base de datos MySQL.

**Funcionalidad:**
- Conecta a MySQL
- Verifica credenciales
- Muestra estado de conexión

![Test DB](evidencias/capturas/test_db_php.jpg)

### Verificación de Servicios

**Apache:**
```bash
sudo systemctl status apache2
# ● apache2.service - The Apache HTTP Server
#    Loaded: loaded
#    Active: active (running)
```

**MySQL:**
```bash
sudo systemctl status mysql
# ● mysql.service - MySQL Community Server
#    Loaded: loaded
#    Active: active (running)
```

**Puertos en escucha:**
```bash
sudo netstat -tlnp | grep -E '(apache|mysql)'
# tcp6  0  0 :::80    :::*  LISTEN  1234/apache2
# tcp   0  0 127.0.0.1:3306  0.0.0.0:*  LISTEN  5678/mysqld
```

![Apache Status](evidencias/capturas/apache_status.jpg)
![MySQL Status](evidencias/capturas/mysql_status.jpg)

---

## 🛠️ Tecnologías Utilizadas

| Tecnología | Versión | Propósito |
|------------|---------|-----------|
| Ubuntu | 22.04 LTS | Sistema operativo base |
| Vagrant | 2.x | Virtualización y aprovisionamiento |
| VirtualBox | 6.x/7.x | Hipervisor |
| Git | 2.x | Control de versiones |
| Docker | 24.x | Contenedores |
| Docker Compose | 2.x | Orquestación de contenedores |
| LVM2 | 2.x | Gestión de volúmenes lógicos |
| Apache | 2.4 | Servidor web |
| MySQL | 8.0 | Base de datos |
| PHP | 8.1 | Lenguaje de programación |
| Nginx | Alpine | Servidor web ligero |
| Redis | Alpine | Base de datos en memoria |
| PostgreSQL | Alpine | Base de datos relacional |
| Grafana | Latest | Visualización de métricas |
| Prometheus | Latest | Monitoreo y métricas |
| Loki | Latest | Agregación de logs |

---

## 📸 Capturas de Evidencia

Todas las capturas de pantalla están organizadas en la carpeta `evidencias/capturas`:

### Docker
- `docker_ps.png` - Contenedores en ejecución
- `grafana_datasources.png` - Datasources configurados
- `grafana_dashboard.png` - Dashboard funcional
- `prometheus_targets.png` - Targets monitoreados

### LAMP
- `index_html.png` - Página principal
- `info_php.png` - Información de PHP
- `test_db_php.png` - Conexión a MySQL
- `apache_status.png` - Estado del servicio Apache
- `mysql_status.png` - Estado del servicio MySQL

### LVM
- `lvm_verificacion.png` - Configuración de volúmenes
- `df_h.png` - Espacio en disco

### Permisos
- `permisos_verificacion.png` - Usuarios y grupos configurados

### General
- `ip_vm.png` - IP de la máquina virtual
- `fastfetch.png` - Información del sistema
- `estructura_archivos.png` - Árbol de directorios

---

## 💻 Comandos Principales

### Git
```bash
git clone [URL]
git add .
git commit -m "mensaje"
git push
git pull
```

### Permisos
```bash
chmod 600 archivo          # Solo dueño lee/escribe
chmod 644 archivo          # Dueño escribe, otros leen
chmod 770 directorio       # Dueño y grupo control total
chown usuario:grupo archivo
```

### LVM
```bash
sudo pvcreate /dev/sdc
sudo vgcreate nombre_vg /dev/sdc
sudo lvcreate -L tamaño -n nombre_lv nombre_vg
sudo mkfs.ext4 /dev/vg/lv
sudo mount /dev/vg/lv /punto/montaje
```

### Docker
```bash
docker-compose up -d       # Levantar servicios
docker-compose down        # Detener servicios
docker ps                  # Ver contenedores
docker-compose logs        # Ver logs
docker-compose config      # Validar sintaxis
```

### Apache
```bash
sudo systemctl start apache2
sudo systemctl enable apache2
sudo systemctl status apache2
```

### MySQL
```bash
sudo mysql
sudo mysql -u usuario -p
sudo systemctl status mysql
```

---

## ⚠️ Problemas Encontrados y Soluciones

### Problema 1: Docker Compose - Redes Inconsistentes
**Síntoma:** Servicios no pueden comunicarse entre sí  
**Causa:** Redis usaba `monitoring-network` mientras otros usaban `monitoring`  
**Solución:** Unificar todos los servicios a la red `monitoring`

### Problema 2: Docker Compose - Volúmenes con Nombres Diferentes
**Síntoma:** Grafana no persiste datos  
**Causa:** Volumen declarado como `grafana-storage` pero usado como `grafana-data`  
**Solución:** Cambiar referencias para que usen el mismo nombre

### Problema 3: Prometheus Targets DOWN
**Síntoma:** Target de nginx aparece como DOWN en Prometheus  
**Causa:** Nginx Alpine no expone métricas por defecto en puerto 9113  
**Solución:** Comentar el job de nginx o agregar nginx-prometheus-exporter

### Problema 4: Permisos en Apache
**Síntoma:** Error 403 Forbidden al acceder a archivos  
**Causa:** Permisos incorrectos en `/var/www/html/`  
**Solución:**
```bash
sudo chown -R www-data:www-data /var/www/html/
sudo chmod -R 755 /var/www/html/
```

---

## 📚 Conclusiones

### Aprendizajes Técnicos

1. **Virtualización:** Comprendimos cómo Vagrant simplifica la creación y gestión de máquinas virtuales, permitiendo replicar entornos de desarrollo de forma consistente.

2. **Control de Versiones:** Aprendimos a trabajar colaborativamente con Git, manejando commits, push, pull y resolviendo conflictos básicos.

3. **Administración de Linux:**
   - Gestión de usuarios, grupos y permisos
   - Comprensión profunda del sistema de permisos (rwx)
   - Uso de comandos básicos y avanzados

4. **LVM (Logical Volume Manager):**
   - Flexibilidad en la gestión de almacenamiento
   - Ventajas sobre particiones tradicionales
   - Capacidad de redimensionar volúmenes sin perder datos

5. **Contenedores Docker:**
   - Arquitectura de microservicios
   - Orquestación con Docker Compose
   - Networking entre contenedores
   - Gestión de volúmenes persistentes

6. **Debugging:**
   - Identificación de errores en archivos de configuración
   - Uso de logs para diagnóstico
   - Resolución sistemática de problemas

7. **Stack LAMP:**
   - Configuración de un servidor web completo
   - Integración de Apache, MySQL y PHP
   - Creación de aplicaciones web dinámicas

### Trabajo en Equipo

- Distribución efectiva de roles y responsabilidades
- Comunicación constante para resolver problemas
- Uso de Git como herramienta de colaboración
- Documentación clara para facilitar el trabajo del equipo

### Desafíos Superados

1. **Errores intencionales en Docker Compose:** Nos obligaron a leer logs, validar configuraciones y pensar críticamente sobre la arquitectura de los servicios.

2. **Configuración de LVM:** Requeríó comprensión de conceptos abstractos (PV, VG, LV) y su aplicación práctica.

3. **Integración de servicios:** Conectar Grafana con Prometheus y Loki demostró la importancia del networking correcto.

4. **Servidor LAMP completo:** Integración de múltiples tecnologías en un stack funcional.

### Aplicaciones Prácticas

Este trabajo nos preparó para:
- Administrar servidores Linux en entornos reales
- Implementar soluciones con contenedores
- Configurar sistemas de monitoreo
- Diagnosticar y resolver problemas técnicos
- Trabajar en equipos de DevOps

---

---

## 📄 Licencia

Este proyecto fue realizado con fines educativos para la asignatura de Arquitectura y Sistemas Operativos.