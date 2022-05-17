numero = 0

def on_forever():
    global numero
    if input.button_is_pressed(Button.A):
        basic.show_number(input.temperature())
        if input.temperature() > 10 and input.temperature() < 18:
            basic.show_string("Watering the plant")
    if input.button_is_pressed(Button.B):
        numero = randint(0, 100)
        basic.show_number(numero)
        if numero < 60:
            basic.show_string("Watering the plant")
        elif numero > 70:
            basic.show_string("Stopped watering the plant")
    if input.logo_is_pressed():
        basic.show_number(input.light_level())
        if input.light_level() > 120:
            def on_gesture_shake():
                n = 5
                while(n > 0):
                        for i in range(5):
                            for j in range(5):
                                    led.plot(i, j)
                        basic.pause(200)
                        basic.clear_screen()
                        basic.pause(200)
                        for i in range(5):
                                for j in range(5):
                                    led.plot(i, j)
                        n = n-1
            input.on_gesture(Gesture.SHAKE, on_gesture_shake)
        if input.light_level() < 120:
            print("Stopped watering the plant")
basic.forever(on_forever)
