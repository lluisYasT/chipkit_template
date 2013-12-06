Plantilla para ChipKIT
======================
La idea de esta plantilla es colocar el código fuente del programa en src y las
bibliotecas de terceros en lib.
- Para compilar y enlazar: make
- Para cargar en placa: make load

Se incluye el script "prep_sketch.pl" que simula el comportamiento de MPIDE
declarando las funciones definidas en "sketch.pde" al principio del mismo,
junto con la inclusión de WProgram.h.
