# Noter om erfaringer med Godot Engine 3.5

-----------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------


## Database med elephantSQL og Godot 

Programmet:
- https://github.com/digitaltdesignlyngby/GodotDatabaseProjekt  

Her videoer jeg har lavet (ajrp):
- Godot database 1/2 : https://youtu.be/0WiEkQu0DYE 
- Godot database 2/2 : https://youtu.be/lK5rFEQatAA
- Godot med Github : https://youtu.be/2abX2lDjOZQ

-----------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------


## Lav en platformer i Godot

Programmet:
- https://github.com/digitaltdesignlyngby/GodotPlatformer

Her videoer jeg har set ...
- Video kanal : https://www.youtube.com/playlist?list=PLP6PvXLevG9JddCjycHv8Lt3nRerIV7Go
- Andrew Hoffman platformer tutorial : https://www.youtube.com/watch?v=dpBcidxfJSg&list=PLP6PvXLevG9JddCjycHv8Lt3nRerIV7Go&index=2
- Andrew Hoffman om tilmap : https://www.youtube.com/watch?v=d5IyWAyk3T8


## Tilføjer bullets til platformer (projekt ovenfor)
Bullets
1. Tilføjer ny Area2D node - der består af en sprite node og en collision2D node
2. Laver TilesMap til group: "MapGroup" og laver Player til group : "PlayerGroup"
3. Tilføjer script til Bullet med signal på collsion der opfanges af den selv og laver "queue_free" på begge objekter hvis de ikke er i group map eller player
4. Ændrer script på player så den kan lave instanser af Bullet, der positioneres samme sted som Player med tilføjes til parent som er Level1...

## Camera fra to vinkler

CameraSystem
Ændrer camera view ..
1. Laver 2 forskellige kamera - et på Level og et andet på Player
2. (GUI.tscn) Laver 2 forskellige instanser af GUI scener - et på level og et på player
3. (GUI.gd)Når man trykker på GUI i level skifter kamera til player og den ene GUI bliver usynlig og den anden synlig
4. Selve tilstanden huskes i den globale boolean variabel "cameraPlayer" i singletonen "globals.gd"...
I settings "project.godot" - sættes autoload til at autoloade "globals.gd"


## VIGTIGT FOR EXPORT AF SPIL TIL FEKS. HTML5:

EDITOR BUILD
```
		var b = bullet.instance(PackedScene.GEN_EDIT_STATE_INSTANCE)
```

BYGGET TIL HTML5 dvs. EXPORTERET OG IKKE BYGGET I EDITOR:
```
		var b = bullet.instance()
```

## Enemies NPC
1. Laver en scene der nedarver fra Player ved at oprette en ny scene - og klikke på "instance child scene" ved siden af "+" (new scene)
2. Derefter højreklikke på scenen og trykke "exetend script" - det nye script hedder "Enemy.gd"
3. I "Enemy.gd" overskrives funktionen "get_input(delta)" og istedet for at styre med knapperne - laver vi nu random tal der styre "hop" og "bevægelse"
4. Der tilføjes en ny sprite der placeres ovenpå den anden ... et par solbriller... så man kan se forskel på spilleren og fjenderne

## Input for web!
Forsøg på at tilføje styring af input "InputEventTouch" til touch-screen sevices...
Virker ikke helt med InputEventScreenTouch da det kun virker på selve trykket,...

-----------------------------------------------------------------------------------------------------------------------------

GUI - nu med controls til at styre spilleren
1. Anvendelse af globals: up, left, right og shoot sat af knapperne
2. Player objektet tjekker om nogle af værdierne er sande og reagerer

