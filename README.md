import turtle
import random

# Initialize turtle
t = turtle.Turtle()
t.speed(1)  # Fastest speed
turtle.bgcolor("white")  # Set background color

# Function to draw a filled circle
def filled_circle(radius, color="white"):
    t.color(color)
    t.begin_fill()
    t.circle(radius)
    t.end_fill()

# Function to draw a square
def draw_square(length, fill_color):
    t.color(fill_color)
    t.begin_fill()
    for _ in range(4):
        t.forward(length)
        t.left(90)
    t.end_fill()

# Function to draw cloud
def cloud(x, y):
    t.penup()
    t.goto(x, y)
    t.pendown()
    filled_circle(15, "cyan")
    t.penup()
    t.goto(x + 20, y)
    t.pendown()
    filled_circle(20, "cyan")
    t.penup()
    t.goto(x + 40, y)
    t.pendown()
    filled_circle(15, "cyan")

# # Function to draw a flower with stem and leaves
def draw_flower(x, y):
    # Draw the flower
    t.penup()
    t.goto(x, y)
    t.pendown()
    t.color("red")
    t.begin_fill()
    t.circle(10)
    t.end_fill()

    # Draw the stem
    t.penup()
    t.goto(x, y-10)
    t.pendown()
    t.color("green")
    t.setheading(-90)  # Point to the bottom - 90 degrees
    t.forward(40)
    
    # Draw the leaves at the end of the stem
    t.up()
    t.goto(x+5, y-15)
    t.down()
    t.begin_fill()
    t.circle(10, steps=3)
    t.end_fill()

    t.up()
    t.goto(x-15, y-15)
    t.down()
    t.begin_fill()
    t.circle(10, steps=3)
    t.end_fill()

# Draw base of the house
t.penup()
t.goto(-100, -100)
t.pendown()
draw_square(200, "blue")

# Draw roof of the house
t.penup()
t.goto(-100, 100)
t.pendown()
t.color("magenta")
t.begin_fill()
for _ in range(3):
    t.forward(200)
    t.left(120)
t.end_fill()

# Draw the first window
t.penup()
t.goto(-80, 40)
t.pendown()
draw_square(40, "light green")

# Draw the second window
t.penup()
t.goto(40, 40)
t.pendown()
draw_square(40, "light green")

# Draw the door
t.penup()
t.goto(-40, -100)
t.pendown()
draw_square(80, "orange")

# Draw the tree trunk
t.penup()
t.goto(160, -100)
t.pendown()
draw_square(40, "brown")

# Draw tree leaves
t.penup()
t.goto(140, -60)
t.pendown()
t.color("green")
t.begin_fill()
for _ in range(3):
    t.forward(80)
    t.left(120)
t.end_fill()

# Draw flowers on the left side of the house in 3 rows
flower_coordinates = [
    (-160, -100), (-180, -90), (-200, -80),
    (-160, -70),  (-180, -60), (-200, -50),
    (-160, -40),  (-180, -30), (-200, -20)
]
for x, y in flower_coordinates:
    draw_flower(x, y)
  
# Draw three clouds above the house
cloud(-120, 150)
cloud(0, 180)
cloud(120, 150)

# Hide the turtle and show the drawing
t.hideturtle()
turtle.done()
