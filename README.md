# Sistema de Gestión de Datos - OTNI TEXTIL
## Documentación y Especificaciones Técnicas
*Autora:* Gabriela Del Hoyo

---

## 1. Minuta de Requisitos y Reglas de Negocio

* *RF08 - Control de Stock por Talle:* El sistema controla la cantidad disponible de productos de forma independiente para cada talle o variante de la prenda.
* *RF09 - Integridad de Precios y Cantidades:* Se valida que no se puedan ingresar valores negativos ni iguales a cero al cargar precios, subtotales o cantidades de artículos.
* *RN09 - Unicidad de DNI y Usuario:* No se permite registrar clientes duplicados con el mismo número de DNI, ni tampoco empleados con el mismo nombre de usuario.
* *RN10 - Cálculo de Subtotal:* El importe subtotal de cada ítem se obtiene calculando exactamente la cantidad multiplicada por el precio unitario.

---

## 2. Tratamiento de Talles en el Modelo Entidad-Relación (DER)

En la entidad *PRODUCTO, cada registro combina el modelo y el talle correspondiente (por ejemplo: *"Camisa Trabajo - Talle M"), garantizando un control de inventario preciso por variante.

---

## 3. Justificación del Proceso de Normalización

* *Primera Forma Normal (1FN):* Se eliminaron los grupos repetitivos mediante la creación de la entidad intermedia DETALLE_VENTA (o detalle de comprobante).
* *Segunda Forma Normal (2FN):* Todos los atributos que no son clave primaria dependen funcionalmente de la totalidad de la clave correspondiente.
* *Tercera Forma Normal (3FN):* Se eliminaron las dependencias transitivas, separando los datos del cliente y del empleado en sus propias entidades e identificadores únicos.
*
## Planilla de Control de Pruebas (QA / Testing) - Gabriela del Hoyo

| ID | Módulo / Pantalla | Prueba Realizada | Resultado Esperado | Resultado Obtenido | Estado / Observación |
|----|------------------|------------------|--------------------|--------------------|-----------------------|
| 01 | Inicio | Carga de contadores del panel | Mostrar resumen de stock/ventas | Contadores en 0 | ❌ Observado a desarrollo |
| 02 | Productos | Formato de moneda en interfaz | Mostrar precios con prefijo de pesos ($) | Se identificó prefijo "S/." | ❌ Observado a desarrollo |
| 03 | Ventas | Registrar venta con varios productos | Permitir asociar múltiples ítems | Detalle_Venta funcional | ✅ Aprobado |
| 04 | Login | Validación de credenciales | Control de acceso por perfil | Ingreso correcto | ✅ Aprobado |
