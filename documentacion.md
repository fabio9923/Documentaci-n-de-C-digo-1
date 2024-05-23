#   Documentación
## IntCell.h
```c++
#ifndef INTCELL_H
#define INTCELL_H

class IntCell {
public:
IntCell() = default;
IntCell(int newValue = 0);
IntCell(const IntCell &rhs);
IntCell(IntCell &&rhs) noexcept;
~IntCell() = default;

IntCell &operator=(const IntCell &rhs);
IntCell &operator=(IntCell &&rhs) noexcept;
IntCell &operator=(int rhs);
IntCell &operator+(const IntCell &rhs);
IntCell &operator+(int rhs);
IntCell &operator-(const IntCell &rhs);
IntCell &operator-(int rhs);

int getValue() const;
void setValue(int newValue);

private:
int storedValue;
int storedValue2;
int storedValue3;
};

#endif  // INTCELL_H
```
###### En este codigo la primera parte que es :
```c++
IntCell() = default; // predeterminado
IntCell(int newValue = 0); // valor inical opcional 
```
###### Se empiesan con los constructores  predeterminado y un constructor con un valor inicial que estan públicos el _predeterminado que es el que iniciará intcell con un valor de 0_ y el _constructor inicial acepta un valor inicial opcional para que lo tenga intcell_.

```c++
IntCell(const IntCell &rhs); // copia 
IntCell(IntCell &&rhs) noexcept;// movimiento
~IntCell() = default; // destructor
```
###### En esta parte del código tenemos  copia, movimiento y destructor la función de cada uno es comenzando con el constructor de copia  el  cual crea una nueva instancia de intcell copiando los datos de otra instancia, el constructor de movimiento crea una nueva instancia moviendo los datos de otra instancia y por último el destructor Este se encarga de liberar recursos al ser destruido un objeto.

```c++
IntCell &operator=(const IntCell &rhs);//copia
IntCell &operator=(IntCell &&rhs) noexcept;//movimiento
IntCell &operator=(int rhs);//valor entero
IntCell &operator+(const IntCell &rhs);//suma con otra celda
IntCell &operator+(int rhs);//suma
IntCell &operator-(const IntCell &rhs);//resta con otra celda
IntCell &operator-(int rhs);//resta
```

###### Estos son los operadores de asignación y de aritmética los cuales se usan para copiar o mover valores entre los objetos  intcell y los aritméticos que como su nombre lo indica son para hacer las operaciones que indique el código en este caso son sumas y restas.

```c++
int getValue() const; //obtener valor
void setValue(int newValue);//dar valor
```
###### Los siguientes métodos se usan para obtener el valor que esté almacenado en intcell y para darle un valor para que almacene intcell.

```c++
int storedValue;//valor almacenado 1
int storedValue2;//valor almacenado 2
int storedValue3;//valor almacenado 3
```
###### son variables privadas que almacenaran los valores en cada instancia intcell.

## IntCell.cpp
```c++
#include "IntCell.h"

IntCell::IntCell(int newValue) : storedValue(newValue) {}

IntCell::IntCell(const IntCell &rhs) : storedValue(rhs.storedValue) {}

IntCell::IntCell(IntCell &&rhs) noexcept : storedValue(rhs.storedValue) {}

IntCell &IntCell::operator=(const IntCell &rhs) {
    if (this != &rhs) {
        storedValue = rhs.storedValue;
    }
    return *this;
}

IntCell &IntCell::operator=(IntCell &&rhs) noexcept {
    if (this != &rhs) {
        storedValue = rhs.storedValue;
        rhs.storedValue = 0;
    }
    return *this;
}

IntCell &IntCell::operator=(int rhs) {
    storedValue = rhs;
    return *this;
}

IntCell &IntCell::operator+(const IntCell &rhs) {
    storedValue = storedValue + rhs.storedValue;
    return *this;
}

IntCell &IntCell::operator+(int rhs) {
    storedValue = storedValue + rhs;
    return *this;
}

IntCell &IntCell::operator-(const IntCell &rhs) {
    storedValue = storedValue - rhs.storedValue;
    return *this;
}

IntCell &IntCell::operator-(int rhs) {
    storedValue = storedValue - rhs;
    return *this;
}

int IntCell::getValue() const {
    return storedValue;
}

void IntCell::setValue(int newValue) {
    storedValue = newValue;
}
```
```c++
//implementacion constructores

//valor inical
IntCell::IntCell(int newValue) : storedValue(newValue) {}
//copia
IntCell::IntCell(const IntCell &rhs) : storedValue(rhs.storedValue) {}
//movimiento 
IntCell::IntCell(IntCell &&rhs) noexcept : storedValue(rhs.storedValue) {}

```
###### Estos constructos se encargan de inicializar el valor de newvalue, crean una nueva instancia intcell con el valor de otra instancia y crea otra instancia moviendo los datos de otra instancia.

```c++
//implementacion operadores

//copia
IntCell &IntCell::operator=(const IntCell &rhs) {
    if (this != &rhs) {
        storedValue = rhs.storedValue;
    }
    return *this;
}
//movimiento
IntCell &IntCell::operator=(IntCell &&rhs) noexcept {
    if (this != &rhs) {
        storedValue = rhs.storedValue;
        rhs.storedValue = 0;
    }
    return *this;
}
//asignacion de valor
IntCell &IntCell::operator=(int rhs) {
    storedValue = rhs;
    return *this;
}
//suma con otra celda
IntCell &IntCell::operator+(const IntCell &rhs) {
    storedValue = storedValue + rhs.storedValue;
    return *this;
}
//suma
IntCell &IntCell::operator+(int rhs) {
    storedValue = storedValue + rhs;
    return *this;
}
//resta con otra celda
IntCell &IntCell::operator-(const IntCell &rhs) {
    storedValue = storedValue - rhs.storedValue;
    return *this;
}
//resta
IntCell &IntCell::operator-(int rhs) {
    storedValue = storedValue - rhs;
    return *this;
}
```

###### En este espeacio se implementa los operadores para que cumpla la funcion cada uno.

```c++
//implementacion de metodos
//obtener valor
int IntCell::getValue() const {
    return storedValue;
}
//dar un valor
void IntCell::setValue(int newValue) {
    storedValue = newValue;
```

###### en esto se implementan los metodos para obtener un valor o establecer una nuevo.

## RAM:
###### Todas las instancias de intcell ocupan memoria en el que también se puede almacenar storedvalue los operadores y métodos no ocupan memoria ram extra por que hacen las operaciones en storadvalue y las variables locales  si ocupan memoria adicional pero  se libera cuando el método se finaliza de ejecutar.
