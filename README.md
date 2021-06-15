[![Build Status](https://travis-ci.com/supsun-sockol/lab06.svg?branch=main)](https://travis-ci.com/supsun-sockol/lab06)
Все что нужно сделать для сборки кода в покеты - это подключить cpack.
```
install(TARGETS hello_world DESTINATION bin)
set(CPACK_PACKAGE_NAME "hello_world")
set(CPACK_PACKAGE_VENDOR "MyCompany")
set(CPACK_PACKAGE_CONTACT "https://myprojectsite.org")
set(CPACK_DEBIAN_PACKAGE_MAINTAINER "supsun-sockol@yandex.ru")
set(CPACK_PACKAGE_DESCRIPTION "The most stupid program ever written")
set(CPACK_GENERATOR "RPM" "DEB")
include(CPack)
```

и продкачать rpm пакет
