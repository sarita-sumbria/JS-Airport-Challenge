# JS-Airport-Challenge

Task:

We have a request from a client to write the software to control the flow of planes at an airport. The planes can land and take off provided that the weather is sunny. Occasionally it may be stormy, in which case no planes can land or take off. Here are the user stories that we worked out in collaboration with the client:

As an air traffic controller
So I can get passengers to a destination
I want to instruct a plane to land at an airport

As an air traffic controller
So I can get passengers on the way to their destination
I want to instruct a plane to take off from an airport and confirm that it is no longer in the airport

As an air traffic controller
To ensure safety
I want to prevent landing when the airport is full

As the system designer
So that the software can be used for many different airports
I would like a default airport capacity that can be overridden as appropriate

As an air traffic controller
To ensure safety
I want to prevent takeoff when weather is stormy

As an air traffic controller
To ensure safety
I want to prevent landing when weather is stormy


Stories Completed
------------------

1st user story:

As an air traffic controller
So I can get passengers to a destination
I want to instruct a plane to land at an airport


Converting user story into domain model

nouns: traffic controller or user, passengers, plane, airport
verbs: instruct, land

| Objects         | Messages            |    
| ----------------:-------------------- |
| user            |                     |
| plane           | instruction to land |
| airport         | landing                |


user <-> plane <-> airport <-> user

Steps taken:
1) Created a failing feature test in spec/featureSpec.js
 Error: Plane is not defined

 2) Created a unit test for Plane class in spec/planeSpec.js
 Same error as feature test

 3) Created a Plane class in src/plane.js
 Error: planes can be expected to land at an airport

 ReferenceError: Airport is not defined
 TypeError: plane.land is not a function

 Plane can land at an airport
 Error: Expected undefined not to be undefined.

 4) Added a land method to the Plane class.
 Still have a failing feature test

 5) created a unit test for Airport class in spec/airportSpec.js

 6) created a Airport class in src/airport.js
 still failing the test

 7) Added planes method to the Airport class.
 New error for feature test: Expected [  ] to contain Plane({  }).

 8)  plane object needs to interact with airport object.
 Interaction is stubbed in the plane unit test.

 * New thing learned that 'spys' are Jasmine's equivalent of 'doubles'.  

 New Error: Expected spy airport.clearForLanding to have been called with:
  [ Plane({  }) ]
but it was never called.

9) plane class is updated with airport clearForLanding method.
TypeError: airport.clearForLanding is not a function

10) defined clearForLanding function in Airport class

11) 'Spy' is used in the airport unit test

12) Airport class updated with the following constructor function.

```
constructor() {
  this._hangar = []
}
```

Result: First user story Completed (All tests passing).


2st user story:

As an air traffic controller
So I can get passengers on the way to their destination
I want to instruct a plane to take off from an airport and confirm that it is no longer in the airport

Steps taken:

1) Added a feature test for plane takeoff.
TypeError: plane.takeoff is not a function

2) Created a unit test for plane takeoff function.
Both feature test and unit test are failing.

3) Updated the Plane class with the following function.

```
constructor() {
      this.__location;
    }
```
```
TypeError: this._location.clearForTakeOff is not a function
```

4) Added a unit test for takeoff function in spec/airportSpec.js and spec/planeSpec.js

5) Updated the code in airport.js and plane.js files to pass the tests.

Result: All tests are passing. 2nd user story completed.
