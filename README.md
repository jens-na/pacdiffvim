Overview
==========
<tt>pacdiffvim</tt> is a .pacnew file updater for vim enthusiasts. The shell script locates all .pacnew files
and opens a tab for each configuration file comparision (diff) in vim. Furthermore the script defines a few 
vim functions to operate with a .pacnew diff.

###Dependencies
- Bash 4.x
- Vim 7.x

###Installation
- Download pacdiffvim <tt>wget https://raw.github.com/jens-na/pacdiffvim/master/pacdiffvim</tt>
- Put <tt>pacdiffvim</tt> to <tt>/usr/local/bin</tt>
- <tt>chmod +x /usr/local/bin/pacdiffvim</tt>

Usage
==========
###Command line options
If you start <tt>pacdiffvim</tt> without any parameters, the script tries to locate all .pacnew files with <tt>find</tt>
in the directory <tt>/etc</tt> and starts vim with the found diff candidates. If there is nothing to do the script
will exit with return code 0.

* <tt>-r, --root</tt>    - You can update .pacnew files in another directory if you specify an alternative root 
                           path with <tt>-r</tt> or <tt>--root</tt>. The default directory is <tt>/etc</tt>.
* <tt>-V, --version</tt> - Shows the version and copyright info for <tt>pacvimdiff</tt>.
* <tt>-h, --help</tt>    - Shows the help for the script and exits.

**Environment variables**<br/>
If <tt>$VIMPROG</tt> is specified, the script uses this value to start vim. The default value is 
<tt>vim</tt>. For example if you like to use <tt>gvim</tt> to compare the files you can set <tt>VIMPROG</tt>
to <tt>gvim</tt>. Example: <tt>VIMPROG=gvim pacdiffvim</tt>

###Runtime
<tt>pacdiffvim</tt> starts vim with a few vim commands to deal with the .pacnew diff. 

* <tt>:PacNextDiff</tt>    - the command opens the next available .pacnew diff (if there is any)
* <tt>:PacOK</tt>          - if you have finished the diff between the .pacnew file and the configuration file
                             you should invoke this command. It will delete the corresponding .pacnew file and
                             closes the current diff.
* <tt>:PacExit</tt>        - closes all the vim buffers and vim itsself without saving, deleting, modifying anything.

License and Copyright
=======
Licensed under the GNU General Public License 3.

(C) Jens Nazarenus, 2013
