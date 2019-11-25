# Manda
SPA designed for one thing only: dot mandalas

![Manda image](https://i.imgur.com/7zn0OWT.png)

the url/domain name in the image above is *NOT* real. I repeat: manda.com is not mine. It is me using a fake host name on a loopback ip address on my local machine for testing. If you must know the details:

- edit hosts file on your windows box and add \<fake domain name here\>.com 127.0.0.2
- ipconfig /flush
- get nodejs, then get http-server package
- run http-server <root dir of files you want server to run from> -a 127.0.0.2 -p 80 -c-1
- load browser, go to your new domain name/index.html (http server will not auto map / to index.html)

the 2 on the ip is not a typo. you can do this for as many local domains you want to run on your box. I do this a lot to get around the localhost or file:// domain restrictions you get with certain operations in browsers, and it lets you use localStorage/indexedDB without mixing it up with other things you develop on your machine.

\<tl;dr\>stop asking about manda.com ;)

# So what is a dot mandala?
google the phrase 'dot mandala' and look at the image/video results. Its a beautiful art form, and it can be done pretty easily with a little bit of paint and some simple tools. You will see many dot mandala paintings on rocks, canvas, etc. The really impressive ones are the indian wedding mandalas...so much detail. There are many tutorials showing you how they are done, with different styles, paints and tools used.

# So why use this app?
Originally my intent was to start doing these mandalas myself, getting the paints, tools, etc. But I like to see what I'm about to do beforehand, so this little app is the result. It lets me quickly mock up the piece I want to do, then I can try it for real.

I'm also pretty handy with javascript and graphics, so getting this page going was not a difficult task. The app itself is pretty simple, it uses basic math and a bit of code to make it very easy to design your own mandalas. The radial tools make it a breeze to set up the symmetries in your artwork, and everything is saved locally on your machine. A server is not required to run this, you can run it directly in your browser from disk.

# how to get it on your machine
just grab the html file. All the code is in one file, index.html. You don't need a server to run this. Tested to work fine in latest Chrome, Edge and Opera desktop browsers. Im on windows 10, so linux/macOS support will be severely limited ;) No mobile support yet, stay tuned!

# where are the projects stored?
Since this is a SPA (single page app) there is no server backend. Everything happens locally on your machine. When you use the Save button, the mandala is stored in a database on your machine. The mandalas themselves are stored in a pretty compact format (js objects, but heavily stripped down). a moderately detailed mandala would take maybe 25k to 100k of storage. The alternative is to use the PNG button, which will give you an image file of the mandala you created. With this method you can create many mandalas...but you wont be able to store them for editing later. UPDATE: just converted over to indexedDB. Should allow much more space, will have to look at quota api to see where things are in terms of storage limits

# what are all those controls...
I tried to make this as functional as possible for anyone trying their hand at a dot mandala. They are:
- radial symmetry. when enabled, instead of one dot displayed at the cursor, you will see several. They all revolve around the center of the mandala (the center can be changed, keep reading). The number of dots you see can be altered with:
- number of radials. This defines how many radial lines (and dots) you will see around the center. if its set to 4, you will see 4 dots, each 90 degrees apart from each other. set to 8, you'll get 8, 45 degrees apart. etc. when the focus is on this box, you can use the mousehweel to quickly adjust the value.
- radial offset. This lets you adjust where the radials start around the circle. By default its 0 but you can change this value to move the radial lines. several quick keys are defined that set this to 0, 1/4, 1/2 and 3/4 angle between radials. This control also works with mousewheel, in .25 degree increments
- radial mirroring. When enabled, this will create a 'reflection' of the dots around the radial lines. This is VERY handy when doing flower petal designs.
- snap to radials. When enabled, the cursor will snap to the radial lines, allowing precise positioning when putting down your shapes.
- color picker. This is the color area on the top of the toolbox where you pick hue,saturation and luminance of a color. Clicking in the circle or box will set the color you want. There arow keys and \[,\] keys allow you to tweak the colors as you go. Shift + those keys will give you larger adjustments 
- zoom and pan. Mousewheel to zoom, ctrl + left mouse button/drag will pan the image
- adjust dot size. Shift + mousewheel will adjust the dot size
- color dropper. Shift + left mouse button will grab the color under the cursor
- change center of radials. enter key over a dot will set the center of the radials to that dot
- new. this will clear the current session
- gallery. this opens up a popup that will display small thumbnails of your previous creations that were saved in local storage. Clicking on any of these will load it in.
- png. this will create a static image of your current mandala session, and start a download
- save. this stores the current session into localstorage

