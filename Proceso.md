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
Puede visualizar la ejecucion y los comentarios asiaciados explicando la funcion de cada linea en el archico con extension .ipynb en esgte repositorio.


# Parte 3 Rail
Relizamos la configuraciones pertinentes(tuve algunas problemas) en nuestro dispositivo y para asegurarse de que todo funcione, ejecutamos la aplicación localmente.
![Captura de pantalla de 2023-10-11 09-27-44](https://github.com/miguelvega/PC2_Actividades_CC3S2/assets/124398378/34e4aa48-a9dc-4783-9327-a99e2384516f)

Luego, nos dirigimos a nuestro navegador, colocamos `http://localhost:3000`, con lo cual deberiamos ver la página de inicio genérica de Ruby on 
Rails, que en realidad es proporcionada por tu aplicación
![Captura de pantalla de 2023-10-11 09-27-56](https://github.com/miguelvega/PC2_Actividades_CC3S2/assets/124398378/eb8e4da2-84f0-4101-8208-6da643d27a08)
