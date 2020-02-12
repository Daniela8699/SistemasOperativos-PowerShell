## Ejercicios
1. Cree dos archivos de texto similares (con una o dos líneas diferentes).
   Compárelos empleando ``diff``.
   ```console
   PS C:\Users\danie> notepad prueba1.txt
   PS C:\Users\danie> notepad prueba2.txt
   PS C:\Users\danie> type prueba1.txt
    pruebaaaaa
   PS C:\Users\danie> type prueba2.txt
    textoooo
    
   PS C:\Users\danie> diff -ReferenceObject (Get-Content prueba1.txt) -DifferenceObject (Get-Content prueba2.txt)

   InputObject SideIndicator
   ----------- -------------
   textoooo    =>           
   pruebaaaaa  <=  
   ```
2. Qué ocurre si se ejecuta:
   ```powershell
   get-service | export-csv servicios.csv | out-file
   ```
   Por qué?
   ``` powershell
   out-file : No se puede procesar el argumento porque el valor del argumento "path" es NULL. Cambie el valor del argumento "path" a un valor no nulo.
   En línea: 1 Carácter: 42
   + get-service | export-csv servicios.csv | out-file
   +                                          ~~~~~~~~
       + CategoryInfo          : InvalidArgument: (:) [Out-File], PSArgumentNullException
       + FullyQualifiedErrorId : ArgumentNull,Microsoft.PowerShell.Commands.OutFileCommand
   ```
   
   Da un error, debido a que cuando el sistema intenta ejecutar out-file se da cuenta que en ese momento el pipe esta vacio y no puede exportar nada.
3. Cómo haría para crear un archivo delimitado por puntos y comas (;)?
   PISTA: Se emplea ``export-csv``, pero con un parámetro adicional.
4. ``Export-cliXML`` y ``Export-CSV`` modifican el sistema, porque pueden crear
   y sobreescribir archivos. Existe algún parámetro que evite la
   sobreescritura de un archivo existente? Existe algún parámetro que
   permita que el comando pregunte antes de sobresscribir un archivo?
5. Windows emplea configuraciones regionales, lo que incluye el separador de
   listas. En Windows en inglés, el separador de listas es la coma (,).
   Cómo se le dice a ``Export-CSV`` que emplee el separador del sistema en lugar
   de la coma?
6. Identifique un cmdlet que permita generar un número aleatorio.
7. Identifique un cmdlet que despliegue la fecha y hora actuales.
8. Qué tipo de objeto produce el cmdlet de la pregunta 7?
9. Usando el cmdlet de la pregunta 7 y ``select-object``, despliegue solamente
   el día de la semana, así:

```console
   DayOfWeek
   ---------
    Thursday
```

10. Identifique un cmdlet que muestre información acerca de parches (hotfixes)
    instalados en el sistema.
11. Empleando el cmdlet de la pregunta 10, muestre una lista de parches
    instalados. Luego extienda la expresión para ordenar la lista por fecha
    de instalación, y muestre en pantalla únicamente la fecha de instalación,
    el usuario que instaló el parche, y el ID del parche. Recuerde examinar
    los nombres de las propiedades.
12. Complemente la solución a la pregunta 11, para que el sistema ordene los
    resultados por la descripción del parche, e incluya en el listado la
    descripción, el ID del parche, y la fecha de instalación.
    Escriba los resultados a un archivo HTML.
13. Muestre una lista de las 50 entradas más nuevas del log de eventos System.
    Ordene la lista de modo que las entradas más antiguas aparezcan primero;
    las entradas producidas al mismo tiempo deben ordenarse por número índice.
    Muestre el número índice, la hora y la fuente para cada entrada. Escriba
    esta información en un archivo de texto plano.