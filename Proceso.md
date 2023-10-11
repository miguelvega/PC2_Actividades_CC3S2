# Parte 1  Algoritmos, Programación Orientada a Objetos

## Escribe una función que acepte una cadena que contenga todas las letras del alfabeto excepto una y devuelva la letra que falta. Por ejemplo, la cadena the quick brown box jumps over a lazy dog contiene todas las letras del alfabeto excepto la letra f. La función debe tener una complejidad temporal de O(n).

```
def letra_faltante(cadena)
    cadena = cadena.downcase # Primero pasamos la cadena a minusculas
    abecedario = ('a'..'z').to_a #Transformamos a un arreglo
    cadena.each_char do |letra|
    abecedario.delete(letra) if abecedario.include?(letra) #Borraremos las letras que coindicen con el abecedario y que estan contenidas en la cadena
    end
    abecedario[0]# Con lo cual solo nos quedaria una unica letra dentro del abecedario
end

cadena = "the quick brown box jumps over a lazy dog"
letraFaltante = letra_faltante(cadena)
"La letra que falta es: #{letraFaltante}"

```
Al ser un codigo pequeño la explicacion lo escribi como comentario al final de cada linea de codigo.
Puede visualizar la ejecucion y los comentarios asociados al archivo `PC2_Parte1_MIguelVega.ipynb` ubicado en este repositorio.

## Un árbol binario ordenado es aquel en el que cada nodo tiene un valor y hasta 2 hijos, cada uno de los cuales es también un árbol binario ordenado, y el valor de cualquier elemento del subárbol izquierdo de un nodo es menor que el valor de cualquier elemento en el subárbol derecho del nodo. Defina una clase colección llamada BinaryTree que ofrezca los métodos de instancia << (insertar elemento), empty? (devuelve cierto si el árbol no tiene elementos) y each (el iterador estándar que devuelve un elemento cada vez, en el orden que tú quieras). 

```
class ArbolBinario 
  attr_accessor :valor, :izq, :der

  def initialize(value)
    @valor = value # En un inicio este seria nuestro nodo raiz
    @izq = nil
    @der = nil
  end

  def insertar_elemento(elemento)
    if elemento <= @valor
       if @izq.nil?
        @izq = ArbolBinario.new(elemento)
       else
        @izq.insertar_elemento(elemento)
       end
   else
      if @der.nil?
       @der = ArbolBinario.new(elemento)
      else
       @der.insertar_elemento(elemento)
   end
  end

  end

  def empty?
    @izq.nil? && @der.nil?
  end

  def each(&block)
    @izq.each(&block) if @izq
    block.call(@valor)
    @der.each(&block) if @der
  end
end

arbol = ArbolBinario.new(6)
arbol.insertar_elemento(4)
arbol.insertar_elemento(7)
arbol.insertar_elemento(5)
arbol.insertar_elemento(2)

puts "El arbol esta vacio? #{arbol.empty?}"

puts "Elementos en el arbol:"
arbol.each { |elemento| puts elemento }

```
En un inicio cuando queremos crear una instancia de la clase ArbolBinario, el argumento sera la raiz del arbol como se puede
apreciar en el construvtor de dicha clase.
método llamado insertar_elemento` que permite insertar un elemento en el árbol binario, para ello compara `elemento` con `valor` para determinar si debe insertarse en el subárbol izquierdo (izq) o en el subárbol derecho (der) del nodo actual
El metodo `empty?` verifica si el árbol está vacío. El árbol se considera vacío si ambos 
subárboles, izquierdo y derecho, son nil.




# Parte 3 Rail
Relizamos la configuraciones pertinentes(tuve algunas problemas) en nuestro dispositivo y para asegurarse de que todo funcione, ejecutamos la aplicación localmente.
![Captura de pantalla de 2023-10-11 09-27-44](https://github.com/miguelvega/PC2_Actividades_CC3S2/assets/124398378/34e4aa48-a9dc-4783-9327-a99e2384516f)

Luego, nos dirigimos a nuestro navegador, colocamos `http://localhost:3000`, con lo cual deberiamos ver la página de inicio genérica de Ruby on 
Rails, que en realidad es proporcionada por tu aplicación
![Captura de pantalla de 2023-10-11 09-27-56](https://github.com/miguelvega/PC2_Actividades_CC3S2/assets/124398378/eb8e4da2-84f0-4101-8208-6da643d27a08)

Rails define tres entornos (production, development y test), cada uno de los cuales gestiona tu propia base de datos independiente. Rails almacena estos entornos y los medios para conectarse a la base de datos asociada con cada uno de ellos en config/database.yml




![Captura de pantalla de 2023-10-11 12-05-36](https://github.com/miguelvega/PC2_Actividades_CC3S2/assets/124398378/1de54ab7-c244-4d9d-9616-4bb27166712a)

```
class CreateMovies < ActiveRecord::Migration[6.1]
  def change
    create_table 'movies' do |t|
      t.string 'title'
      t.string 'rating'
      t.text 'description'
      t.datetime 'release_date'

      t.timestamps
    end
  end
end

```


![Captura de pantalla de 2023-10-11 12-08-21](https://github.com/miguelvega/PC2_Actividades_CC3S2/assets/124398378/9e72bada-9869-4b65-a078-2665da779014)

![Captura de pantalla de 2023-10-11 12-09-16](https://github.com/miguelvega/PC2_Actividades_CC3S2/assets/124398378/905f8b7e-17cf-4d1e-b767-f3e569ff647e)

![Captura de pantalla de 2023-10-11 12-09-24](https://github.com/miguelvega/PC2_Actividades_CC3S2/assets/124398378/6b17bc67-9f27-491c-a043-4da472364c88)

```
class Movie < ActiveRecord::Base

end

```


![Captura de pantalla de 2023-10-11 12-25-17](https://github.com/miguelvega/PC2_Actividades_CC3S2/assets/124398378/1f458fd2-2dd6-430e-a1e1-2d33fea8894a)

Sembramos la base de datos (es decir, agregar datos iniciales) con algunas películas para hacer que el resto de la actividad sea más interesante. Para ellos copiamos el siguiente codigo en `db/seeds.rb` y ejecutamos rake db:seed.

```
# Seed the RottenPotatoes DB with some movies.

more_movies = [

{:title => 'Ganibal', :rating => 'G',

:release_date => '25-Nov-1992'},

{:title => 'Fuerza bruta', :rating => 'R',

:release_date => '21-Jul-1989'},

{:title => 'The Ring', :rating => 'PG-13',

:release_date => '10-Aug-2011'},

{:title => 'Alien: The Return ', :rating => 'PG',

:release_date => '12-Jun-1981'}

] 
```
Ejecutamos nuevamente el comando `Rails comsole` y realizamos algunas consultas para ver el contenido de la base de datos.
Con lo cual se puede apreciar los registros añadidos previamente en la base de datos y para ello hemos usado en primera instancia `Movie.first`para verificar si tenemos datos en la base de datos y para inspeccionar la primera entrada para asegurarnos de que se crearon correctamente. Tambien, hemos usado `Movie.all` para mostrar la lista de todas las películas en la base de datos.`
![Captura de pantalla de 2023-10-11 12-35-20](https://github.com/miguelvega/PC2_Actividades_CC3S2/assets/124398378/15df3a6f-6cb5-416e-941f-42c770b67c75)
