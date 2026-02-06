# main.py
# EXTREMELY DETAILED 3D ADVENTURE GAME (EXPANDED VERSION)
# Engine: Ursina (Python)
# GitHub-ready + Save/Load system

from ursina import *
from ursina.prefabs.first_person_controller import FirstPersonController
import random, json, os

app = Ursina()
window.title = '3D Adventure Game'
window.fps_counter.enabled = True

# ------------------ CONSTANTS ------------------
SAVE_FILE = 'savegame.json'
WORLD_SIZE = 60
GRAVITY = 1

# ------------------ PLAYER ------------------
player = FirstPersonController(
    speed=6,
    jump_height=2,
    gravity=GRAVITY,
    mouse_sensitivity=Vec2(40, 40)
)
player.cursor.visible = False
player.hp = 100
player.level = 1
player.exp = 0

# ------------------ UI ------------------
hp_text = Text(text='HP: 100', position=(-0.85, 0.45), scale=2)
level_text = Text(text='LVL: 1', position=(-0.85, 0.40), scale=2)
info_text = Text(text='[F5] Save  [F9] Load', position=(-0.2, -0.45), scale=1.5)

# ------------------ ENVIRONMENT ------------------
Sky()
terrain = Entity(model='plane', texture='grass', collider='box', scale=(WORLD_SIZE,1,WORLD_SIZE))

# ------------------ WORLD GENERATION ------------------
blocks = []
def generate_world():
    blocks.clear()
    for x in range(-WORLD_SIZE//2, WORLD_SIZE//2, 4):
        for z in range(-WORLD_SIZE//2, WORLD_SIZE//2, 4):
            if random.random() < 0.25:
                b = Entity(
                    model='cube',
                    color=color.rgb(120,90,60),
                    position=(x,1,z),
                    scale=(2, random.randint(2,6), 2),
                    collider='box'
                )
                blocks.append(b)

generate_world()

# ------------------ ENEMIES ------------------
enemies = []
def spawn_enemies(amount=10):
    enemies.clear()
    for i in range(amount):
        e = Entity(
            model='cube',
            color=color.red,
            position=(random.randint(-25,25),1,random.randint(-25,25)),
            collider='box'
        )
        e.hp = 30 + player.level * 5
        e.speed = 2 + player.level * 0.1
        enemies.append(e)

spawn_enemies()

# ------------------ WEAPON ------------------
sword = Entity(
    model='cube',
    color=color.azure,
    scale=(0.2,1.5,0.2),
    parent=camera.ui,
    position=(0.6,-0.3),
    rotation=(0,0,-20)
)

attack_cd = 0

# ------------------ SAVE / LOAD ------------------
def save_game():
    data = {
        'player': {
            'hp': player.hp,
            'level': player.level,
            'exp': player.exp,
            'position': [player.x, player.y, player.z]
        }
    }
    with open(SAVE_FILE, 'w') as f:
        json.dump(data, f)
    print('Game Saved')


def load_game():
    if not os.path.exists(SAVE_FILE):
        print('No save file found')
        return
    with open(SAVE_FILE, 'r') as f:
        data = json.load(f)
    player.hp = data['player']['hp']
    player.level = data['player']['level']
    player.exp = data['player']['exp']
    player.position = Vec3(*data['player']['position'])
    hp_text.text = f'HP: {player.hp}'
    level_text.text = f'LVL: {player.level}'
    spawn_enemies()
    print('Game Loaded')

# ------------------ GAME LOOP ------------------
def update():
    global attack_cd
    attack_cd -= time.dt

    # Update UI
    hp_text.text = f'HP: {int(player.hp)}'
    level_text.text = f'LVL: {player.level}'

    # Enemy AI
    for e in enemies[:]:
        if distance(e, player) < 15:
            e.look_at(player)
            e.position += e.forward * time.dt * e.speed
        if distance(e, player) < 1.5:
            player.hp -= 15 * time.dt
        if e.hp <= 0:
            destroy(e)
            enemies.remove(e)
            player.exp += 10
            if player.exp >= 50:
                player.level += 1
                player.exp = 0
                spawn_enemies(12)

    if player.hp <= 0:
        application.quit()

# ------------------ INPUT ------------------
def input(key):
    global attack_cd
    if key == 'left mouse down' and attack_cd <= 0:
        attack_cd = 0.5
        sword.animate_rotation((0,0,40), duration=0.1)
        sword.animate_rotation((0,0,-20), delay=0.1, duration=0.1)
        for e in enemies:
            if distance(e, player) < 2:
                e.hp -= 20

    if key == 'f5':
        save_game()
    if key == 'f9':
        load_game()

# ------------------ START ------------------
app.run()

"""
GitHub Structure:
/adventure-game
 ├─ main.py
 ├─ savegame.json (auto-created)
 ├─ assets/
 ├─ README.md
 └─ requirements.txt
"""
