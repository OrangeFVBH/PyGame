import time
import pygame as pg

pg.init()
monitor_surfase = pg.display.Info()
SIZE = WIDTH, HEIGHT = monitor_surfase.current_w, monitor_surfase.current_h
COLOR_SKY = pg.Color('crimson')
COLOR_GROUND = pg.Color((0, 120, 0))
COLOR_SUN = 'yellow'
SUN_RADIUS = 300
SPEED = 0.1
FPS = 60


def darkness(color: pg.Color, light: float) -> pg.Color:
    h, s, l, a = color.hsla
    light = max(0, light)

    new_color = pg.Color(color)
    new_color.hsla = (h, s, int(l * light), a)
    return new_color



screen = pg.display.set_mode(SIZE, pg.FULLSCREEN)
pg.display.set_caption('Закат')
running = True
animation = 0
clock = pg.time.Clock()
while running:
    for event in pg.event.get():
        if event.type == pg.QUIT:
            running = False
    if animation < 1:
        animation += 0.00011
    screen.fill(darkness(COLOR_SKY, 1 - animation))
    sun_y = (HEIGHT / 2 + SUN_RADIUS) * animation
    pg.draw.circle(screen, COLOR_SUN, (WIDTH / 2, sun_y), SUN_RADIUS)
    pg.draw.rect(screen, darkness(COLOR_GROUND, 1 - animation), (0, HEIGHT / 2, WIDTH, HEIGHT / 2))
    pg.display.flip()
    t = clock.tick(FPS)
    if animation < 1:
        animation += SPEED / FPS
