cmake_minimum_required(VERSION 3.0)

message("CMake " "is " "the " "most " "powerful " "buildsystem!")

# Напечатает "Hello, my lovely CMake", один таб и "!":
message("Hello, my lovely CMake\t!")

# Напечатает "Hello,_my_lovely_CMake!" без пробелов:
message(Hello,_my_lovely_CMake!)

# Определить переменную VARIABLE со значением "Mr. Thomas":
set(VARIABLE "Mr. Thomas")

# Напечает "His name is: Mr. Thomas":
message("His name is: " ${VARIABLE})

# Напечатает "'BINGO' is equal to: []", так как "BINGO" не определена:
message("'BINGO' is equal to: [${BINGO}]")

# Удалить переменную VARIABLE:
unset(VARIABLE)

# Напечатает "Of course, 5 > 1!":
if(5 GREATER 1)
    message("Of course, 5 > 1!")
elseif(5 LESS 1)
    message("Oh no, 5 < 1!")
else()
    message("Oh my god, 5 == 1!")
endif()

# Напечатает в консоль три раза "VARIABLE is still 'Airport'":
set(VARIABLE Airport)
while(${VARIABLE} STREQUAL Airport)
    message("VARIABLE is still '${VARIABLE}'")
    message("VARIABLE is still '${VARIABLE}'")
    message("VARIABLE is still '${VARIABLE}'")
    set(VARIABLE "Police station")
endwhile()

# Напечатает "Give me the sugar please!" с новых строк:
foreach(VARIABLE Give me the sugar please!)
    message(${VARIABLE})
endforeach()


# Напечатает "0 1 2 3 4 5 6 7 8 9 10" с новых строк:
foreach(VARIABLE RANGE 10)
    message(${VARIABLE})
endforeach()

# Напечатает "3 4 5 6 7 8 9 10 11 12 13 14 15" с новых строк:
foreach(VARIABLE RANGE 3 15)
    message(${VARIABLE})
endforeach()

# Напечатает "50 60 70 80 90" с новых строк:
foreach(VARIABLE RANGE 50 90 10)
    message(${VARIABLE})
endforeach()


# Определение функции "print_numbers":
function(print_numbers NUM1 NUM2 NUM3)
    message(${NUM1} " " ${NUM2} " " ${NUM3})
endfunction()

# Определение макроса "print_words":
macro(print_words WORD1 WORD2 WORD3)
    message(${WORD1} " "  ${WORD2} " " ${WORD3})
endmacro()

# Вызов функции "print_numbers", которая напечатает "12 89 225":
print_numbers(12 89 225)

# Вызов макроса "print_words", который напечатает "Hey Hello Goodbye":
print_words(Hey Hello Goodbye)

# Определить макрос, содержащий команду выхода:
macro(demonstrate_macro)
    return()
endmacro()

# Определить функцию, вызывающую предыдущий макрос:
function(demonstrate_func)
    demonstrate_macro()
    message("The function was invoked!")
endfunction()

# Напечатает "Something happened with the function!"
demonstrate_func()
message("Something happened with the function!")

# Функция, определяющая переменную "VARIABLE" со значением
# "In the parent scope..." в родительской области видимости:
function(demonstrate_variable)
    set(VARIABLE "In the parent scope..." PARENT_SCOPE)
endfunction()

# Определить переменную "VARIABLE" в текущей области видимости:
demonstrate_variable()

# Теперь возможно получить к переменной "VARIABLE" доступ:
message("'VARIABLE' is equal to: ${VARIABLE}")
