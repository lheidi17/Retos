
# 1. Filtrar y manipular data frame.
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
##
```
 especies_lago <- especies %>%
  filter(habitat == "Lago") %>%
  arrange(desc(tamano))
print(especies_lago)
```
### Producto:
##

![Tabla de Esoecies](https://github.com/user-attachments/assets/ec34db6f-2407-411b-bafe-a2679f5b7f71)

# 2. Grafico
##
> 2.1 Grafico de dispersion entre Sepal.Length y SepalWidth coloreados según la especie.
```
ggplot(iris, aes(x = Sepal.Length, y = Sepal.Width, color = Species)) +
  geom_point(size = 3) +
  labs(title = "Relación entre Largo y Ancho de Sépalo",
       x = "Largo del Sépalo",
       y = "Ancho del Sépalo") +
  theme_minimal() +
  scale_color_manual(values = c("setosa" = "green", "versicolor" = "purple", "virginica" = "red"))
```
### Producto:
![Grafico 1](https://github.com/user-attachments/assets/e245d463-cebf-484f-9198-1c2cf083f359)

# 3. Datos agrupados y realialización de cálculos agregados.
##
> 3.1 Calificaciones agrupadas por estudiante.
```
calificaciones <- data.frame(
  estudiante = c("Ana", "Carlos", "Lucía", "Jorge", "Ana", "Carlos", "Lucía", "Jorge"),
  asignatura = c("Matemáticas", "Matemáticas", "Matemáticas", "Matemáticas", "Historia", "Historia", "Historia", "Historia"),
  calificacion = c(95, 85, 92, 88, 78, 82, 85, 90)
)
```
> 3.2 Promedio calculado por cada alumno.
```
 promedio_calificaciones <- calificaciones %>%
  group_by(estudiante) %>%
  summarise(promedio = mean(calificacion))
>print(promedio_calificaciones)
```
### Producto 
###
![Estudiante por promedio](https://github.com/user-attachments/assets/af945035-d6da-4a57-ba86-5ffcde19f092)

# 4. Transformación de datos y creación de nuevas variables.
##
> 4.1 Creación de el data frame de alturas.
```
 alturas <- data.frame(
  nombre = c("Laura", "Pedro", "Sara", "Miguel"),
  altura_cm = c(160, 175, 150, 180)
)
```
> 4.2 Creacion de una nueva columna con las alturas.
```
alturas <- alturas %>%
  mutate(altura_m = altura_cm / 100)
print(alturas)
```
### Resultado
##
![Estudiante por altura](https://github.com/user-attachments/assets/d18d8ed3-0dee-4f33-8111-8056986a6ddc)

# 5. Generación de gráficos de barras.
> 5.1 Creacion del data drame de ventas.
```
ventas <- data.frame(
  mes = c("Enero", "Febrero", "Marzo", "Abril", "Mayo", "Junio"),
  ventas = c(12000, 15000, 13000, 16000, 17500, 14000)
)
```
> 5.2 Creación del gráfico de barras para visualizar las ventas mensuales.
```
ggplot(ventas, aes(x = mes, y = ventas, fill = mes)) +
  geom_bar(stat = "identity") +
  labs(title = "Ventas Mensuales",
       x = "Mes",
       y = "Ventas") +
  theme_minimal() +
  scale_fill_brewer(palette = "Pastel 2") 
```
### Resultado
##
![Grafico 2](https://github.com/user-attachments/assets/891b572b-5e6c-4c47-bdc9-91bd02ad756b)

# 6. Lectura & escritura de archivos cvs.
> 6.1 Creación del data frame de productos.
```
productos <- data.frame(
  producto = c("A", "B", "C", "D"),
  precio = c(20, 35, 50, 10),
  cantidad_vendida = c(100, 200, 150, 250)
)
```
> 6.2  Calculo de el total de ingresos.
```
productos <- productos %>%
  mutate(ingreso_total = precio * cantidad_vendida)
```
> 6.3 Escribir nuestro archivo cvs.
```
write.csv(productos, "productos_con_ingresos.csv", row.names = FALSE)
print(productos)
```
### Resultado
![Total de ingresos](https://github.com/user-attachments/assets/41dfe8a7-898a-4a38-875c-ed8f5271f5f4)

# 7. Gráfico de caja.
> 7.1 Creación del grafico de boxplot para la variable mpg según el número de cilindros 
```
ggplot(mtcars, aes(x = factor(cyl), y = mpg, fill = factor(cyl))) +
  geom_boxplot() +
  labs(title = "Distribución de MPG según el Número de Cilindros",
       x = "Número de Cilindros",
       y = "Millas por Galón (MPG)") +
  scale_fill_manual(values = c("4" = "VioletRed", "6" = "Turquoise", "8" = "Salmon")) + 
  theme_minimal()
```
### Ressultado 
##
![Grafico 3](https://github.com/user-attachments/assets/d3e888fb-e6c8-4c86-8a2e-758c14d8c746)
