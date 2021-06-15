[![Build Status](https://travis-ci.com/Ko71k/lab6.svg?branch=main)](https://travis-ci.com/Ko71k/lab6)
Все что нужно сделать для сборки кода в покеты - это подключить cpack и продкачать rpm пакет.
```
install(TARGETS hello_world DESTINATION bin)
set(CPACK_PACKAGE_NAME "hello_world")
set(CPACK_PACKAGE_VENDOR "MyCompany")
set(CPACK_PACKAGE_CONTACT "https://myprojectsite.org")
set(CPACK_DEBIAN_PACKAGE_MAINTAINER "rassmagin.wolf@mail.tu")
set(CPACK_PACKAGE_DESCRIPTION "Programm")
set(CPACK_GENERATOR "RPM" "DEB")
include(CPack)
```

