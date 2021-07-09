set(Boost_USE_STATIC_LIBS OFF) 
set(Boost_USE_MULTITHREADED ON)  
set(Boost_USE_STATIC_RUNTIME OFF) 

cmake_minimum_required(VERSION 3.12)
find_package (Python3 COMPONENTS Interpreter Development)

# https://stackoverflow.com/questions/5238160/boost-python-linking
FIND_PACKAGE(PythonLibs)
message("Include dirs of Python: " ${PYTHON_INCLUDE_DIRS} )
message("Libs of Python: " ${PYTHON_LIBRARIES} )

FIND_PACKAGE(Boost COMPONENTS python39)
message("Include dirs of boost: " ${Boost_INCLUDE_DIRS} )
message("Libs of boost: " ${Boost_LIBRARIES} )

ENABLE_TESTING()
INCLUDE_DIRECTORIES(${Boost_INCLUDE_DIRS} ${PYTHON_INCLUDE_DIRS})
LINK_LIBRARIES(${Boost_LIBRARIES} ${PYTHON_LIBRARIES}) # Deprecated but so convenient!

# set(CMAKE_EXE_LINKER_FLAGS "-lboost_system -lboost_python39 -lpython3.9m")

ADD_SUBDIRECTORY(01-HelloWorld)
ADD_SUBDIRECTORY(02-ExposingClasses)
ADD_SUBDIRECTORY(03-Constructors)
ADD_SUBDIRECTORY(04-ClassMembers)
ADD_SUBDIRECTORY(05-Inheritance)
ADD_SUBDIRECTORY(06-VirtualFunctionsInPython)
ADD_SUBDIRECTORY(07-Operators)
ADD_SUBDIRECTORY(08-CallPolicies)
ADD_SUBDIRECTORY(09-Overloading)
ADD_SUBDIRECTORY(10-Embedding)
ADD_SUBDIRECTORY(11-Iterators)
ADD_SUBDIRECTORY(12-Exceptions)
ADD_SUBDIRECTORY(13-AutoInstantiation)
