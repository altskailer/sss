extends Control

@onready var canvas_group = $CanvasGroup
@onready var button = $CanvasGroup/VBoxContainer/Button

var fading_out = false

func _ready():
    # نبدأ بشفافية كاملة
    canvas_group.group_opacity = 1.0
    button.pressed.connect(_on_button_pressed)

func _on_button_pressed():
    # عكس حالة التلاشي (إذا كان ظاهر يخفيه والعكس)
    fading_out = !fading_out
    var target_opacity = 0.0 if fading_out else 1.0
    fade_to(target_opacity, 1.0) # المدة ثانية واحدة

func fade_to(target_opacity: float, duration: float):
    var tween = create_tween()
    tween.tween_property(canvas_group, "group_opacity", target_opacity, duration)
    
