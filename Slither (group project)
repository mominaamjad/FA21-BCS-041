import turtle
from turtle import *
import random
from freegames import square, vector

# screen
turtle.Screen().bgcolor("#293241")
turtle.title("SLITHER")
turtle.setup(width=600, height=600)

# score
pen = turtle.Turtle()
pen.speed(0)
pen.color('white')
pen.penup()
pen.hideturtle()
pen.goto(0, 260)
pen.write("SCORE: 0", align='center', font=('Courier', 24, 'normal'))

# variables
food = vector(0, 0)  # starting point of food
snake = [vector(15, 0)]  # starting point of snake (list)
aim = vector(15, 0)  # starting direction in which the snake moves

# boundary
area = turtle.Turtle()
area.speed(0)
area.penup()
area.hideturtle()
area.goto(-295, -255)

area.fillcolor('#C3DBE9')
area.begin_fill()
area.forward(585)
area.left(90)
area.forward(510)
area.left(90)
area.forward(585)
area.left(90)
area.forward(510)
area.left(90)
area.end_fill()


def boundary(head):
    # Return True if head inside boundaries
    return -295 <= head.x < 285 and -270 < head.y < 255


def move():
    # Move snake forward one segment
    head = snake[-1].copy()  # makes copies of existing list
    head.move(aim)
    if not boundary(head) or head in snake: # out condition
        square(head.x, head.y, 15, 'grey')
        #update()
        go = turtle.Turtle()
        go.speed(0)
        go.color('black')
        go.penup()
        go.hideturtle()
        go.goto(0, -15)
        go.write("GAME OVER", align='center', font=('arial', 35, 'bold'))

        return
    snake.append(head)
    score = len(snake)
    if head == food:
        pen.clear()
        pen.write("SCORE: {}".format(score), align='center', font=('Courier', 24, 'normal'))
        food.x = random.randint(-16, 16) * 15
        food.y = random.randint(-16, 16) * 15
    else:
        snake.pop(0)
    clear()
    for body in snake:
        square(body.x, body.y, 15, '#293241')
    square(food.x, food.y, 15, '#EE6C4D')

    ontimer(move, 100)  # controls speed of move function
    listen()  # connects keypress to a function
    onkey(lambda: direction(15, 0), 'Right')
    onkey(lambda: direction(-15, 0), 'Left')
    onkey(lambda: direction(0, 15), 'Up')
    onkey(lambda: direction(0, -15), 'Down')


def direction(x, y):
    # Change snake direction
    aim.x = x
    aim.y = y


# watermark
watermark = turtle.Turtle()
watermark.speed(0)
watermark.color('white')
watermark.penup()
watermark.hideturtle()
watermark.goto(0, -290)
watermark.write("FA21-BCS-027    FA21-BCS-041 ", align='center', font=('Courier', 10, 'normal'))

hideturtle()
tracer(0)
move()
mainloop()
