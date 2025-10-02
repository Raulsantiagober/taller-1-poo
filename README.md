Taller: POO y modificadores de acceso
en Python


Instrucciones


• Lee cada fragmento, ejecuta mentalmente el código y responde lo que se
pide. • Recuerda: en Python no hay “modificadores” como en Java/C++; se
usan convenciones:

o Público: nombre

o Protegido (convención): _nombre

o Privado (name mangling): __nombre se convierte a
_<Clase>__nombre • No edites el código salvo que la pregunta lo solicite.
Parte A. Conceptos y lectura de código

1) Selección múltiple
Dada la clase:

class A:

x = 1

_y = 2

__z = 3

a = A()

¿Cuáles de los siguientes nombres existen como atributos accesibles directamente
desde a?

A) a.x

B) a._y

C) a.__z

D) a._A__z

A,B,D; A al ser público, al ser de convención pero accesible y de al
ser name mangling

3) Salida del programa
   
class A:
def __init__(self):

self.__secret = 42

a = A()

print(hasattr(a, '__secret'), hasattr(a,'_A__secret'))

¿Qué imprime?

Imprime: False True

5) Verdadero/Falso (explica por qué)
6) 
a) El prefijo _ impide el acceso desde fuera de la
clase. b) El prefijo __ hace imposible acceder al
atributo.

c) El name mangling depende del nombre de la clase.

a) El prefijo _ impide el acceso es Falso, es solo convención.

b) El prefijo __ hace imposible acceder es Falso, se puede con name mangling.

c) El name mangling depende del nombre de la clase Verdadero.
8) Lectura de código

class Base:
def __init__(self):
self._token = "abc"
class Sub(Base):
def reveal(self):
return self._token
print(Sub().reveal())
¿Qué se imprime y por qué no hay error de acceso?
imprime abc ya que _tocken es accesible en subclases.
9) Name mangling en herencia
class Base:
def __init__(self):
self.__v = 1
class Sub(Base):
def __init__(self):
super().__init__()
self.__v = 2
def show(self):
return (self.__v, self._Base__v)
print(Sub().show())
¿Cuál es la salida?
Imprime: (2, 1)
10) Identifica el error
class Caja:
__slots__ = ('x',)
