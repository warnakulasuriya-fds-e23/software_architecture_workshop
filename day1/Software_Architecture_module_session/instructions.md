

- You dont pick a style because its cool (Scalability, Responsiveness, Reliability, Modifiability, Security)

# Meet AgriSense (The target project)

A cooperative platform for thousands of smallholder farms: field sensors feed a dashboard and mobile arlerts, an agornomist runs analytics, and irrigation values can be controlled remotely or automatically- over flaky rural connections.
1. Sense (Soil moistur, temparture, rainfall from field gatewats)
2. Decide (Detect threshold breache:)
3. Act (Alert farmers SMS/push and open close valves)
4. Learn (Store history, agronomist analytics and sensor)

# C4 Diagrams
Zoom Levels 
On a mpa


C4 Level 1 - Context diagram (Agrisense platform block in the middle and other actors like agronomist connect to it and services like weather service connect to it)

C4 Level 2 - Containers ( Data ingestions flow after getting through gateway)


# Part1 - Six Architectural Styles

## [Style 1/6] Pipe & Filter (Data-Flow)
Stage of pipe does its job only, next stage does its job only.
In Agrisense: Raw readings flow through ingest -> validate -> clean -> aggregate -> store. Each filter is indpendent and trivial to add to. Validating reading from senors is advisable , dont process signals from unregistered sensors, anamolous readings, etc. Clean data also. Aggregate values from sensors and  store.

## [Style 2/6] Data cenetered (Repository)
Nobody talks to each other directly.
In Agrisense: All historical readings live in one shared store and the services that need the data will indepenedantly read and process them.

## [Style 3/6] Layered
You cant bypass, each layer calls to the layer behind it to reach the required target
In AgrisenseL

## [Style 4/6] Call & Return (Client-Server)
Call and stays blocked until result is recieved
In Agrisense: A farmer taps 'open valve'. The app calls the control service, waitsm and gets back 'valve opened'

## [Style 5/6] Object-Oriented

In Agrisense: Domain objects - Farm, Senor, Valve each hold their own data.

## [Style 6/6] Event-Driven (Publish/ Subscribe)

In Agrisense: A `soil-too-dry` event is published once. The SMS sender, the push notifier and te audit log each react indepenedantly.


## The Big Reveal
This kinda a rice and curry thing, each pattern is applied in different patterns

### How to chose: Quality attribute -> reach for this style

High throughput oon a stream | Pipe & Filter |
One shred source of truth | Data-Centered |
Modifiablilty & clear roles | Layered |
Simple request -> response | Client-Server |
Rich behaviour | Event Driven |

eg:
Banking core - Layered  strong consistency
A compiler - Pipe & Filter
....

# Part2 -  WHat is inside the boxes(Component Design)

## C4 Level 3- Inside the Alert Engine

## Cohesion - one reason to exisit

## Encapsulation

## Separation of concerns

## Design pattern - use proven pattern

Common Mistakes
- Overpowered objects
- spaghetti patterns
- one stlye fits all assumption


# The Exercics that should be done
## QuickEats 
A city-wide online food-ordering & delivery platform. 

1. C4 Context + Container
2. A style per container
3. Zoom into one box
4. Pick one pattern
