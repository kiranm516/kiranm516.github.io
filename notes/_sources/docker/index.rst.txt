======
Docker
======

Space Usage [001]_
------------------

.. code:: batch

   docker system df


Save docker image [002]_
------------------------

.. code:: batch

   # pull the image
   docker pull ubuntu

   # save the image to a file
   docker save -o ubuntu_image.docker ubuntu

   # load the image from file
   docker load ubuntu_image.docker

Change VHD location [003]_
--------------------------

Docker | Settings | Advanced | Change VHD Location

Note: The selected directory should be empty. Docker will move the image

Start bash from running container [004]_
----------------------------------------

docker exec [OPTIONS] CONTAINER COMMAND [ARG...] [flags]

e.g., docker exec -it oracle /bin/bash

-i - Interactive
-t - Pusedo TTY
oracle - Container name
/bin/bash - Command to be executed

Commit
------

Usage:  docker commit [OPTIONS] CONTAINER [REPOSITORY[:TAG]]

Create a new image from a container's changes

Options:
  -a, --author string    Author (e.g., "John Hannibal Smith
                         <hannibal@a-team.com>")
  -c, --change list      Apply Dockerfile instruction to the created image
  -m, --message string   Commit message
  -p, --pause            Pause container during commit (default true)

Check these links
-----------------

https://www.digitalocean.com/community/tutorials/how-to-remove-docker-images-containers-and-volumes
https://stackoverflow.com/questions/17665283/how-does-one-remove-an-image-in-docker
https://store.docker.com/profiles/kiranm516/content/sub-e2395a92-3d01-49bd-b79d-7ec6713c0113

.. [001] https://stackoverflow.com/questions/26753087/docker-how-to-analyze-a-containers-disk-usage
.. [002] https://serverfault.com/questions/701248/downloading-docker-image-for-transfer-to-non-internet-connected-machine
.. [003] https://stackoverflow.com/questions/42369522/docker-wont-change-vhd-location?rq=1
.. [004] https://blog.codeship.com/using-docker-commit-to-create-and-change-an-image/