from tkinter import Tk, Canvas, mainloop, NW
from PIL import Image, ImageTk
window_width = 600
window_height = 600
tk = Tk()
c = Canvas(tk, width=window_width, height=window_height, bg='white')
c.pack()
game_map = [
    [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
    [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
    [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
    [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
    [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
    [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
    [0, 1, 1, 1, 1, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0],
    [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0],
    [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 1, 1, 1, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0],
    [0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0],
    [0, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
    [0, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
    [0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
    [0, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 1, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
    [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
    [0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 0],
    [0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 1, 1, 0, 0, 0, 1, 0, 0, 0],
    [0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1, 1, 1, 1],
    [0, 0, 0, 1, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
    [0, 0, 1, 0, 0, 0, 1, 1, 1, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
    [0, 0, 0, 0, 0, 0, 1, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
    [0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
    [0, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
    [0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 1, 0, 1, 0, 0, 0, 0, 0],
    [0, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 1, 1, 1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0],
    [0, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 1, 0, 0, 0, 0],
    [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 1, 0, 0, 0],
    [0, 0, 0, 1, 1, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0],
    [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 1, 1, 0, 0, 0, 0],
    [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
    [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
    [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1],
]

bullet=[]
block_width = window_width // 30
block_height = window_height // 30
vrag = ImageTk.PhotoImage(Image.open("C:/Users/S2016/Documents/GeekHack III/soldat.jpg").resize((block_width, block_height)))
brick = ImageTk.PhotoImage(Image.open("C:/Users/S2016/Documents/GeekHack III/stena.jpg").resize((block_width, block_height)))
grass = ImageTk.PhotoImage(Image.open("C:/Users/S2016/Documents/GeekHack III/zemlya.jpg").resize((block_width, block_height)))
UP = ImageTk.PhotoImage((Image.open("C:/Users/S2016/Documents/GeekHack III/purple_guy3.png").convert('RGBA').resize((block_width, block_height))))
DOWN = ImageTk.PhotoImage((Image.open("C:/Users/S2016/Documents/GeekHack III/purple_guy1.png").convert('RGBA').resize((block_width, block_height))))
LEFT = ImageTk.PhotoImage((Image.open("C:/Users/S2016/Documents/GeekHack III/purple_guy2.png").convert('RGBA').resize((block_width, block_height))))
RIGHT = ImageTk.PhotoImage((Image.open("C:/Users/S2016/Documents/GeekHack III/purple_guy.png").convert('RGBA').resize((block_width, block_height))))
bull = ImageTk.PhotoImage((Image.open('C:/Users/S2016/Documents/GeekHack III/pulya.png').convert('RGBA').resize((block_width, block_height))))
for i in range(30):
    for j in range(30):
        if game_map[i][j] == 0:
            c.create_image(i * block_width, j * block_height, image=grass, anchor=NW)
        if game_map[i][j] == 1:
            c.create_image(i * block_width, j * block_height, image=brick, anchor=NW)
vrag = {"vrag": c.create_image(6 * block_width, 6 * block_height, image= UP, anchor=NW, state='normal')}
tank = {
    "up": c.create_image(6 * block_width, 6 * block_height, image= UP, anchor=NW, state='normal'),
    "down": c.create_image(6 * block_width, 6 * block_height, image= DOWN, anchor=NW, state='hidden'),
    "left": c.create_image(6 * block_width, 6 * block_height, image= LEFT, anchor=NW, state='hidden'),
    "right": c.create_image(6 * block_width, 6 * block_height, image= RIGHT, anchor=NW, state='hidden')
}
c.coords(tank, 6*block_width, 6*block_height)
def turn(tank, direction):
    x, y = c.coords(tank['down'])
    for i in tank:
        if i == direction:
            c.itemconfigure(tank[i], state='normal')
        else:
            c.itemconfigure(tank[i], state='hidden')
def rotate(tank, direction):
    x, y = c.coords(tank['up'])
    turn(tank, direction)
    return (int(x // block_width), int(y // block_height))
     
def move(tank, x, y):
    c.move(tank['up'], x, y)
    c.move(tank['down'], x, y)
    c.move(tank['left'], x, y)
    c.move(tank['right'], x, y)
    
def coords(tank):
    x, y = c.coords(tank['up'])
    return (int(x // block_width), int(y // block_height))

# проверка доступности клетки
def is_available(i, j):
    if i < 0 or i >= 30 or j < 0 or j >= 30:
        return False
    if game_map[i][j] == 1:
        return False
    return True
def keyDown(key):
    global tank
    dx = 0
    dy = 0
    direction = ""
    if key.char in ('a', 'ф'):
        direction = 'left'
        x, y = coords(tank)
        rotate(tank, direction)
        if is_available(x - 1, y):
            dx = -1
    if key.char in ('d', 'в'):
        direction = 'right'
        x, y = coords(tank)
        rotate(tank, direction)
        print(x, y)
        if is_available(x + 1, y):
            dx = 1
    if key.char in ('w', 'ц'):
        direction = 'up'
        x, y = coords(tank)
        rotate(tank, direction)
        if is_available(x, y - 1):
            dy = -1
    if key.char in ('s', 'ы'):
        direction = 'down'
        x, y = coords(tank)
        if is_available(x, y + 1):
            dy = 1
    if key.char in ('q', 'й'):
        direction = 'left'
        x, y = coords(tank)
        if is_available(x - 1, y):
            dx = -1
    if key.char in ('e', 'у'):
        direction = 'right'
        x, y = coords(tank)
      
        print(x, y)
        if is_available(x + 1, y):
            dx = 1
    if key.char in ('r', 'к'):
        direction = 'up'
        x, y = coords(tank)
        rotate(tank, direction)
        if is_available(x, y - 1):
            dy = -1
    move(tank, dx * block_width, dy * block_height)
tk.bind("<KeyPress>", keyDown)

def someone_down(x, y, game_map):
    height = len(game_map[0])
    for j in range(y + 1, height):
        if game_map[x][j] == -1:
            return False
        elif game_map[x][j] == 0:
            pass
        elif game_map[x][j] == 1:
            return 1
        else:
            return game_map[x][j]
def someone_up(x, y, game_map):
    for j in range(y - 1, -1, -1):
        if game_map[x][j] == -1:
            return False
        elif game_map[x][j] == 0:
            pass
        elif game_map[x][j] == 1:
            return 1
        else:
            return game_map[x][j]
def someone_right(x, y, game_map):
    width = len(game_map)
    for j in range(x + 1, width):
        if game_map[j][y] == -1:
            return False
        elif game_map[j][y] == 0:
            pass
        elif game_map[j][y] == 1:
            return 1
        else:
            return game_map[j][y]
def someone_left(x, y, game_map):
    width = len(game_map)
    for j in range(x -1, -1, -1):
        if game_map[j][y] == -1:
            return False
        elif game_map[j][y] == 0:
            pass
        elif game_map[j][y] == 1:
            return 1
        else:
            return game_map[j][y]

def make_choice(x,y,game_map):
    width = len(game_map)
    height = len(game_map[0])
    actions = []

    me = game_map[x][y]
    up-1 = someone_up(x, y, game_map)
    down-1 = someone_down(x, y, game_map)
    left-1 = someone_left(x, y, game_map)
    right-1 = someone_right(x, y, game_map)y

    if up_1:
        if up_1 == 1:
            return 'go_up'
        
    if down_1:
        if down_1 == 1:
            return 'go_down'
        
    if left_1:
        if left_1 == 1:
            return 'go_left'
        
    if right_1:
        if right_1 == 1:
            return 'go_right'
       
    if y != 0 and game_map[x][y-1] != -1:
        actions.append('go_up')
    if y != height -1 and game_map[x][y+1] != -1:
        actions.append('go_down')
    if x != 0 and game_map[x-1][y] != -1:
        actions.append('go_left')
    if x != width -1 and game_map [x+1][y] != -1:
         actions.append('go_right')
    return random.choice(actions)

mainloop()