# how is it so fast?
Im using a clever trick where the current set is rendered into an offscreen canvas (not using offscreen api, just noticed that) and copying that into the onscreen canvas on refresh. The cursor and radial lines are the only things drawn in realtime.

# cant edit/undo/delete existing shapes!
Not yet...working on that part ;)

# things are missing/doesnt work
This is still a work in progress. bear with me. Consider it an alpha version. I released it so you all can play with it, and maybe you can help me with other browsers (i dont have safari for example)

# is it free?
Yes. but donations would be highly appreciated if you have a big heart. Whatever you think is fair would be appreciated ;)

# can i use \<insert x here\> in my own project?
sure. just kindly mention me somewhere. If you charge for it... All i can say is remember me, I like money too ;)

# doesnt work in \<insert browser name\> on \<insert OS here\>
Edge, Opera and Chrome for windows 10 desktop are the only browsers I have to test with (which is like, almost everybody. RIGHT?). I could use a hand with other Os/browsers out there ;) dont say IE. I hate IE. seriously.

# phone/tablet?
I would love to see this work on a mobile device. I have little experience working with touchscreens and because of all the keyboard shortcuts, I would have to redesign the entire UI for it. It weighs heavily on my thoughts tho, I will adress mobile use in the near future!

# you could have done x differently/your indentation sucks/oh no you didnt!
I know it could have been done differently. I did not design this for a code review, this was more of a 'what if', a toy project. I know there are people in the FP camp who would scream at me for some of the hacks im using in my code. I know theres blatant abuse of prototypes. I know theres copy-pasta/spaghetti monsters in the code. *I KNOW THIS CODE IS NOT PERFECT AND IT WILL SET OFF OCD ON MILLIONS OF CODERS AROUND THE WORLD*. Not my problem, deal with it ;) Im doing this for fun anyway. If there is something you can contribute that can improve the app in anyway, I promise I will listen.

# nuff sed
make some awesome art!

# TODO
- touchscreen events would be nice, that might end up being a seperate project
- editing of current session objects...right now its add only, no delete/undo/edit
- svg support? not hard to do.
- perhaps an online gallery for people to show off their creations? I have the github.io page started, but not sure how i can store all that data. otherwise ill have to fork up something for a domain
- names on thumbnails in gallery
- color palette?
- any other ideas? let me know.

# SVG?
I'm really curious how this would behave with an SVG renderer instead of canvas. I did canvas originally for performance, but you can definitely see aliasing artifacts when zoomed in. SVG should look good no matter what zoom level you are at. The only thing stopping me is how well it would perform when there are many objects on the screen. Ill do a test version later that does SVG and see how it goes

# update 11/25/2019
just commited a huge change in the handling of the shape format. The way things were done before, everytime you clicked the mouse it would store a new array of dots, storing each dots coordinates individually, along with size and color. Now, the format specifies just size,color,count,radial offset,angle,distance from center and center coordinates, for an entire set of dots. This sounds more complicated, but actually it is less because imagine storing an array of dots with 32 radials, mirrored, which would be 64 pairs of x/y coordinates, versus the one object that describes the 64 dots. This will make the format much more compact, especially in the pack/unpack functions when storing the session into indexedDB. Had to factor code to handle the new shape format, which helped make the code a bit more readable. This also lets me go back later and edit the shapes after they were put down. Next update will do just that ;) Also added a bunch of indexedDB support so loading/saving happens from indexDB, not localStorage
