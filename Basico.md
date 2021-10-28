# Intruducción a c++
[🏠Home](Readme.md)

Los archivos de **C++** se dividen en dos **.h y el cpp.**  
### **_Clases en UE4_**:
> En Unreal Engine hay diferentes clases entre ellas estan los Actores, Pawns, Character, Actor Component, etc. Tambien podremos crear nuestras propias clases.

Dentro de una clase en la parte del .h tenemos los #include y luego el resto.
Dentro de class hay diferentes modulos 


### **_Variables_**:
> En Unreal Engine hay diferentes variables y podemos crear variables propias. Las variables casi siempre se crean en el archivo .h

#### Modificadores de _Variables_:
> En las variables existen [los modificadores](https://docs.unrealengine.com/4.26/en-US/ProgrammingAndScripting/GameplayArchitecture/Properties/Specifiers/) que son llamados antes de una variable, para definirlos se tiene que escribir **UPROPERTY( )**   
 
 Los mas usados son:  
 1-**UPROPERTY(EditAnywhere)** int Example1 [_Se puede editar donde sea_]  
 2-**UPROPERTY(VisibleAnywhere)** int Example1 [_Se puede ver donde sea_]  
 3-**UPROPERTY(BlueprintReadOnly**) int Example1 [_Se puede ver en blueprint_]   
 4-**UPROPERTY(BlueprintEditOnly)** int Example1 [_Se puede editar en blueprint_]  
 5-**UPROPERTY(BlueprintReadWrite)** int Example1 [_Se puede editar en blueprint_]

 tambien se pueden poner en categorias por ejemplo:

>UPROPERTY(EditDefaultsOnly, Category = "FX")  
>UParticleSystem* ExplosionEffect;   

Y en el engine se veria algo asi:  
[![Muy nashe El pablito!](Imagenes\Engine\CategoriaExample.png "ANASHE")](https://github.com/Pablyco/Documentacion/blob/master/Imagenes/Engine/CategoriaExample.png?raw=true)


### **_Eventos_**:

>Son situaciones donde detectamos algo y nos pasa un dato, valor, etc. Por ejemplo el tick:

Virtual void Tick(float DeltaTime) override; [_En el .h_]  
Donde:  
**Virtual** Es para en un futuro que se pueda sobreescribir este evento.  
**Void** dice que no va a devolver ningun dato.  
**Tick** es el nombre del evento.  
**float DeltaTime** Es un parametro es decir que requiere un float.  
**Override;** Es para remplazar la version original del tick que viene del padre.  

void AActor::Tick(float DeltaTime)  [_En el .cpp_]  
{
    
}

#### Habilitar _Tick_:
por default en c++ vienen desactivados el tick y debemos activarlos para ello hay que hacer el **Constructor** de nuestra clase **no es lo mismo que BeginPlay**.    

En el .h:  
APablito(); [_Nombre de tu clase con una A adelante por ejemplo APablito._]  

En el .cpp:  
APablito::APablito()  
{
    PrimaryActorTick.BcanEverTick = True; 
}

### _**Movimiento y Rotacion Basica en UE4 c++**_:

#### Movimiento:  
  
  
En el .h debemos definir variables que son necesarias las funciones: 
 
 en cpp la funcione "**AddActorLocalOffset()**" nos pide un vector en el caso de UE4 es un FVector. Entonces en el .h Deberiamos definir una variable para esta funcion por ejemplo:  

UPROPERTY(EditAnywhere)  
FVector Velocidad [_La vamos a establecer desde el Engine_]  
cpp :
**AddActorLocalOffset(Velocidad, true)**
, true es para definir el bSweep.  
#### Rotacion:
**AddActorLocalOffset(FVector o FQuat)**  
Es muy parecido al movimiento, entonces en el .h hay que definir las variables y en cpp la funcion con su respectiva variables. 

#### Para que todo esto funcione se deben establecer dentro del evento Tick:  

void APablito::Tick(float DeltaTime)   
{  
    AddActorLocalOffset(Velocidad, true)  
    AddActorLocalOffset(VelRotacion, true)  
}



