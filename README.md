# 🚀 Sistema de Gestión Telecam.net - MongoDB


## Estructura de archivos:
```python
📁 telecam_net/
├── clientes.json          # 30 documentos - Información de clientes
├── facturas.json          # 30 documentos - Registros de facturación
├── planes.json            # 30 documentos - Catálogo de servicios
├── solicitudes_soporte.json # 30 documentos - Tickets de soporte
├── tecnicos.json          # 30 documentos - Recurso técnico
└── zonas_cobertura.json   # 30 documentos - Áreas de servicio
```

### **1. Configuración inicial**
```javascript
use telecam_net;
```

### **2. Importar colecciones**
(Ejecutar en la terminal)

```bash
mongoimport --db telecam_net --collection clientes --file clientes.json --jsonArray
mongoimport --db telecam_net --collection facturas --file facturas.json --jsonArray
mongoimport --db telecam_net --collection planes --file planes.json --jsonArray
mongoimport --db telecam_net --collection solicitudes_soporte --file solicitudes_soporte.json --jsonArray
mongoimport --db telecam_net --collection tecnicos --file tecnicos.json --jsonArray
mongoimport --db telecam_net --collection zonas_cobertura --file zonas_cobertura.json --jsonArray
```

---


### **3. Consultas con expresiones regulares documentadas**

---

### **Clientes**

> Consulta 1: Buscar clientes cuyos nombres empiezan por "Mar"

```javascript
db.clientes.find({ "nombre": { "$regex": "^Mar" } })
```
Esta consulta permite autocompletar nombres en formularios de búsqueda.

---

> Consulta 2: Buscar clientes con correos de Gmail

```javascript
db.clientes.find({ "correo": { "$regex": "@gmail\.com$" } })
```
Útil para campañas de email marketing dirigidas.

---

> Consulta 3: Buscar clientes ubicados en Floridablanca

```javascript
db.clientes.find({ "ciudad": { "$regex": "blanca$" } })
```
Facilita análisis geográfico de la base de clientes.

---

> Consulta 4: Buscar números de teléfono que empiezan con 310

```javascript
db.clientes.find({ "telefono": { "$regex": "^310" } })
```
Identificación de operadoras móviles comunes entre los clientes.

---

> Consulta 5: Buscar direcciones que contengan "Cra" o "Carrera"

```javascript
db.clientes.find({ "direccion": { "$regex": "Cra|Carrera", "$options": "i" } })
```
Ayuda a organizar rutas de visita técnica por nomenclatura urbana.

---

### **Facturas**

> Consulta 6: Buscar facturas con estado "pendiente" o "vencida"

```javascript
db.facturas.find({ "estado_pago": { "$regex": "pendiente|vencida" } })
```
Soporte para procesos de cobranza automatizada.

---

> Consulta 7: Buscar facturas de planes de internet (que contienen "MB")

```javascript
db.facturas.find({ "plan": { "$regex": "MB" } })
```
Permite calcular ingresos por servicios de internet.

---

> Consulta 8: Buscar facturas emitidas en junio de 2024

```javascript
db.facturas.find({ "fecha_emision": { "$regex": "^2024-06" } })
```
Reportes contables mensuales.

---

> Consulta 9: Buscar facturas cuyo monto termine en "900"

```javascript
db.facturas.find({ "monto": { "$regex": "900$" } })
```
Análisis de estrategias de precios terminados en 900.

---

> Consulta 10: Buscar facturas con código inicial "FAC-0"

```javascript
db.facturas.find({ "id_factura": { "$regex": "^FAC-0" } })
```
Revisión de los primeros registros facturados.

---

### **Planes**

> Consulta 11: Buscar planes que contengan "Fibra" en la descripción

```javascript
db.planes.find({ "descripcion": { "$regex": "Fibra", "$options": "i" } })
```
Identificación de servicios premium para mantenimiento.

---

> Consulta 12: Buscar planes con velocidad entre 100MB y 999MB

```javascript
db.planes.find({ "velocidad": { "$regex": "^[1-9][0-9]{2}MB" } })
```
Segmentación de clientes que requieren alto rendimiento.

---

