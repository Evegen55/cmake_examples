cmake_minimum_required(VERSION 3.0)
# Скомпилировать исполняемый файл "MyExecutable" из
# исходников "ObjectHandler.c", "TimeManager.c" и "MessageGenerator.c":
add_executable(MyExecutable ObjectHandler.c TimeManager.c MessageGenerator.c)

# Скомпилировать статическую библиотеку "MyLibrary" из
# исходников "ObjectHandler.c", "TimeManager.c" и "MessageConsumer.c":
add_library(MyLibrary STATIC ObjectHandler.c TimeManager.c MessageConsumer.c)

# ==== два блока эквивалентного кода

# Задать исполняемый файл "MyExecutable" из исходников
# "ObjectPrinter.c" и "SystemEvaluator.c":
add_executable(MyExecutable ObjectPrinter.c SystemEvaluator.c)
# Добавить к цели "MyExecutable" исходник "MessageConsumer.c":
target_sources(MyExecutable MessageConsumer.c)
# Добавить к цели "MyExecutable" исходник "ResultHandler.c":
target_sources(MyExecutable ResultHandler.c)

# Задать исполняемый файл "MyExecutable" из исходников
# "ObjectPrinter.c", "SystemEvaluator.c", "MessageConsumer.c" и "ResultHandler.c":
add_executable(MyExecutable ObjectPrinter.c SystemEvaluator.c MessageConsumer.c
ResultHandler.c)

# Присвоить переменной "VALUE" значение свойства "C_STANDARD":
get_target_property(VALUE MyTarget C_STANDARD)

# Вывести значение полученного свойства на экран:
message("'C_STANDARD' property is equal to [${VALUE}]")

# Загрузить настройки пакета библиотеки "GSL":
find_package(GSL 2.5 REQUIRED)

# Скомпоновать исполняемый файл с библиотекой "GSL":
target_link_libraries(MyExecutable GSL::gsl)

# Уведомить компилятор о каталоге заголовков "GSL":
target_include_directories(MyExecutable ${GSL_INCLUDE_DIRS})


# Установить цели "TimePrinter" и "DataScanner" в директорию "bin":
install(TARGETS TimePrinter DataScanner DESTINATION bin)
# Установить файлы "DataCache.txt" и "MessageLog.txt" в директорию "~/":
install(FILES DataCache.txt MessageLog.txt DESTINATION ~/)
# Установить каталоги "MessageCollection" и "CoreFiles" в директорию "~/":
install(DIRECTORY MessageCollection CoreFiles DESTINATION ~/)
