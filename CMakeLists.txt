cmake_minimum_required(VERSION 3.5)

project(Wt_AuthWidgetTest LANGUAGES CXX)

find_package(Wt REQUIRED)
include_directories( ${Wt_INCLUDE_DIR} )

find_package(Boost REQUIRED)
include_directories( ${Boost_INCLUDE_DIR} . ./model)
link_directories(${Boost_LIBRARY_DIRS})

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

add_executable(Wt_AuthWidgetTest
    main.cpp
    QRAuthWidget.C
    model/QRAuthService.C
    model/QRTokenDatabase.C
    model/Session.C
    model/User.C
    QRAuthWidget.h
    model/QRAuthService.h
    model/QRTokenDatabase.h
    model/Session.h
    model/User.h
)

target_link_libraries(Wt_AuthWidgetTest
  PRIVATE Wt::Wt
  PRIVATE Wt::Dbo
  PRIVATE Wt::DboSqlite3
  PRIVATE Wt::HTTP
)



install(TARGETS Wt_AuthWidgetTest
    LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
    RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR}
)
