# 🎉 Sistema de Rifas

Sistema completo para crear, configurar y ejecutar rifas de manera profesional con interfaz web interactiva.

## 📋 Características

- ✨ **Interfaz Intuitiva**: Configurador visual sin necesidad de programar
- 🎁 **Múltiples Premios**: Agrega tantos premios como necesites con cantidades personalizables
- 👥 **Gestión de Participantes**: 
  - Carga mediante archivo CSV
  - Template descargable incluido
  - Soporte para integración con API (próximamente)
- 🎨 **Animaciones Profesionales**: Sorteo en vivo con efectos visuales
- 💾 **Exportación Automática**: Genera archivos JSON de configuración
- 📱 **Responsive**: Funciona en cualquier dispositivo

## 🚀 Inicio Rápido

### 1. Abrir el Sistema

Simplemente abre `index.html` en tu navegador. Verás dos opciones:

- **Configurador**: Para crear una nueva rifa
- **Ejecutar Rifa**: Para realizar el sorteo en vivo

### 2. Crear una Rifa

1. Haz clic en **"Crear Nueva Rifa"**
2. Completa los siguientes pasos:

#### Paso 1: Información General
- Ingresa el **nombre de la rifa** (ej: "Rifa Navidad 2026")
- Opcionalmente, agrega la fecha del evento

#### Paso 2: Configurar Premios
- Ingresa el nombre del premio (ej: "Bicicleta")
- Define la cantidad (cuántos premios de este tipo)
- Haz clic en **"Agregar Premio"**
- Repite para agregar más premios
- Puedes eliminar premios con el botón 🗑️

#### Paso 3: Configurar Participantes

**Opción A: Subir Archivo CSV**
1. Selecciona "Subir Archivo CSV"
2. Descarga el template haciendo clic en "⬇️ Descargar Template CSV"
3. Llena el template con tus datos:
   ```csv
   codigo,nombre
   1001,Juan Pérez
   1002,María García
   1003,Carlos López
   ```
4. Arrastra el archivo a la zona indicada o haz clic en "Seleccionar Archivo"

**Opción B: Integración API** (En desarrollo)
- Esta opción estará disponible próximamente para obtener participantes desde una API

### 3. Generar Configuración

1. Haz clic en **"🎉 Generar Configuración de Rifa"**
2. Se descargará automáticamente un archivo JSON con la configuración
3. Opcionalmente, abre la página de rifa para ejecutar el sorteo

### 4. Ejecutar el Sorteo

1. Abre `rifa.html` en tu navegador
2. La rifa cargará la última configuración creada
3. Haz clic en los botones para sortear ganadores

## 📁 Estructura de Archivos

```
Rifa/
│
├── index.html                      # Página principal del sistema
├── configurador.html               # Interfaz de configuración de rifas
├── rifa.html                       # Página de ejecución del sorteo
├── portada.html                    # Portada de presentación
│
├── procesar_configuracion.py       # Script para procesar configuraciones
├── convertir.py                    # Script de conversión de datos
├── leer_excel.py                   # Utilidad para leer archivos Excel
│
└── data/                           # Carpeta de datos
    ├── datos_rifa.json             # Configuración actual de rifa
    ├── participantes_*.csv         # Archivos de participantes
    └── premios_*.csv               # Archivos de premios
```

## 🔧 Uso Avanzado

### Convertir Configuración a Formato Antiguo

Si necesitas usar el formato de `datos_rifa.json` del sistema anterior:

```bash
python procesar_configuracion.py configuracion_MiRifa.json
```

Este comando:
- Lee el archivo de configuración generado por el configurador
- Lo convierte al formato esperado por `rifa.html`
- Guarda el resultado en `data/datos_rifa_MiRifa.json`

### Formato del CSV de Participantes

El archivo CSV debe tener exactamente estas columnas:

```csv
codigo,nombre
```

**Ejemplo:**
```csv
codigo,nombre
1001,Juan Pérez
1002,María García
1003,Carlos López
1004,Ana Martínez
```

**Notas importantes:**
- La primera línea debe ser el encabezado: `codigo,nombre`
- Cada participante en una línea separada
- Sin espacios extra alrededor de las comas
- Guarda el archivo con codificación UTF-8

### Template de Excel

Para facilitar la carga de datos, puedes:

1. Descargar el template desde el configurador
2. Llenar los datos en Excel:
   - Columna A: código
   - Columna B: nombre
3. Guardar como CSV (delimitado por comas)
4. Subir al configurador

## 🎨 Personalización

### Cambiar Colores

Edita las variables CSS en `configurador.html`:

```css
:root {
  --primary-color: #667eea;
  --secondary-color: #764ba2;
}
```

### Modificar Animaciones

Las animaciones del sorteo se encuentran en `rifa.html` en la sección de estilos y scripts.

## 🐛 Solución de Problemas

### El archivo CSV no se carga

**Problema**: El archivo no es reconocido o muestra 0 participantes

**Solución**:
- Verifica que el archivo tenga extensión `.csv`
- Asegúrate de que tenga el encabezado correcto: `codigo,nombre`
- Verifica que esté guardado con codificación UTF-8
- No uses punto y coma (`;`), solo comas (`,`)

### Los premios no se muestran

**Problema**: Después de agregar premios, no aparecen en la lista

**Solución**:
- Asegúrate de ingresar un nombre para el premio
- Haz clic en el botón "Agregar Premio"
- Verifica que la cantidad sea mayor a 0

### La configuración no se descarga

**Problema**: Al hacer clic en "Generar Configuración" no pasa nada

**Solución**:
- Verifica que todos los pasos estén completos (nombre, premios, participantes)
- Revisa la consola del navegador (F12) para ver errores
- Prueba con otro navegador

## 🔄 Flujo de Trabajo Recomendado

1. **Preparación**:
   - Descarga el template CSV
   - Llena los datos de participantes en Excel
   - Guarda como CSV

2. **Configuración**:
   - Abre el configurador
   - Ingresa el nombre de la rifa
   - Agrega todos los premios
   - Carga el CSV de participantes
   - Genera la configuración

3. **Ejecución**:
   - Abre la página de rifa
   - Verifica que los datos se cargaron correctamente
   - Ejecuta el sorteo en vivo

4. **Post-Evento**:
   - Guarda el archivo JSON de configuración
   - Exporta los resultados si es necesario

## 🆕 Próximas Características

- [ ] Integración con APIs para obtener participantes automáticamente
- [ ] Exportación de resultados en PDF
- [ ] Historial de rifas anteriores
- [ ] Modo de prueba sin consumir participantes
- [ ] Soporte para múltiples plantas/departamentos en una sola rifa
- [ ] Autenticación y permisos de usuario
- [ ] Dashboard de estadísticas

## 📞 Soporte

Si encuentras algún problema o tienes sugerencias, documenta:
- El navegador que estás usando
- Los pasos que realizaste
- Capturas de pantalla del error
- El mensaje de error (si hay alguno en la consola F12)

## 📝 Notas de Versión

### v2.0 - Configurador Interactivo
- ✨ Nueva interfaz de configuración visual
- 📄 Soporte para carga de CSV
- 📥 Template descargable
- 🎨 Diseño renovado
- 💾 Exportación automática de configuración

### v1.0 - Sistema Original
- 🎁 Sistema básico de rifas
- 📊 Carga manual de datos
- 🎨 Animaciones de sorteo

## 📄 Licencia

Este sistema es de uso interno. Todos los derechos reservados.
