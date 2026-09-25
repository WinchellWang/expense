# 💳 Guía de registro automático de gastos con Apple Pay

> Registra pagos sin contacto con Apple Pay mediante Atajos: categoría fija, registro en General para revisar después o clasificación con IA en el dispositivo.

[English](AUTOMATION_GUIDE.md) | [简体中文](AUTOMATION_GUIDE.zh-Hans.md) | [繁體中文](AUTOMATION_GUIDE.zh-Hant.md) | [日本語](AUTOMATION_GUIDE.ja.md) | [Français](AUTOMATION_GUIDE.fr.md) | [Español](AUTOMATION_GUIDE.es.md)

---

## 📌 Descripción general

Con las automatizaciones personales de Atajos de iOS, puedes registrar compras automáticamente en **Expense** en el instante en que acercas tu iPhone o Apple Watch para pagar con Apple Pay.

### Ventajas de esta automatización
- ⚡ **Cero esfuerzo**: En el momento en que se valida la tarjeta, el gasto se guarda silenciosamente en segundo plano.
- 🏷️ **Opciones de clasificación**: Asocia una categoría del activador con Expense, usa General o deja que la IA estime la categoría.
- 🏪 **Nombre del comercio incluido**: Guarda de forma automática el nombre de la tienda o restaurante en las notas del gasto.
- 🔒 **Procesamiento local**: El registro convencional usa App Intents en tu iPhone. Para la IA, elige On-Device. No se requiere acceso bancario.

---

## 🛠️ Requisitos previos

- Un **iPhone** con iOS 18.0 o posterior.
- **Apple Pay** configurado con al menos una tarjeta en la app Cartera (Wallet).
- La aplicación **Expense** instalada en tu iPhone.
- La aplicación nativa **Atajos** de Apple.

---

## 🚀 Atajo convencional: configuración paso a paso

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

Repite los pasos para las categorías disponibles en el activador. La tabla muestra ejemplos de correspondencias; no cubre todos los pagos de Apple Pay:

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

## ⚠️ Limitaciones del atajo convencional y alternativa General

La automatización Transacción de Apple permite filtrar por categoría, pero la entrada que recibe el atajo **no incluye el campo Category**. Por tanto, un atajo convencional no puede leer la categoría original de Apple Pay. Es una limitación del diseño de Atajos de iOS que Expense no puede solucionar.

- **Correspondencia uno a uno**: Selecciona una categoría en el activador y elige explícitamente la categoría equivalente de Expense en **Add Expense**. Crea una automatización para cada correspondencia. Algunas categorías de Apple Pay no aparecen en la lista del activador, por lo que los pagos que no coincidan con las categorías seleccionadas no se registrarán.
- **Registrar todas las categorías**: Selecciona **Any Category** (cualquier categoría), **Any Card** (cualquier tarjeta) y **Any Merchant** (cualquier comercio), y fija **Add Expense → Category** en **General**. Así evitas omisiones causadas por el filtro de categoría, incluso para pagos sin una categoría seleccionable equivalente. Después, edita manualmente las categorías en Expense. El atajo sigue sin poder identificar la categoría original.

Usa un solo método para los mismos pagos. Al activar **Any Category**, desactiva las automatizaciones por categoría que cubran esos pagos para evitar duplicados. «Todos» se refiere aquí a los pagos sin contacto de Apple Pay que iOS entrega al activador Transacción.

---

## 🤖 Atajo con IA: todas las categorías y clasificación automática

> **La IA permite completar la clasificación automática:** Any Category incluye todas las categorías y el nombre del comercio permite estimar la clasificación. Así reduces la organización manual sin tener que guardar todos los gastos en General.

Mantén el activador **Any Category** para evitar el filtrado y deja que Apple Intelligence estime la categoría de Expense a partir del nombre del comercio. La IA no recupera el campo Category que falta en Apple Pay. El flujo proporcionado clasifica **antes de Add Expense**, con un solo registro por pago.

### Requisitos

