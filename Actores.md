### ⚡Spawn de Actores y particulas ⚡
[🏠Home](Readme.md)

Para spawnear actores vamos a necesitar una  clase(UClass) que sera la que va a ser spawneada, una location(FVector🔀), una rotacion (FRotator🔄) y los parametros del actor previamente establecidos  la funcion es la siguiente (_Ejemplo: Spawn de  un proyectil_):      

Crea una variable tipo estructura sobre los parametros.
>FActorSpawnParameters ActorSpawnParams;  

Chequea  la colision del Actor a spawnear y en este caso si la colision al  spawnear colisiona tratara de adjustar el spawn sino puede no spawneara el actor.

>ActorSpawnParams.SpawnCollisionHandlingOverride = ESpawnActorCollisionHandlingMethod::AdjustIfPossibleButDontSpawnIfColliding;

Configura el Instigator del ActorSpawnParams.
>ActorSpawnParams.Instigator  = this;
				
Spawnea el Actor con las variables previamente explicadas.			
>World->SpawnActor<AMultiPlayerProjectile>(ProjectileClass, SpawnLocation, SpawnRotation, ActorSpawnParams);

Donde
ProjectileClass = Es la clase a spawnear.  
SpawnLocation = FVector de la Location del actor.  
SpawnRotation = FRotator de la Rotacion del actor. 
ActorSpawnParams = Son los parametros ya establecidos.

Tambien hay un Blueprint para spawnear Actores de una clase.  
![Muy nashe El pablito!](/Imagenes/Engine/SpawnActor.png?raw=true "Que haces leyendo esto pa?")