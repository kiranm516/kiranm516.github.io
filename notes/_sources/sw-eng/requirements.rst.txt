============
Requirements
============

User Stories
============

1. Role-Goal-Benefit
   
   * Role: Describle a specific role
   * Goal: An achievable goal
   * Benefit: The value that the goal might hold
   * Role can be non-human entities

2. Limitations
3. Definition of Done
4. Engineering Tasks
5. Effort Estimate

   * Should be within an iteration e.g., 2 weeks in Scrum

Easily verifiable so the client knows what the expect, and the person fulfilling the user story can be validated that they've completed the task.

As clear as possible, without ambiguities

**INVEST**

- I - Independence

  - All user stories should be independent of each other

* N - Negotiable
* V - Valueable
* E - Estimable
* S - Small
* T - Testability

Consider the following value statement in the context of a user story for developing a data analysis system:

'As a quantitative researcher, I want to be able to calculate the correlation between two variables, so that I can determine how correlated these variables are.'

Which INVEST guideline is most violated by this user story?

* Independent
* Negotiable
* Valuable correct
* Estimable
* Small
* Testable

The benefit in this value statement is simply repeating the goal, and therefore violates the principle of a user story being *Valuable*. A better value statement would have included the benefit of determining correlation between two variables

Example
-------
Use case: As a prof. I want to create repositories so students can work

Role - Prof
Goal - Create repositories
Benefit - Students can work

Limitations: Need: Repo names, student id's
Definition of done:

    * Runnable as single command
    * Automated test cases
    * Programmatically verifiable

Engineering notes:
    * Should use GitHubManager class
Cost estimate:
    * 1.5 units/days

Decomposing User Stories
------------------------

Role: Player
Goal: Move Mario
Benefit: Dodge/Attack the enemy

Limitations: Keyboard input
Notes: Use existing Level class
Cost: 3

    * +1 - Key Control
    * +1 - Handling movement
    * +1 - Handling collissions

DOD:

    * Key input controls mario's movement
    * Mario is able to move through the level
    * When mario colides enemey, one of them should be hit

I: Independent  - NO
N: Negotiable   - YES
V: Valuable     - YES
E: Estimable    - YES
S: Small        - NO
T: Testable     - YES

1. Find entities that can be decompose
2. Link the entities decomposed
3. Find the actions involved; bind actions
4. Prototype
5. Formalize; like UML
6. Start implementation

Entities can be found in Defintion of Done
    Key, Mario, Level, Enemies
Both mario and enimies are both figures
    Key
    Level
    Figure
    Mario
    Enemy
