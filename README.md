extends Node2D

@export var coin_scene: PackedScene
@export var number_of_coins := 50
@export var spawn_area := Rect2(Vector2(0,0), Vector2(1000,600))

func _ready():
    randomize()
    for i in range(number_of_coins):
        var coin = coin_scene.instantiate()
        coin.position = Vector2(
            randf_range(spawn_area.position.x, spawn_area.end.x),
            randf_range(spawn_area.position.y, spawn_area.end.y)
        )
        add_child(coin)
