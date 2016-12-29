
find_package(XENOMAI REQUIRED)
find_package(ODE REQUIRED)

INCLUDE_DIRECTORIES(.)
INCLUDE_DIRECTORIES(./include)
INCLUDE_DIRECTORIES(${XENOMAI_INCLUDE_DIRS})
INCLUDE_DIRECTORIES(${ODE_INCLUDE_DIRS})

LINK_DIRECTORIES(${XENOMAI_LIBRARIES_DIRS})
LINK_DIRECTORIES(${ODE_LIBRARIES_DIRS})

AUX_SOURCE_DIRECTORY(./tasks ALL_TASKS)

ADD_EXECUTABLE(air_hockey main.cpp global_variables.cpp ${ALL_TASKS})

ADD_SUBDIRECTORY(interpolation)

TARGET_LINK_LIBRARIES(air_hockey ${XENOMAI_NATIVE_SKIN_LIBS})
TARGET_LINK_LIBRARIES(air_hockey ${ODE_LIBS})
TARGET_LINK_LIBRARIES(air_hockey interpolation jsoncpp)