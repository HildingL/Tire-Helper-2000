import time
import board
import digitalio
import analogio
import threading
import rotaryio
import TH2000_display.py as *


encoder = rotaryio.IncrementalEncoder(board.8, board.10)
pressure_sensor = analogio.AnalogIn(board.A0)
Valve_out = digitalio.DigitalInOut(board.16)
Valve_out.direction = digitalio.Direction.OUTPUT
Valve_in = digitalio.DigitalInOut(board.18)
Valve_in.direction = digitalio.Direction.INPUT
target_pressure = 0
precission = 0.1
time_big = 1
time_small = 0.5
can_run = True
override = False


def air(direction, size)
    if direction = fill:
        valve = Valve_in
    else:
        valve = Valve_out
        
    t_big = threading.timer(time_big, valve.value = False)
    t_small = threading.timer(time_small, valve.value = False)
    if size = big AND can_run = True:
        valve.value = True
        t_big.start
    elif can_run = True:
        valve.value = False
        t_small.start
        
while True:
    encoder_position = encoder.position
    encoder_change = encoder_position - last_position 

    target_pressure = last_target_pressure + encoder_change
    pressure = pressure_sensor.value
    if (pressure <  target_pressure * (1 - precission)):
        air(fill, big)
        
    if (pressure > target_pressure * (1 + precission)):
        air(empty, big)
    
    if pressure > 0.2:
        can_run = True
    else:
        can_run = False
    
    percentage = 100 * pressure / target_pressure            
    
    last_position = encoder_position
    last_target_pressure = target_pressure
