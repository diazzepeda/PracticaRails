Buenas practicas en Ruby On Rails
1. Revisar indentacion
2. Revisar espacios entre condicionales o variables
3. Validar con RuboCop
4. Utilizar map o each en ciclos
5. Saltar una linea de ultimo en todos los archivos

##### Algunos métodos numéricos útiles
- > num.event? = true or false :´Devuelve true si int es un número par´
- > num.odd? = true or false :´Devuelve true si int es un número impar´

##### Escapes 
- > \\  #=> ´Need a backslash in your string?´
- > \b  #=> ´Backspace´
- > \r  #=> ´Carriage return, for those of you that love typewriters´
- > \n  #=> ´Newline. You'll likely use this one the most.´
- > \s  #=> ´Space´
- > \t  #=> ´Tab´
- > \"  #=> ´Double quotation mark´
- > \'  #=> ´Single quotation mark´

##### Algunos métodos de cadena utiles
- > "hola".capitalize = "Hola" :´Convierte el string con la primera letra en mayuscula.´
- > "hola".upcase = "HOLA" :´Convierte el string en mayusculas.´
- > "HOLA".downcase = "hola" :´Convierte el string en minisculas.´
- > "HOLA".empty = false :´Valida si el string esta vacio.´
- > "hola".capitalize = "Hola" :´Convierte el string con la primera letra en mayuscula.´
- > "hola".include?("z") = false :´Valida si incluye la letra "s" en el string.´

##### Simbolos
Para crear un símbolo, simplemente coloque dos puntos al principio de algún texto:
- > :my_symbol

Símbolos vs. Cadenas
Para tener una mejor idea de cómo se almacenan los símbolos en la memoria, dale un giro a esto en irb o un REPL. El método #object_id devuelve un identificador entero para un objeto. (Y recuerda: ¡en Ruby, todo es un objeto!)

- > "string" == "string"  #=> true
- > "string".object_id == "string".object_id  #=> false
- > :symbol.object_id == :symbol.object_id    #=> true
- 
##### Metodos de comparacion

#eql? comprueba tanto el tipo de valor como el valor real que contiene.
- > 5.eql?(5.0) #=> false; although they are the same value, one is an integer and the other is a float
- > 5.eql?(5)   #=> true

#equal? comprueba si ambos valores son exactamente el mismo objeto en la memoria. Esto puede ser un poco confuso debido a la forma en que las computadoras almacenan algunos valores para la eficiencia. Dos variables que apuntan al mismo número generalmente devolverán .true
psdt: Sirve tambien para cadenas
- > a = 5
- > b = 5
- > a.equal?(b) #=> true

#operador especial que se conoce cariñosamente como el operador de la nave espacial. A diferencia de los otros operadores de comparación, que todos devuelven o , el operador de la nave espacial devuelve uno de los tres valores numéricos.truefalse
<=> (operador de naves espaciales) devuelve lo siguiente:
-1 si el valor de la izquierda es menor que el valor de la derecha;
0 si el valor de la izquierda es igual al valor de la derecha; y
1 si el valor de la izquierda es mayor que el valor de la derecha.
- > 5 <=> 10    #=> -1
- > 10 <=> 10   #=> 0
- > 10 <=> 5    #=> 1

#unless es exactamente lo contrario de . Es un negado.ifif
En otras palabras, los siguientes tres ejemplos son equivalentes.
```
unless number.even?
  runs if `number` is NOT even
else
  runs if `number` is even
end

if not number.even?
  runs if `number` is NOT even
else
  runs if `number` is even
end

if !number.even?
  runs if `number` is NOT even
else
  runs if `number` is even
end
```
Validar si se ingreso un numero
```
def even_odd(number)
  unless number.is_a? Numeric
    return "A number was not entered."
  end
  if number % 2 == 0
    "That is an even number."
  else
    "That is an odd number."
  end
end
puts even_odd(20) #=>  That is an even number.
puts even_odd("Ruby") #=>  A number was not entered.
```
Métodos de predicado
A veces encontrará métodos Ruby incorporados que tienen un signo de interrogación () al final de su nombre, como , , o . Todos estos son métodos de predicados, que es una convención de nomenclatura que Ruby utiliza para los métodos que devuelven un booleano, es decir, devuelven o bien .?even?odd?between?truefalse
```
puts 5.even?  #=> false
puts 6.even?  #=> true
puts 17.odd?  #=> true
puts 12.between?(10, 15)  #=> true
```
Metodos Select y Reject 
```
friends = ['Sharon', 'Leo', 'Leila', 'Brian', 'Arun']

friends.select { |friend| friend != 'Brian' }
 #=> ["Sharon", "Leo", "Leila", "Arun"]
 ```
o incluso mejor y más al grano:
```
friends = ['Sharon', 'Leo', 'Leila', 'Brian', 'Arun']

friends.reject { |friend| friend == 'Brian' }
 #=> ["Sharon", "Leo", "Leila", "Arun"]
```
Metodo each_with_index
```
ruits = ["apple", "banana", "strawberry", "pineapple"]

fruits.each_with_index { |fruit, index| puts fruit if index.even? }

#=> apple
#=> strawberry
#=> ["apple", "banana", "strawberry", "pineapple"]
```
Metodo map
```
friends = ['Sharon', 'Leo', 'Leila', 'Brian', 'Arun']

friends.map { |friend| friend.upcase }
#=> `['SHARON', 'LEO', 'LEILA', 'BRIAN', 'ARUN']`
```
Metodo Select
```
responses = { 'Sharon' => 'yes', 'Leo' => 'no', 'Leila' => 'no', 'Arun' => 'yes' }
responses.select { |person, response| response == 'yes'}
#=> {"Sharon"=>"yes", "Arun"=>"yes"}
```
Metodo include?
```
numbers = [5, 6, 7, 8]

numbers.include?(6)
#=> true

numbers.include?(3)
#=> false
```
Metodo any?
```
numbers = [21, 42, 303, 499, 550, 811]

numbers.any? { |number| number > 500 }
#=> true

numbers.any? { |number| number < 20 }
#=> false
```
Metodo all?
```
fruits = ["apple", "banana", "strawberry", "pineapple"]

fruits.all? { |fruit| fruit.length > 3 }
#=> true

fruits.all? { |fruit| fruit.length > 6 }
#=> false
```
Metodo none?
```
fruits = ["apple", "banana", "strawberry", "pineapple"]

fruits.none? { |fruit| fruit.length > 10 }
#=> true

fruits.none? { |fruit| fruit.length > 6 }
#=> false
```










