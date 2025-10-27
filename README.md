# 💻 Bash — работа через командную строку

Иногда нам нужно работать с удалёнными серверами, где нет графического интерфейса.
В таких случаях важно уметь пользоваться Bash — с его помощью можно создавать, редактировать и удалять файлы и папки прямо из командной строки.

Здесь я делюсь примерами Bash-команд, которые использовала во время обучения тестированию для выполнения различных задач и автоматизации.

## Навигация

- [Работа с файлами и каталогами](#задача-1)
- [Редактирование файлов, проверка и завершение процессов, работа с сайтами](#задача-2)

## Задача 1

#### Работа с файлами и каталогами

```bash
~                                                   # Открыть домашнюю директорию
pwd                                                 # Показать текущий путь к каталогу
mkdir test1                                         # Создать каталог с именем test1
cd test1                                            # Перейти в каталог test1
touch file{1,2,3}.txt                               # Создать файлы 1, 2, и 3 внутри каталога test1
ls                                                  # Проверить содержимое каталога
cd ..                                               # Перейти в домашнюю директорию
mkdir test2                                         # Создать каталог с именем test2
rmdir test2                                         # Удалить пустой каталог test2
rm file2.txt                                        # Удалить файл 2 из папки test1
mkdir test3                                         # Создать каталог с именем test3
cd test3                                            # Перейти в каталог test3
touch file{1,2}.txt                                 # Создать 2 файла в каталоге test3
cd ..                                               # Вернуться в домашнюю директорию
rm -rf test3                                        # Удалить каталог test3
mkdir test4                                         # Создать каталог test4
mv test1/file{1,3}.txt test4                        # Переместить файлы 1 и 3 из каталога test1 в каталог test4
echo line1 >> file1.txt                             # Добавить 3 строки со словом line в file1.txt
echo line2 >> file1.txt
echo line3 >> file1.txt
cat file1.txt                                       # Проверить содержимое file1.txt
echo line1 >> file3.txt                             # Добавить 3 строки со словом line в file3.txt
echo line2 >> file3.txt
echo line3 >> file3.txt
cat file1.txt file3.txt                             # Проверить содержимое файлов file1.txt и file3.txt сразу
nano file3.txt + вручную отредактировать содержимое # Используя один из редакторов замените все строки в файле 3
```
## Задача 2
#### Редактирование файлов, проверка и завершение процессов, работа с сайтами
```bash
mkdir test3                                            # Создать папку test3
cd test3                                               # Открыть папку test3

# Добавить в папку test 3 три файла 4,5 и 6, в каждом из которых должно быть по 4 строки row1, row2, row3, row4
echo -e "row1\nrow2\nrow3\nrow4" > file4.txt                
echo -e "row1\nrow2\nrow3\nrow4" > file5.txt
echo -e "row1\nrow2\nrow3\nrow4" > file6.txt

grep "row2" file5.txt                                  # Найти строку "row2" в файле 5
grep -r  "row"                                         # Найти строку "row" в папке test3
grep -c "row" file6.txt                                # Посчитать кол-во строк с содержимым "row" в файле 6
find . -name "file5.txt"                               # Найти файл 5 в папке test3
find .name "file5.txt" -delete                         # Используя команду find, удалить файл 5
echo test > file4.txt                                  # Используя команду echo добавить слово test в файл 4
sed -'s/test/fail/g' file4.txt                         # Заменить слово test в файле 4 на fail
echo test >> file4.txt                                 # Добавить слово test, так чтобы сохранилось содержимое
ps aux                                                 # Посмотреть все процессы для юзеров которые происходят в системе
kill 324                                               # Убить процесс с PID 324
ping rusau.net                                         # Узнать доступность ресурса rusau.net
ping -c 5 rusau.net                                    # Отправить 5 пакетов на сайт rusau.net

# Используя GET и команду curl, получить информацию о зарегистрированных питомцах с любым статусом на https://petstore.swagger.io/
curl https://petstore.swagger.io/v2/pet/findByStatus?status=registered          

# Используя POST и команду curl, Создать нового пользователя на https://petstore.swagger.io
curl -X POST "https://petstore.swagger.io/v2/pet" \                            
     -H "Content-Type: application/json" \
     -d '{"id":123,"name":"Fluffy","photoUrls":["url1"],"status":"available"}'
```