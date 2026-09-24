# 💳 Guía de registro automático de gastos con Apple Pay

> Registra tus gastos en tiempo real al pagar con Apple Pay mediante las automatizaciones de Atajos de iOS. 100 % privado, local en tu dispositivo y sin escribir nada manualmente.

[English](AUTOMATION_GUIDE.md) | [简体中文](AUTOMATION_GUIDE.zh-Hans.md) | [繁體中文](AUTOMATION_GUIDE.zh-Hant.md) | [日本語](AUTOMATION_GUIDE.ja.md) | [Français](AUTOMATION_GUIDE.fr.md) | [Español](AUTOMATION_GUIDE.es.md)

---

## 📌 Descripción general

Con las automatizaciones personales de Atajos de iOS, puedes registrar compras automáticamente en **Expense** en el instante en que acercas tu iPhone o Apple Watch para pagar con Apple Pay.

### Ventajas de esta automatización
- ⚡ **Cero esfuerzo**: En el momento en que se valida la tarjeta, el gasto se guarda silenciosamente en segundo plano.
- 🏷️ **Categorización inteligente**: Asocia las categorías predeterminadas de Apple Pay (Comida y bebida, Compras, Transporte, etc.) directamente con tus categorías de Expense.
- 🏪 **Nombre del comercio incluido**: Guarda de forma automática el nombre de la tienda o restaurante en las notas del gasto.
- 🔒 **100 % privado y local**: Todo se procesa en tu propio iPhone. Sin vincular cuentas bancarias ni servidores externos; tus datos nunca salen del dispositivo.

---

## 🛠️ Requisitos previos

- Un **iPhone** con iOS 18.0 o posterior (se recomienda iOS 27+).
- **Apple Pay** configurado con al menos una tarjeta en la app Cartera (Wallet).
- La aplicación **Expense** instalada en tu iPhone.
- La aplicación nativa **Atajos** de Apple.

---

## 🚀 Guía de configuración paso a paso

A continuación se explica la configuración tomando como ejemplo la categoría **«Comida y bebida (Food & Drinks)»** (el procedimiento es idéntico para cualquier otra categoría):

### Paso 1: Crear una nueva automatización en Atajos
1. Abre la app **Atajos** en tu iPhone.
2. Toca la pestaña **Automatización** en la parte inferior de la pantalla.
3. Toca el botón **`+`** en la esquina superior derecha.
4. Desplázate hacia abajo y selecciona **Transacción** (en algunas versiones de iOS aparece como **Cartera**).

---

### Paso 2: Configurar las condiciones del activador
En la pantalla de configuración:

1. **Tarjeta**: Selecciona **Cualquier tarjeta** (o elige tarjetas específicas).
2. **Categorías**:
   - Toca **Categorías**.
   - Marca **Comida y bebida** (Food & Drinks).
   - Confirma tocando la marca de verificación azul `✓` arriba a la derecha.
3. **Comercios**: Mantén la opción **Cualquier comercio**.
4. **Modo de ejecución**:
   - Marca **Ejecutar inmediatamente** (el interruptor se pondrá en **verde**).
   - Desactiva **Notificar al ejecutar** (para que no aparezcan alertas molestas cada vez que pagues).
5. Toca **Siguiente** en la esquina superior derecha.

---

### Paso 3: Añadir las acciones de la automatización
Selecciona **Nueva automatización vacía** y agrega las 3 acciones siguientes en orden:

#### Acción 1: Extraer números limpios
Apple Pay suele entregar los importes acompañados del símbolo de moneda (por ejemplo, `$9.21`, `15,50 €`). Extraer el número garantiza que no se produzcan errores:
1. Toca **Añadir acción**.
2. Busca **«Obtener números de la entrada»** (en inglés `Get numbers from`) y selecciónala.
3. Toca el parámetro de entrada y selecciona **Entrada del atajo** (o toca `Transacción > Importe`).
   - La acción mostrará: `Obtener números de [Importe]`.
   - La variable generada será **`Números`** (`# Numbers`).

#### Acción 2: Registrar el gasto en Expense
1. En la barra de búsqueda inferior, escribe **Expense**.
2. Selecciona la acción **Add Expense** (Añadir gasto).
3. Configura los parámetros:
   - **Amount (Importe)**: Toca el campo y selecciona la variable **`Números`** generada en la Acción 1.
   - **Category (Categoría)**: Toca el campo y elige **`🍱 Food & Drinks`** (Comida y bebida).
   - **Note (Nota)**: Toca el campo, elige **Entrada del atajo**, pulsa sobre la cápsula azul y selecciona **Comercio** (`Pay Merchant`).
4. Toca la flecha `>` de la tarjeta **Add Expense** para ver más opciones:
   - Desactiva **Mostrar al ejecutar** (Show When Run) para que el registro se realice de forma silenciosa en segundo plano.

#### Acción 3: Detener el atajo
1. En la barra de búsqueda inferior, busca y añade **«Detener este atajo»** (Stop this shortcut).
2. Toca **Listo** en la esquina superior derecha para guardar la automatización.

---

## 📸 Estructura completa de la automatización

Tu automatización finalizada tendrá la siguiente estructura:

![shortcuts](./shortcuts.jpg)

---

## 💡 Recomendación: Configuración multicategoría

Repite el proceso anterior para crear automatizaciones dedicadas a tus categorías de gasto más habituales:

| Categoría del activador | Categoría en Expense |
| :--- | :--- |
| **Comida y bebida** | `🍱 Food & Drinks` |
| **Compras** | `🛍️ Shopping` |
| **Transporte** | `🚗 Transportation` |
| **Viajes** | `🏖️ Travel` |
| **Servicios** | `🛠️ Services` |
| **Entretenimiento** | `🎠 Entertainment` |
| **Salud** | `💊 Health` |

---

## ❓ Preguntas frecuentes y solución de problemas

### Q1: ¿Por qué el importe queda vacío o se registra como 0.00?
**Causa**: En muchos países el valor de `Importe` incluye símbolos monetarios (`€`, `$`) que impiden su lectura directa como número simple.  
**Solución**: Asegúrate de incluir la acción **«Obtener números de la entrada»** y de enlazar la variable **`# Números`** al campo `Amount` de Add Expense.

### Q2: ¿Por qué aparece un aviso pidiendo confirmación en cada pago?
**Solución**:
1. Comprueba en el activador que **Ejecutar inmediatamente** esté activado y **Notificar al ejecutar** esté desactivado.
2. Dentro de las acciones, despliega las opciones de `Add Expense` y asegúrate de que **Mostrar al ejecutar** esté desactivado.

### Q3: ¿Puedo modificar la categoría o la nota después?
**Sí.** Todas las entradas registradas aparecen al instante en la pantalla principal de Expense. Puedes tocar cualquier apunte para ajustar su categoría, importe o detalles.

### Q4: ¿Expense envía mis datos financieros a servidores externos?
**No.** Todo el procesamiento se realiza en local mediante el framework App Intents de Apple. No se necesitan cuentas ni registros, y tu privacidad financiera queda 100 % protegida en tu dispositivo.
