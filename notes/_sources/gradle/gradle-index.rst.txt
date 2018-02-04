======
Gradle
======

Notes based on Udacity Gradle course

What is Gradle?
===============

Installing Gradle
=================

Basics Concepts
===============

build.gradle
------------
`build.gradle` is the default build script to be used.
For using another script by specifying `-b` flag with the build file name

Quite mode
----------
.. code:: groovy

    gradle -q

Runs gradle in quite mode so only error messages are shown

Project
-------
Every build script can be think of as for one project. It literaly contains the data for that projects like tasks

Task
====
Task is the central concept to gradle. A project build process have several tasks and it has several other properites

.. code:: groovy

    task hello {
        description "Task description"
        group "Task group name"
        doLast {
            println "Hello, Task!"
        }
    }

dependsOn
---------

e.g.,

.. code:: groovy

    task putOnSocks {
        doLast {
            println "Putting on Socks."
        }
    }

    task putOnShoes {
        dependsOn "putOnSocks"
        doLast {
            println "Putting on Shoes."
        }
    }

finalizedBy
-----------

When run eatBreadkFast afterwards brushYourTeeth task is also run

.. code:: groovy

    task eatBreakFast {
        finalizedBy "brushYourTeeth"
        doLast {
            println "Eating breakfast"
        }
    }

    task brushYourTeeth {
        doLast {
            println "Brushing..."
        }
    }

mustRunAfter
------------
