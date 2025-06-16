# 🚀 Sistema de Gestión para Telecam.net

## 📌 Descripción del Proyecto

Sistema de gestión integral para la empresa de telecomunicaciones **Telecam.net**, especializada en servicios de:

- Internet de alta velocidad  
- Televisión por cable e IPTV  
- Telefonía fija y móvil  

El sistema permite administrar eficientemente:

- Información de clientes y planes contratados  
- Facturación y estados de pago  
- Solicitudes de soporte técnico  
- Asignación de técnicos por zonas  
- Cobertura de servicios en el área metropolitana de Bucaramanga  

---

## 🛠 Configuración de la Base de Datos

### Requisitos previos

- MongoDB 4.4+ instalado  
- MongoShell o MongoDB Compass  
- Archivos JSON del repositorio  

### 1. Crear la base de datos

```bash
use telecam_net

### 2. Importar las colecciones

mongoimport --db telecam_net --collection clientes --file clientes.json --jsonArray
mongoimport --db telecam_net --collection facturas --file facturas.json --jsonArray
mongoimport --db telecam_net --collection planes --file planes.json --jsonArray
mongoimport --db telecam_net --collection solicitudes_soporte --file solicitudes_soporte.json --jsonArray
mongoimport --db telecam_net --collection tecnicos --file tecnicos.json --jsonArray
mongoimport --db telecam_net --collection zonas_cobertura --file zonas_cobertura.json --jsonArray

### 📊 25 Consultas con Expresiones Regulares
## Clientes (1-5)





