cmake_minimum_required(VERSION 3.10)

# название проекта
project(ZMQExample)

# стандарт для C
set(CMAKE_C_STANDARD 99)

# поиск ZeroMQ
find_package(PkgConfig REQUIRED)
pkg_check_modules(PC_ZMQ REQUIRED libzmq)

# исполняем. файл для клиента
add_executable(client client.c)

# Линкуем клиент с библиотекой ZeroMQ
target_link_libraries(client ${PC_ZMQ_LIBRARIES})

# Добавляем исполняемый файл для сервера
add_executable(server server.c)

# Линкуем сервер с библиотекой ZeroMQ
target_link_libraries(server ${PC_ZMQ_LIBRARIES})

# Включаем заголовочные файлы от ZeroMQ
target_include_directories(client PUBLIC ${PC_ZMQ_INCLUDE_DIRS})
target_include_directories(server PUBLIC ${PC_ZMQ_INCLUDE_DIRS})

