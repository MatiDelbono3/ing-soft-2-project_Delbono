Como respuesta al pedido de obtener las ambigüedades a consultar con el analista, la herramienta me mostró el siguiente detalle:
Leí el enunciado completo y, aunque está bastante detallado, tiene varias ambigüedades importantes que deberías consultar con el analista antes de diseñar o implementar. Te las agrupo por tema para que las puedas usar directamente como checklist 👇

🔎 1. Ambigüedades funcionales generales
¿Qué significa exactamente “ingresa al buscador”?
No queda claro:
si es un sistema interno,
si hay autenticación previa,
ni qué datos mínimos se requieren para acceder.
¿Qué define que una cuenta esté activa, suspendida o dada de baja?
¿Viene de otra tabla/sistema?
¿Se consulta por API?
¿Qué estados posibles existen exactamente?
“Mostrar el botón o no según las condiciones”
¿Solo depende del estado del seguro?
¿O también de permisos del usuario?
👤 2. Identificación de la persona
¿Cómo se identifica unívocamente a una persona?
¿Tipo + número de documento es clave única?
¿Puede haber duplicados?
“Si la persona ya existe…”
¿Qué significa “existe”?
¿En cualquier módulo?
¿Solo personas activas?
¿Qué pasa si existe pero está dada de baja?
Bloqueo de campos
¿Se bloquean todos los campos SIEMPRE?
¿Qué pasa si los datos están desactualizados?
🧾 3. Datos personales
Sexo (Checkbox)
Esto es ambiguo:
Un checkbox permite múltiples valores
Pero “sexo” normalmente es único
👉 ¿Debe ser radio button?
Fecha de nacimiento (desde 1940)
¿Es inclusive?
¿Por qué esa restricción? ¿Es negocio o ejemplo?
CUIT autogenerado
No se especifica la fórmula exacta
¿Se valida contra AFIP o solo cálculo interno?
¿Qué pasa si el CUIT ya existe?
Nacionalidad / Provincia / País
¿De dónde salen los valores?
¿Son tablas maestras?
🏠 4. Domicilio
Campos obligatorios parcialmente definidos
Dice que calle, número, CP, localidad, provincia y país son obligatorios
Pero:
¿Piso es opcional?
¿Se permiten direcciones internacionales?
Código postal
¿Formato validado?
¿Depende del país?
📊 5. Porcentaje de beneficio (CRÍTICO)

Este es el punto más ambiguo del enunciado:

“El porcentaje no debe ser 0”
¿Puede ser negativo?
¿Puede ser mayor a 100?
“El porcentaje siempre debe ser 100%”
¿Esto aplica por beneficiario o por total?

Se contradice con:

“si ya existen beneficiarios, editar para que sumen 100%”

👉 Ambigüedad clave:

¿Se valida:
al guardar cada beneficiario?
o al finalizar la carga de todos?
Edición de beneficiarios existentes
¿Cómo se editan?
¿Desde la misma pantalla?
¿Se requiere confirmación?
💾 6. Guardado y validaciones
“Validar todos los campos”
No se especifica:
formato de documento
formato de CUIT
formato de fecha
reglas de nombre/apellido
Mensajes de error
¿Uno por campo?
¿Lista de errores?
¿Bloqueantes o advertencias?
“Mostrar pantalla de beneficiarios”
¿Se recarga?
¿Es redirección?
¿Se mantiene contexto de cuenta?
🔄 7. Comportamiento del sistema
Autocompletado
¿Es automático al salir del campo?
¿Requiere botón “buscar”?
Performance
¿Se consulta base en tiempo real?
¿Hay caché?
📋 8. Valores posibles (tablas maestras)
¿Son fijos o configurables?
Tipo documento
IVA
Estado civil
¿Pueden cambiar en el futuro?
👉 Impacta en diseño (hardcode vs tabla)
⚠️ 9. Casos no contemplados
¿Puede haber más de un beneficiario con mismo documento?
¿Se puede eliminar un beneficiario?
¿Se puede modificar después del alta?
¿Qué pasa si la suma da ≠ 100% al guardar?
¿Hay límite de beneficiarios?
🧠 Conclusión

El enunciado está bien como guía funcional, pero le faltan definiciones clave de:

reglas de negocio (especialmente porcentajes),
validaciones formales,
comportamiento del sistema,
modelo de datos implícito.
