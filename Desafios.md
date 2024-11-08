# DESAFIOS
# 1. Filtración y manipulación de data frames.
## 

1.1 Especies que viven en un lago.
```
  especies <- data.frame(
  especie = c("Ajolote", "Rana", "Serpiente", "Tortuga"),
  habitat = c("Lago", "Río", "Bosque", "Lago"),
  tamano = c(30, 10, 150, 50),
  peso = c(150, 25, 1000, 500)
)
```
1.2 Especies ordenadas por tamaño de mayor a menor.
``
 especies_lago <- especies %>%
  filter(habitat == "Lago") %>%
  arrange(desc(tamano))
>print(especies_lago)
### Producto:
```
# 2. Grafico
##
> 2.1 Grafico de dispersion entre Sepal.Length y SepalWidth coloreados según la especie.
> 
>ggplot(iris, aes(x = Sepal.Length, y = Sepal.Width, color = Species)) +
  geom_point(size = 3) +
  labs(title = "Relación entre Largo y Ancho de Sépalo",
       x = "Largo del Sépalo",
       y = "Ancho del Sépalo") +
  theme_minimal() +
  scale_color_manual(values = c("setosa" = "purple", "versicolor" = "black", "virginica" = "yellow"))
### Producto:
>

# 3. Datos agrupados y realialización de cálculos agregados.
##
> 3.1 Calificaciones agrupadas por estudiante.
>
> calificaciones <- data.frame(
  estudiante = c("Ana", "Carlos", "Lucía", "Jorge", "Ana", "Carlos", "Lucía", "Jorge"),
  asignatura = c("Matemáticas", "Matemáticas", "Matemáticas", "Matemáticas", "Historia", "Historia", "Historia", "Historia"),
  calificacion = c(95, 85, 92, 88, 78, 82, 85, 90)
)
> Promedio calculado por cada alumno.
> promedio_calificaciones <- calificaciones %>%
  group_by(estudiante) %>%
  summarise(promedio = mean(calificacion))
>print(promedio_calificaciones)

### Producto 


# 4. Transformación de datos y creación de nuevas variables
##
> Creación de el data frame de alturas.
> alturas <- data.frame(
  nombre = c("Laura", "Pedro", "Sara", "Miguel"),
  altura_cm = c(160, 175, 150, 180)
)
>
> Creacion de una nueva columna con las alturas.
>alturas <- alturas %>%
  mutate(altura_m = altura_cm / 100)
<
print(alturas)

### Resultado



# 5. Generación de gráficos de barras.
>
ventas <- data.frame(
  mes = c("Enero", "Febrero", "Marzo", "Abril", "Mayo", "Junio"),
  ventas = c(12000, 15000, 13000, 16000, 17500, 14000)
)

# Crear un gráfico de barras para visualizar las ventas mensuales con colores diferentes para cada mes Xd
>ggplot(ventas, aes(x = mes, y = ventas, fill = mes)) +
  geom_bar(stat = "identity") +
  labs(title = "Ventas Mensuales",
       x = "Mes",
       y = "Ventas") +
  theme_minimal() +
  scale_fill_brewer(palette = "Set3") # Utilice una paleta de colores para mayor diferencia


# 6. Lectura & escritura de archivos cvs

>productos <- data.frame(
  producto = c("A", "B", "C", "D"),
  precio = c(20, 35, 50, 10),
  cantidad_vendida = c(100, 200, 150, 250)
)

>productos <- productos %>%
  mutate(ingreso_total = precio * cantidad_vendida)

>write.csv(productos, "productos_con_ingresos.csv", row.names = FALSE)
print(productos)

### Resultado



# 7. Gráfico de caja.
>ggplot(mtcars, aes(x = factor(cyl), y = mpg, fill = factor(cyl))) +
  geom_boxplot() +
  labs(title = "Distribución de MPG según el Número de Cilindros",
       x = "Número de Cilindros",
       y = "Millas por Galón (MPG)") +
  scale_fill_manual(values = c("4" = "lightblue", "6" = "lightgreen", "8" = "coral")) + 
  theme_minimal()
