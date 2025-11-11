extends Area2D

signal collected  # إشارة لما اللاعب يجمع الكوين

func _ready():
    connect("body_entered", Callable(self, "_on_body_entered"))

func _on_body_entered(body):
    if body.name == "Player":  # غيّر الاسم حسب عقدة اللاعب
        emit_signal("collected")
        queue_free()  # احذف الكوين بعد جمعها
