# 📆 Calendario Estilo iOS en Flutter

Este proyecto muestra cómo construir un calendario mensual básico y elegante en Flutter, similar al estilo iOS/macOS. Parte de una estructura simple como la del widget "Parchis Colors" y evoluciona hacia una interfaz visualmente más compleja, manteniéndose 100% en Flutter puro, sin paquetes externos.

---

## 🧱 Base de Conocimiento Inicial (Código Estilo Parchís)

El código de referencia original incluía conceptos fundamentales:

- `MaterialApp`, `Scaffold` y `SafeArea`.
- Uso de `Expanded`, `Container`, `Row` y `Column`.
- Personalización de `Text` y `Colors`.
- Distribución de elementos en una cuadrícula 2x2 usando `Expanded`.

---

## 🚀 Nuevos Conceptos Incorporados en el Calendario

Para lograr el calendario, se introdujeron nuevos widgets y técnicas:

### ✅ 1. `GridView.count`

Permite construir una cuadrícula flexible sin necesidad de usar múltiples `Row` anidados.

- 📌 Antes: múltiples `Row` con `Expanded`
- 🆕 Ahora: una sola estructura `GridView.count` que permite definir `crossAxisCount: 3` para una cuadrícula 3x3 o más.

```dart
GridView.count(
  crossAxisCount: 3,
  children: [...],
)
```

### 2. Uso de AspectRatio

Se usa para asegurar que el calendario mantenga una forma cuadrada sin deformarse.

```dart
AspectRatio(
  aspectRatio: 1,
  child: GridView.count(...),
)
```

### 3. Mapas y Listas para Días del Mes

Se crea una estructura que representa semanas y días usando List<List<int?>>. Esto permite recorrer dinámicamente las filas del calendario y resaltar rangos específicos.

```dart
final List<List<int?>> month = [
  [null, null, 1, 2, 3, 4, 5],
  ...
];
```

### 4. Lógica para Resaltar Fechas
Se introduce una condición para aplicar estilos especiales a ciertos días, como los días 16 al 19.

```dart
final isSelected = day != null && day >= 16 && day <= 19;
```

### 5. Estética Moderna

EdgeInsets, SizedBox, TextStyle, BoxDecoration, borderRadius, etc.
Todo centrado en lograr una apariencia más profesional.

```dart
Container(
  margin: EdgeInsets.all(4),
  decoration: BoxDecoration(
    color: isSelected ? Colors.blue : null,
    borderRadius: BorderRadius.circular(20),
  ),
)
```