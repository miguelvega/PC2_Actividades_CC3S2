# Parte 1  Algoritmos, Programación Orientada a Objetos

Escribe una función que acepte una cadena que contenga todas las letras del alfabeto excepto una y devuelva la letra que falta. Por ejemplo, la cadena the quick brown box jumps over a lazy dog contiene todas las letras del alfabeto excepto la letra f. La función debe tener una complejidad temporal de O(n).

```
def letra_faltante(cadena)
    cadena = cadena.downcase # Primero pasamos la cadena a minusculas
    abecedario = ('a'..'z').to_a #Transformamos a un arreglo
    cadena.each_char do |letra|
    abecedario.delete(letra) if abecedario.include?(letra) #Borraremos las letras que estan en el abecedario que estan contenidas en la cadena
    end
    abecedario[0]# Con lo cual solo nos quedaria una unica letra dentro del abecedario
end

cadena = "the quick brown box jumps over a lazy dog"
letraFaltante = letra_faltante(cadena)
"La letra que falta es: #{letraFaltante}"

```
Puede visualizar la ejecucion y los comentarios asociados al archivo `PC2_Parte1_MIguelVega.ipynb` ubicado en este repositorio, con el fin de explicar la funcion de cada linea de codigo.


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

![Captura de pantalla de 2023-10-11 12-35-20](https://github.com/miguelvega/PC2_Actividades_CC3S2/assets/124398378/15df3a6f-6cb5-416e-941f-42c770b67c75)
