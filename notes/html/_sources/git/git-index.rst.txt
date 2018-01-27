===
Git
===

Deleting all previous commits in Git [001]_
===========================================
Deleting the .git folder may cause problems in your git repository. If you want to delete all your commit history but keep the code in its current state, it is very safe to do it as in the following:

.. code:: batch

	git checkout --orphan latest_branch
	# Add all the files
	git add -A
	Commit the changes
	git commit -am "commit message"
	Delete the branch
	git branch -D master
	Rename the current branch to master
	git branch -m master
	Finally, force update your repository
	git push -f origin master
	PS: this will not keep your old commit history around


Rename local and remote branch [002]_
=====================================

.. code:: batch

  # Rename the branch locally
  git branch -m old-name new-name

  # Delete the old-name remote branch and push the new-name local branch
  git push origin :old-name new-name

  # Reset the upstream branch for the new-name local branch
  git checkout new-name
  git push origin -u new-name


.. [001] https://stackoverflow.com/questions/13716658/how-to-delete-all-commit-history-in-github
.. [002] https://multiplestates.wordpress.com/2015/02/05/rename-a-local-and-remote-branch-in-git