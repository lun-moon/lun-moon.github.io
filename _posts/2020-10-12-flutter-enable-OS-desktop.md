#turns out flutter is already out for windows macos linux
<https://flutter.dev/desktop>

Funny little issue here as of today is that setting the window title on desktop currently seems to require a plugin... to do it right.
<https://github.com/flutter/flutter/issues/30712#issuecomment-580484713>

There is a hack just to edit a .cc file to change the title, do not know if this breaks something somewhere else.  
`vim ~/your_project_directory/linux/my_application.cc`  
edit the line below:  
`gtk_header_bar_set_title(header_bar, "your_title_here");`

Window title is not a big deal as having the three major OS's apparently already supported for real functionality is great.
snap install for linux is easy too (do not be scared by the number of dependencies if installing via snap)