- **iOS 26 o posterior**, en un iPhone compatible con **Apple Intelligence**, activado y disponible en tu idioma y región.
- La acción **Usar modelo (Use Model)** de Atajos, configurada como **En el dispositivo (On-Device)**. Actualizar iOS no basta en un dispositivo incompatible. Consulta la [guía de introducción a Apple Intelligence de Apple](https://support.apple.com/en-ca/guide/iphone/iphc28624b81/ios).

---

## 📥 Descargar el atajo con IA

<a href="https://www.icloud.com/shortcuts/373d0c7f43aa49b6ae3eabe7dcd0c82d">
  <img src="https://cdn.jim-nielsen.com/ios/512/shortcuts-2018-10-03.png" alt="Añadir el atajo con IA" width="64" height="64">
</a>

[Añadir el atajo con IA](https://www.icloud.com/shortcuts/373d0c7f43aa49b6ae3eabe7dcd0c82d)

---

## 🛠️ Configurar el atajo con IA

1. Añade el atajo con IA compartido desde la sección de descarga independiente de arriba.
2. Crea una automatización **Transacción** con **Any Card → Any Category → Any Merchant**, activa **Ejecutar inmediatamente** y desactiva **Notificar al ejecutar**.
3. Ejecuta el atajo importado desde la automatización y pásale **Transacción / Entrada del atajo** para acceder a **Amount** (importe) y **Merchant** (comercio).
4. Comprueba que **Use Model** usa **On-Device** y recibe el nombre del comercio. El modelo devuelve un número de categoría; la rama **If** correspondiente ejecuta **Add Expense** con el importe extraído, la categoría asociada y el comercio en la nota. Revisa las categorías de cada rama en Expense y desactiva **Mostrar al ejecutar**.
5. Desactiva otras automatizaciones que registren los mismos pagos. Comprueba el importe, la nota y la categoría después del primer pago.

### Prompt de clasificación y ajustes del modelo

Copia el siguiente prompt en inglés en **Use Model**. En la última línea, sustituye `Transaction (Merchant)` por la variable real **Transacción → Merchant** de la entrada del atajo; no lo dejes como texto literal. Todas las versiones de la guía usan el mismo prompt para mantener los mismos números de categoría.

Como muestra la captura, configura **Model → On-Device**, **Output → Number** (número) y desactiva **Follow Up**. En las ramas If, compara la **Response** numérica con los valores de `1` a `8`; `8` corresponde a General.

```text
You are a transaction classification assistant.

Your task is to classify the given merchant/business name into exactly one of the following 8 categories:

1: Food & Drinks (e.g., restaurants, cafes, bars, supermarkets, food delivery)

2: Shopping (e.g., clothing, electronics, home goods, general retail)

3: Transportation (e.g., public transit, gas stations, ride-hailing/Uber/Lyft, tolls, parking)

4: Travel (e.g., airlines, hotels, Airbnb, car rentals, booking agencies)

5: Services (e.g., utilities, phone bills, insurance, subscriptions, repairs, professional services)

6: Entertainment (e.g., movies, streaming, gaming, concerts, museums, clubs)

7: Health (e.g., pharmacies, doctors, dentists, gyms, wellness)

8: General (other expense that is hard to classify into the above 7 categories)

Rules:
- Output ONLY the single category number (from 1 to 8).
- Do not include any explanations, punctuation, spaces, or extra text.

Here is Merchant Name: Transaction (Merchant)
```

### Flujo y limitaciones

La captura se realizó en **iOS 27**, con los ajustes detallados del modelo desplegados. Los requisitos anteriores siguen siendo **iOS 26 o posterior** en un dispositivo compatible.

![Flujo del atajo con IA](./iOS_27_AI_Shortcuts.jpg)

La IA estima la categoría a partir del nombre del comercio y puede equivocarse, especialmente en tiendas que venden productos variados. Revisa y corrige los registros en Expense cuando sea necesario. Usa **General** si la clasificación es incierta. La captura muestra ramas numeradas: al adaptar el atajo, dirige también las respuestas vacías o inesperadas a General para que una respuesta sin coincidencia no impida el registro. Si falla la ejecución del modelo, puede ser necesario registrar el gasto manualmente.

El procesamiento local requiere seleccionar **On-Device**. Elegir Private Cloud Compute o ChatGPT cambia dónde se procesa la clasificación.

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
El atajo convencional registra los gastos localmente mediante App Intents de iOS. La versión con IA también clasifica localmente al seleccionar **On-Device**; Private Cloud Compute y ChatGPT usan procesamiento remoto. La sincronización y la copia de seguridad opcionales de iCloud en Expense son ajustes independientes.
