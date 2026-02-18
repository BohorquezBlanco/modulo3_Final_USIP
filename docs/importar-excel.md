# Módulo: Importación Masiva desde Excel

## 1. Descripción General

El módulo de Importación Masiva permite cargar registros de clientes al sistema
mediante archivos Excel (.xlsx), optimizando el proceso de registro y reduciendo
errores manuales.

El sistema procesa el archivo, valida la información y genera un reporte de
resultados indicando registros exitosos y errores detectados.

---

## 2. Objetivos del Módulo

- Permitir carga masiva de datos desde archivo Excel.
- Validar estructura y formato del archivo.
- Detectar registros duplicados.
- Generar reporte detallado de procesamiento.
- Registrar auditoría de la operación.

---

## 3. Alcance Funcional

✔ Subida de archivo Excel (.xlsx)  
✔ Validación de columnas obligatorias  
✔ Validación de tipos de datos  
✔ Inserción masiva en base de datos  
✔ Reporte de errores  
✔ Control de permisos por rol  

---

## 4. Requisitos Técnicos

### 4.1 Formato del Archivo

Tipo permitido:
- .xlsx

Tamaño máximo:
- 5 MB

Columnas obligatorias:

- nombre
- email
- telefono
- direccion

Ejemplo de estructura esperada:

| nombre        | email              | telefono   | direccion         |
|--------------|-------------------|------------|------------------|
| Juan Pérez   | juan@email.com     | 70000000   | Av. Central 123  |

---

## 5. Endpoint REST

### POST /clientes/importar

Permite subir archivo Excel para procesamiento masivo.

### Tipo de petición:
multipart/form-data

### Parámetro esperado:
- file (archivo Excel)

---

## 6. Flujo de Procesamiento

1. Validar autenticación del usuario.
2. Validar tipo y tamaño del archivo.
3. Leer contenido del archivo.
4. Validar estructura de columnas.
5. Validar datos fila por fila.
6. Insertar registros válidos.
7. Generar reporte de resultados.

---

## 7. Respuesta del Servicio

### Respuesta 200 OK

```json
{
  "total_registros": 120,
  "registros_exitosos": 115,
  "registros_fallidos": 5,
  "errores": [
    {
      "fila": 10,
      "error": "Email duplicado"
    }
  ]
}
