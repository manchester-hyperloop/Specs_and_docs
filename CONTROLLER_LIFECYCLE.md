# Controller Lifecycle
The svg diagram shows the difference stages in the "lifecycle" of the system 
controller, namely its initialisation, normal operation (via the FSM), and 
finalisation (leading to shutdown).

## Initialisation
This stage includes initialising core components such as the CAN bus, inertial 
measurement unit, motor drivers.

## FSM
The FSM controls the behaviour of the system through the 4 different active 
states and the 1 error state. When it is entered, it starts off in the Idle 
state (unless a different state is specified) and progresses to the different 
states according to set rules.

### Idle
The default state, encapsulates behaviour at a "station" where the pod is 
idling and waiting for passengers or otherwise not moving along the track.

### Accelerating
Encapsulates behaviour during acceleration to a new speed, transitioning after 
the speed is reached.

### Steady
Encapsulates behaviour during movement along the track at a fixed speed.

### Decelerating
Encapsulates behaviour during deceleration to a new speed, transitioning after 
the speed is reached.

### Panic
Global panic state encapsulating an unrecoverable exception. Should exit out of 
the FSM.

## Finalisation
This stage finalizes any core components that need to be finalised.
