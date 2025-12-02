To fork this Git repo and publish your own Home Assistant Add-on Repository:

* Fork this Git repo in GitHub.
* In the forked repo in GitHub, go to "Actions", then click
  "I understand my workflows, go ahead and enable them".
* Click the "Update" workflow on the left, then click "Run workflow" on the right, then click
  "Run workflow".
  (This will update the configs/docs/etc as needed to reference your fork of the Git repo, then
  commit those changes.)
* Click the "Build" workflow on the left, then click "Run workflow" on the right, then click
  "Run workflow".
  (This will perform an initial build of the Add-on.  The Add-on should work even if you skip this,
  but in that case, installing the Add-on in HA will cause the build to be performed on your HA
  system instead of on GitHub.)

After the initial steps above, the "Update" workflow should run automatically (on a schedule) to
incorporate new upstream updates, and the "Build" workflow should run automatically (on push/merge
to the 'main' branch, if an Add-on's "version" has changed) to build new versions.

To change an Add-on's "version" after making changes or merging a Pull Request, you should either
run the "Release" workflow, or run `<addon>/update --release` in a shell.  (You should not manually
update the version number.)  This will then trigger the "Build" workflow, which will finish building
and releasing the new version.
