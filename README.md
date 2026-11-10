# zmiuka-
prosto zmiuka 
mport pygame
import time
import random

# Швидкість змійки
snake_speed = 15

# Розмір вікна
window_x = 720
window_y = 480

# Визначення кольорів (RGB)
black = pygame.Color(0, 0, 0)
white = pygame.Color(255, 255, 255)
red = pygame.Color(255, 0, 0)
green = pygame.Color(0, 255, 0)

# Ініціалізація pygame
pygame.init()

# Створення вікна гри
pygame.display.set_caption('Класична гра Змійка')
game_window = pygame.display.set_mode((window_x, window_y))

# Контролер кадрів (FPS)
fps = pygame.time.Clock()

# Початкова позиція змійки та її тіло
snake_position = [100, 50]
snake_body = [
    [100, 50],
    [90, 50],
    [80, 50],
    [70, 50]
]

# Позиція їжі
fruit_position = [
    random.randrange(1, (window_x // 10)) * 10,
    random.randrange(1, (window_y // 10)) * 10
]
fruit_spawn = True

# Початковий напрямок руху
direction = 'RIGHT'
change_to = direction

# Початковий рахунок
score = 0

# Функція для виведення рахунку на екран
def show_score(choice, color, font, size):
    score_font = pygame.font.SysFont(font, size)
    score_surface = score_font.render('Рахунок: ' + str(score), True, color)
    score_rect = score_surface.get_rect()
    game_window.blit(score_surface, score_rect)

# Функція завершення гри
def game_over():
    my_font = pygame.font.SysFont('times new roman', 50)
    game_over_surface = my_font.render('Кінець гри! Рахунок: ' + str(score), True, red)
    game_over_rect = game_over_surface.get_rect()
    game_over_rect.midtop = (window_x / 2, window_y / 4)
    game_window.fill(black)
    game_window.blit(game_over_surface, game_over_rect)
    pygame.display.flip()
    time.sleep(3)
    pygame.quit()
    quit()

# Головний цикл гри
while True:
    # Обробка натискань клавіш (стрілочки або W, A, S, D)
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            pygame.quit()
            quit()
        elif event.type == pygame.KEYDOWN:
            if event.key == pygame.K_UP or event.key == pygame.K_w:
                change_to = 'UP'
            if event.key == pygame.K_DOWN or event.key == pygame.K_s:
                change_to = 'DOWN'
            if event.key == pygame.K_LEFT or event.key == pygame.K_a:
                change_to = 'LEFT'
            if event.key == pygame.K_RIGHT or event.key == pygame.K_d:
                change_to = 'RIGHT'

    # Заборона рухатися у протилежний бік миттєво
    if change_to == 'UP' and direction != 'DOWN':
        direction = 'UP'
    if change_to == 'DOWN' and direction != 'UP':
        direction = 'DOWN'
    if change_to == 'LEFT' and direction != 'RIGHT':
        direction = 'LEFT'
    if change_to == 'RIGHT' and direction != 'LEFT':
        direction = 'RIGHT'

    # Рух змійки
    if direction == 'UP':
        snake_position[1] -= 10
    if direction == 'DOWN':
        snake_position[1] += 10
    if direction == 'LEFT':
        snake_position[0] -= 10
    if direction == 'RIGHT':
        snake_position[0] += 10

    # Збільшення змійки при поїданні їжі
    snake_body.insert(0, list(snake_position))
    if snake_position[0] == fruit_position[0] and snake_position[1] == fruit_position[1]:
        score += 10
        fruit_spawn = False
    else:
        snake_body.pop()

    if not fruit_spawn:
        fruit_position = [
            random.randrange(1, (window_x // 10)) * 10,
            random.randrange(1, (window_y // 10)) * 10
        ]
    fruit_spawn = True

    # Очищення екрана
    game_window.fill(black)

    # Малювання змійки
    for pos in snake_body:
        pygame.draw.rect(game_window, green, pygame.Rect(pos[0], pos[1], 10, 10))

    # Малювання їжі
    pygame.draw.rect(game_window, white, pygame.Rect(fruit_position[0], fruit_position[1], 10, 10))

    # Перевірка на вихід за межі екрана
    if snake_position[0] < 0 or snake_position[0] > window_x - 10:
        game_over()
    if snake_position[1] < 0 or snake_position[1] > window_y - 10:
        game_over()

    # Перевірка на зіткнення з власним хвостиком
    for block in snake_body[1:]:
        if snake_position[0] == block[0] and snake_position[1] == block[1]:
            game_over()

    # Оновлення рахунку та екрана
    show_score(1, white, 'times new roman', 20)
    pygame.display.update()
    fps.tick(snake_speed)event.keyevent.typegame_over_rect.midtop010480
72015import pygame
import time
import random

# Швидкість змійки
snake_speed = 15

# Розмір вікна
window_x = 720
window_y = 480

# Визначення кольорів (RGB)
black = pygame.Color(0, 0, 0)
white = pygame.Color(255, 255, 255)
red = pygame.Color(255, 0, 0)
green = pygame.Color(0, 255, 0)

# Ініціалізація pygame
pygame.init()

# Створення вікна гри
pygame.display.set_caption('Класична гра Змійка')
game_window = pygame.display.set_mode((window_x, window_y))

# Контролер кадрів (FPS)
fps = pygame.time.Clock()

# Початкова позиція змійки та її тіло
snake_position = [100, 50]
snake_body = [
    [100, 50],
    [90, 50],
    [80, 50],
    [70, 50]
]

# Позиція їжі
fruit_position = [
    random.randrange(1, (window_x // 10)) * 10,
    random.randrange(1, (window_y // 10)) * 10
]
fruit_spawn = True

# Початковий напрямок руху
direction = 'RIGHT'
change_to = direction

# Початковий рахунок
score = 0

# Функція для виведення рахунку на екран
def show_score(choice, color, font, size):
    score_font = pygame.font.SysFont(font, size)
    score_surface = score_font.render('Рахунок: ' + str(score), True, color)
    score_rect = score_surface.get_rect()
    game_window.blit(score_surface, score_rect)

# Функція завершення гри
def game_over():
    my_font = pygame.font.SysFont('times new roman', 50)
    game_over_surface = my_font.render('Кінець гри! Рахунок: ' + str(score), True, red)
    game_over_rect = game_over_surface.get_rect()
    game_over_rect.midtop = (window_x / 2, window_y / 4)
    game_window.fill(black)
    game_window.blit(game_over_surface, game_over_rect)
    pygame.display.flip()
    time.sleep(3)
    pygame.quit()
    quit()

# Головний цикл гри
while True:
    # Обробка натискань клавіш (стрілочки або W, A, S, D)
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            pygame.quit()
            quit()
        elif event.type == pygame.KEYDOWN:
            if event.key == pygame.K_UP or event.key == pygame.K_w:
                change_to = 'UP'
            if event.key == pygame.K_DOWN or event.key == pygame.K_s:
                change_to = 'DOWN'
            if event.key == pygame.K_LEFT or event.key == pygame.K_a:
                change_to = 'LEFT'
            if event.key == pygame.K_RIGHT or event.key == pygame.K_d:
                change_to = 'RIGHT'

    # Заборона рухатися у протилежний бік миттєво
    if change_to == 'UP' and direction != 'DOWN':
        direction = 'UP'
    if change_to == 'DOWN' and direction != 'UP':
        direction = 'DOWN'
    if change_to == 'LEFT' and direction != 'RIGHT':
        direction = 'LEFT'
    if change_to == 'RIGHT' and direction != 'LEFT':
        direction = 'RIGHT'

    # Рух змійки
    if direction == 'UP':
        snake_position[1] -= 10
    if direction == 'DOWN':
        snake_position[1] += 10
    if direction == 'LEFT':
        snake_position[0] -= 10
    if direction == 'RIGHT':
        snake_position[0] += 10

    # Збільшення змійки при поїданні їжі
    snake_body.insert(0, list(snake_position))
    if snake_position[0] == fruit_position[0] and snake_position[1] == fruit_position[1]:
        score += 10
        fruit_spawn = False
    else:
        snake_body.pop()

    if not fruit_spawn:
        fruit_position = [
            random.randrange(1, (window_x // 10)) * 10,
            random.randrange(1, (window_y // 10)) * 10
        ]
    fruit_spawn = True

    # Очищення екрана
    game_window.fill(black)

    # Малювання змійки
    for pos in snake_body:
        pygame.draw.rect(game_window, green, pygame.Rect(pos[0], pos[1], 10, 10))

    # Малювання їжі
    pygame.draw.rect(game_window, white, pygame.Rect(fruit_position[0], fruit_position[1], 10, 10))

    # Перевірка на вихід за межі екрана
    if snake_position[0] < 0 or snake_position[0] > window_x - 10:
        game_over()
    if snake_position[1] < 0 or snake_position[1] > window_y - 10:
        game_over()

    # Перевірка на зіткнення з власним хвостиком
    for block in snake_body[1:]:
        if snake_position[0] == block[0] and snake_position[1] == block[1]:
            game_over()

    # Оновлення рахунку та екрана
    show_score(1, white, 'times new roman', 20)
    pygame.display.update()
    fps.tick(snake_speed)