import play

play.set_backdrop("black")

spaceship = play.new_image(image = "space.jpg", size = 30, x = 0, y = -200)
asteroid1 = play.new_image(image = "aster.jpg", size = 20, x = 0, y = -100)
asteroid2 = play.new_image(image = "aster1.jpg", size = 20, x = 0, y = 0)
asteroid3 = play.new_image(image = "aster2.jpg", size = 20, x = 0, y = 180)
loze = play.new_text(words = "YOU LOZE!", x = 0, y = 0, font_size = 100, color = "red")
win = play.new_text(words = "YOU WIN!", x = 0, y = 0, font_size = 100, color = "green")
finish = play.new_text(words = "FINISH", x = 0, y = 200, font_size = 100, color = "white")
asteroid = play.new_circle(x = -150, y = 0, radius = 40, color = "white")


#--------------------------------------------
@play.when_program_starts
def start():
  asteroid.start_physics(stable = False, x_speed = 20, y_speed = 0, obeys_gravity = False, bounciness = 1, mass = 1)
  asteroid1.start_physics(stable = False, x_speed = 20, y_speed = 0, obeys_gravity = False, bounciness = 1, mass = 1)
  asteroid2.start_physics(stable = False, x_speed = 20, y_speed = 0, obeys_gravity = False, bounciness = 1, mass = 1)
  asteroid3.start_physics(stable = False, x_speed = 20, y_speed = 0, obeys_gravity = False, bounciness = 1, mass = 1)
  spaceship.start_physics(stable = True, obeys_gravity = False, bounciness = 1, mass = 10)

  spaceship.show()
  win.hide()
  loze.hide()

@play.repeat_forever
def do():
  spaceship.physics.y_speed = 0
  spaceship.physics.x_speed = 0

  if play.key_is_pressed('w'):
    spaceship.physics.y_speed = 10
  if play.key_is_pressed('s'):
    spaceship.physics.y_speed = -10
  if play.key_is_pressed('d'):
    spaceship.physics.x_speed = 10
  if play.key_is_pressed('a'):
    spaceship.physics.x_speed = -10

  if spaceship.is_touching(asteroid):
    loze.show()
    spaceship.hide()
    asteroid.hide()
    asteroid1.hide()
    asteroid2.hide()
    asteroid3.hide()
    win.hide()
    finish.hide()

  if spaceship.is_touching(asteroid1):
    loze.show()
    spaceship.hide()
    asteroid.hide()
    asteroid1.hide()
    asteroid2.hide()
    asteroid3.hide()
    win.hide()
    finish.hide()

  if spaceship.is_touching(asteroid2):
    loze.show()
    spaceship.hide()
    asteroid.hide()
    asteroid1.hide()
    asteroid2.hide()
    asteroid3.hide()
    win.hide()
    finish.hide()

  if spaceship.is_touching(asteroid3):
    loze.show()
    spaceship.hide()
    asteroid.hide()
    asteroid1.hide()
    asteroid2.hide()
    asteroid3.hide()
    win.hide()
    finish.hide()  

  if spaceship.is_touching(finish):
    loze.hide()
    spaceship.hide()
    asteroid.hide()
    asteroid1.hide()
    asteroid2.hide()
    asteroid3.hide()
    win.show()
    finish.hide()

play.start_program()
