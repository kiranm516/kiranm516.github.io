======
Gradle
======

Notes based on Udacity Gradle course

Quite mode
----------

.. code:: groovy

    gradle -q

Runs gradle in quite mode so only error messages are shown

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
