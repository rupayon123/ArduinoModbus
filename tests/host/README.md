# Host regression checks

From the repository root, using Clang or GCC:

```sh
c++ -std=c++11 -Wall -Wextra -Werror -fsanitize=address,undefined \
  -Itests/host -Isrc src/ModbusClient.cpp tests/host/invalid_slave.cpp \
  -o /tmp/arduino-modbus-invalid-slave
/tmp/arduino-modbus-invalid-slave
```

This compiles the production client against a recording libmodbus backend and
minimal Arduino header. It verifies propagation of failed slave selection,
absence of subsequent reads/writes, valid requests, and buffered destination
reselection. It does not exercise serial hardware or replace board compilation
and device testing.
