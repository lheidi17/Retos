# Desafío 1 Filtrar y manipular data frames 

especies <- data.frame(
  especie = c("Ajolote", "Rana", "Serpiente", "Tortuga"),
  habitat = c("Lago", "Río", "Bosque", "Lago"),
  tamano = c(30, 10, 150, 50),
  peso = c(150, 25, 1000, 500)
)

# 1.1 Filtrar las especies que viven en un lago y ordenar por tamaño (de mayor a menor)
especies_lago <- especies %>%
  filter(habitat == "Lago") %>%
  arrange(desc(tamano))

print(especies_lago)

# Generación de gráficos 2
ggplot(iris, aes(x = Sepal.Length, y = Sepal.Width, color = Species)) +
  geom_point(size = 3) +
  labs(title = "Relación entre Largo y Ancho de Sépalo",
       x = "Largo del Sépalo",
       y = "Ancho del Sépalo") +
  theme_minimal() +
  scale_color_manual(values = c("setosa" = "purple", "versicolor" = "black", "virginica" = "yellow"))



# Desafío 3 Agrupar datos y realizar cálculos agregados 

# Crear el data frame de calificaciones
calificaciones <- data.frame(
  estudiante = c("Ana", "Carlos", "Lucía", "Jorge", "Ana", "Carlos", "Lucía", "Jorge"),
  asignatura = c("Matemáticas", "Matemáticas", "Matemáticas", "Matemáticas", "Historia", "Historia", "Historia", "Historia"),
  calificacion = c(95, 85, 92, 88, 78, 82, 85, 90)
)

# Agrupar por estudiante y calcular el promedio de calificación
promedio_calificaciones <- calificaciones %>%
  group_by(estudiante) %>%
  summarise(promedio = mean(calificacion))

print(promedio_calificaciones)

### Resultado 


#  Desafío 4 Transformación de datos y crear nuevas variables
* Crear una nueva columna con las alturas en metros.
* Mostrar el nuevo data frame.

# Crear el data frame de alturas
alturas <- data.frame(
  nombre = c("Laura", "Pedro", "Sara", "Miguel"),
  altura_cm = c(160, 175, 150, 180)
)

# Crear una nueva columna con las alturas en metros
alturas <- alturas %>%
  mutate(altura_m = altura_cm / 100)

print(alturas)

### Resultado



# Desafío 5 Generación de gráficos de barras
* Crear un gráfico de barras para visualizar las ventas mensuales.

ventas <- data.frame(
  mes = c("Enero", "Febrero", "Marzo", "Abril", "Mayo", "Junio"),
  ventas = c(12000, 15000, 13000, 16000, 17500, 14000)
)

# Crear un gráfico de barras para visualizar las ventas mensuales con colores diferentes para cada mes Xd
ggplot(ventas, aes(x = mes, y = ventas, fill = mes)) +
  geom_bar(stat = "identity") +
  labs(title = "Ventas Mensuales",
       x = "Mes",
       y = "Ventas") +
  theme_minimal() +
  scale_fill_brewer(palette = "Set3") # Utilice una paleta de colores para mayor diferencia


# Desafío 6 Lectura & escritura de archivos cvs

productos <- data.frame(
  producto = c("A", "B", "C", "D"),
  precio = c(20, 35, 50, 10),
  cantidad_vendida = c(100, 200, 150, 250)
)

productos <- productos %>%
  mutate(ingreso_total = precio * cantidad_vendida)

write.csv(productos, "productos_con_ingresos.csv", row.names = FALSE)
print(productos)

### Resultado



# Desafío 7 Gráfico de caja (Boxplot)
ggplot(mtcars, aes(x = factor(cyl), y = mpg, fill = factor(cyl))) +
  geom_boxplot() +
  labs(title = "Distribución de MPG según el Número de Cilindros",
       x = "Número de Cilindros",
       y = "Millas por Galón (MPG)") +
  scale_fill_manual(values = c("4" = "lightblue", "6" = "lightgreen", "8" = "coral")) + 
  theme_minimal()
