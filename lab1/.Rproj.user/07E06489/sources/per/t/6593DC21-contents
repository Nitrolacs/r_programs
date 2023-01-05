# Задание 1

b <- c("северные регионы", "средняя полоса", "южные регионы")

a <- c(0.46, 0.41, 0.09, 0.52, 0.33, 0.22, 0.86, 0.41, 0.27, 0.91, 0.28, 
       0.40, 0.54, 0.39, 0.27)

num <- rep(seq(1, 5), each = 3)

b_factor <- factor(b)

# Вывод содержимого каждого объекта
print(num)
print(a)
print(b)
print(b_factor)


# Задание 2

my_frame <- data.frame(Number = num, Climatic_conditions = b_factor, Average_amount_of_meat = a)

print(my_frame)  # Содержимое таблицы данных
dim(my_frame)   # Размерность таблицы данных
str(my_frame)   # Структура таблицы данных
names(my_frame)   # Названия признаков
head(my_frame, n = 4)   # 4 первые строки таблицы
my_frame[my_frame$Average_amount_of_meat >= 0.3 & my_frame$Average_amount_of_meat <= 0.5, ]   # Все объекты, значения которых лежат в диапазоне
my_frame[my_frame$Climatic_conditions == "северные регионы", ]  #  Все объекты с выбранным значением фактора.
my_frame[c(1, 3, 6, 9, 10), ]  # Объекты с номерами 1, 3, 6, 9, 10
my_frame[my_frame$Average_amount_of_meat == min(my_frame$Average_amount_of_meat), ]  # Объект с минимальным значением вещественного признака

# Задание 3

# Добавление ещё трех объектов

my_frame <- rbind(my_frame, c(6, "северные регионы", 0.64),
                            c(6, "средняя полоса", 0.36),
                            c(6, "южные регионы", 0.06))

my_frame$Average_amount_of_meat <- as.numeric(my_frame$Average_amount_of_meat)
my_frame$Number <- as.numeric(my_frame$Number)

print(my_frame)

# Вывод среднего значения и среднеквад. отклонения в файл.

mean_value <- mean(my_frame$Average_amount_of_meat)
sd_value <- sd(my_frame$Average_amount_of_meat)
write.table(c(mean_value, sd_value), file = "values.txt")  

New <- dnorm(my_frame$Average_amount_of_meat, mean_value, sd_value)
my_frame <- cbind(my_frame, New) # Добавление нового столбца
print(my_frame)  # Вывод таблицы

# Задание 4

# Импорт и создание таблицы данных
library(xlsx)
flat <- read.xlsx("C:/Users/nikit/Desktop/programming/r_labs/lab1/Flat98.xlsx", sheetIndex = 1)

head(flat, n = 5)  # 5 первых строк таблицы flat

# Создание функции

f <- function(number_vector) {
  return(head(sort(number_vector, TRUE), 5))
}

test_vector <- c(5, 2, 1, 10, 7, 9, 6, 3, 8, 4)

# Демонстрация работы функции на произвольном числовом векторе
f(test_vector)

# Запись данных о пяти самых дорогих квартирах
write.xlsx(flat[flat$price %in% f(flat$price), ], file = "max_price.xlsx", sheetName = "Sheet1", row.names = FALSE)

# Запись данных о пяти двухкомнатных квартирах с наибольшей жилой площадью

tmp <- flat[flat$rooms == 2, ]
table <- tmp[order(tmp$livsp, decreasing = TRUE), ]

write.xlsx(head(table[table$livsp %in% f(table$livsp), ], n = 5), file = "max_livsp.xlsx", sheetName = "Sheet1", row.names = FALSE)