> Consulta 13: Buscar planes tipo "Tripleplay" o "Dobleplay"

```javascript
db.planes.find({ "tipo": { "$regex": "Tripleplay|Dobleplay" } })
```
Análisis de los paquetes más populares.

---

> Consulta 14: Buscar planes familiares

```javascript
db.planes.find({ "nombre_plan": { "$regex": "Familiar", "$options": "i" } })
```
Personalización de ofertas para grupos familiares.

---

> Consulta 15: Buscar planes con precio entre $100,000 y $199,999

```javascript
db.planes.find({ "precio": { "$regex": "^1[0-9]{5}$" } })
```
Permite enfocar promociones en clientes de alto consumo.

---

### **Solicitudes de Soporte**

> Consulta 16: Buscar solicitudes relacionadas con televisión

```javascript
db.solicitudes_soporte.find({ "tipo": { "$regex": "TV", "$options": "i" } })
```
Detección de fallos frecuentes en servicio de TV.

---

> Consulta 17: Buscar casos urgentes o de alta prioridad

```javascript
db.solicitudes_soporte.find({ "prioridad": { "$regex": "alta|urgente", "$options": "i" } })
```
Ayuda a priorizar tareas críticas del día.

---

> Consulta 18: Buscar fallos reportados en routers o módems

```javascript
db.solicitudes_soporte.find({ "descripcion": { "$regex": "router|módem", "$options": "i" } })
```
Gestión de reclamos técnicos frecuentes.

---

> Consulta 19: Buscar errores técnicos codificados como "E-###"

```javascript
db.solicitudes_soporte.find({ "descripcion": { "$regex": "E-[0-9]{3}" } })
```
Diagnóstico de errores sistémicos estandarizados.

---

> Consulta 20: Buscar solicitudes resueltas en junio 2024

```javascript
db.solicitudes_soporte.find({ "estado": "resuelto", "fecha": { "$regex": "^2024-06" } })
```
Evaluación de desempeño del equipo técnico.

---

### **Técnicos**

> Consulta 21: Buscar técnicos con especialidad en internet

```javascript
db.tecnicos.find({ "especialidad": { "$regex": "Internet", "$options": "i" } })
```
Asignación eficiente según el tipo de problema.

---

> Consulta 22: Buscar técnicos disponibles en la zona norte

```javascript
db.tecnicos.find({ "zona_asignada": { "$regex": "^Norte", "$options": "i" }, "disponible": true })
```
Optimización de logística por ubicación.

---

> Consulta 23: Buscar técnicos con más de 2 años de experiencia

```javascript
db.tecnicos.find({ "fecha_ingreso": { "$regex": "^202[0-1]" } })
```
Ideal para asignar casos complejos a personal senior.

---

> Consulta 24: Buscar técnicos con apellidos terminados en "ez"

```javascript
db.tecnicos.find({ "nombre": { "$regex": "ez$" } })
```
Estadísticas internas sobre diversidad en personal.

---

> Consulta 25: Buscar técnicos en zonas donde hay fibra óptica

```javascript
var zonasFibra = db.zonas_cobertura.find({ "tipo_cobertura": { "$regex": "Fibra", "$options": "i" } }, { "nombre": 1, "_id": 0 }).toArray().map(z => z.nombre);
db.tecnicos.find({ "zona_asignada": { "$in": zonasFibra } })
```
Alineación de personal experto con zonas tecnológicas.

---

### **4. Índices sugeridos para rendimiento**

```javascript
db.clientes.createIndex({ "nombre": 1 });
db.facturas.createIndex({ "id_cliente": 1 });
db.solicitudes_soporte.createIndex({ "zona": 1 });
```
Los índices mejoran el tiempo de respuesta en las consultas frecuentes.

---

### **5. Consulta de agregación ejemplo**

> Conteo de clientes por ciudad "Bucaramanga"

```javascript
db.clientes.aggregate([
  { $match: { ciudad: { "$regex": "Bucaramanga" } } },
  { $count: "total_clientes" }
])
```
Ideal para reportes comerciales y segmentación por zonas.

---

### 📌 Autor
Desarrollado por Víctor Alejandro Pabón · [@Alejandro-846](https://github.com/Alejandro-846)

