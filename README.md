extends Node2D

var coin = 0

func _process(delta: float) -> void:
	# تحديث عداد الكوين على الشاشة
	$CanvasLayer/Label.text = "Coin :"  + str(coin)

func _on_coin_body_entered(body: Node2D) -> void:
	if body.name == "PLAYER":
		coin += 1
		$Coin.queue_free()

func _on_door_body_entered(body: Node2D) -> void:
	if body.name == "PLAYER":
		get_tree().change_scene_to_file("res://scenes/hard.tscn")
