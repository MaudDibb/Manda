# Manda
SPA designed for one thing only: dot mandalas

![Manda image](https://i.imgur.com/7zn0OWT.png)

# So what is a dot mandala?
google the phrase 'dot mandala' and look at the image/video results. Its a beautiful art form, and it can be done pretty easily with a little bit of paint and some simple tools. There are many tutorials, with different styles and tools used. 

# So why use this app?
Originally my intent was to start doing these mandalas myself, getting the paints, tools, etc. But I like to see what I'm about to do beforehand, so this little app is the result. It lets me quickly mock up the piece I want to do, then I can try it for real.

I'm also pretty handy with javascript and graphics, so getting this page going was not a difficult task. The app itself is pretty simple,
it uses basic math and a bit of code to make it very easy to design your own mandalas. The radial tools make it a breeze to set up the symmetries in your artwork, and everything is saved locally within your browser.

# how to get it on your machine
just grab the html file. all code is included, you dont need a server to run this. You do need a latest version of chrome, the javascript uses features only found in Chrome. I will make it work in Edge and other browsers, but for now...get Chrome ;) 

# where are the projects stored?
Since its a SPA (single page app) there is no server backend. Everything happens locally on your machine. When you use the Save button, the mandala is stored as a text string in localStorage. This means you have roughly 5 megabytes of storage. The mandalas themselves are stored in a pretty compact format (json, but heavily stripped down). a moderately detailed mandala would take maybe 25k to 100k of storage. The alternative is to use the PNG button, which will give you an image file of the mandala you created. With this method you can create many mandalas...but you wont be able to store them for editing later. I'm looking into IndexDB which would allow much more storage.

# what are all those controls...so many of them
I tried to make this as functional as possible for anyone trying their hand at a dot mandala. The basics of it is:
- radial symmetry. when enabled, instead of one dot displayed, you will see several. They all revolve around the center of the mandala (this can be changed, keep reading). The number of dots you see can be altered with:
- number of radials. This defines how many radial lines (and dots) you will see around the center. if its set to 4, you will see 4 dots, each 90 degrees apart from each other. set to 8, youll get 8, 45 degrees apart. etc. when the focus is on this box, you can use the mousehweel to quickly adjust the value.
- radial offset. This lets you adjust where the radials start around the circle. By default its 0 (north) but you can change this value to move the radial lines. several quick keys are defined that set this to 0, 1/4, 1/2 and 3/4 offset between radials. This control also works with mousewheel, in .25 degree increments
- radial mirroring. When enabled, this will create a 'reflection' of the dots around the radial lines. This is VERY handy when doing flower petal type designs.
- snap to radials. When enabled, the cursor will snap to the radial lines, allowing precise positioning when putting down your shapes.
- color picker. This is the color area on the top of the toolbox where you pick hue,saturation and luminance of a color. Clicking in the circle or box will set the color you want. There are keys that allow you to tweak the colors as you go. 
- zoom and pan. The mousewheel is rigged to zoom, ctrl + left mouse button will trigger panning
- adjust dot size. Shift + mousewheel will adjust the dot size
- color dropper. Shift + left mouse button will grab the color under the cursor
- change center of radials. enter key over a dot will set the center of the radials to that dot

# cant edit current shapes?
No...working on that part ;)

# somethings missing/doesnt work
This is still a work in progress. bear with me. I released it so you all can play with it, and maybe you can help me with other browsers (i dont have safari for example)

# is it free?
yes. but donations would be highly appreciated if you have a big heart. Whatever you think is fair ;)

# can i use x in my own project?
sure. just kindly mention me somewhere. If you charge for it...well. All i can say is remember me ;)

# doesnt work in edge
yep i know. Theres quite a few things in the code base that edge does not like (named capture groups in a regular expression for one...bad microsoft!). I work exclusively with chrome. for now, just use chrome.

# phone/tablet?
Id love to see this work on a mobile device. I unfortunately have little experience working with touchscreens and because of all the keyboard shortcuts...id have to redesign the entire UI for it. It weighs heavily on my thoughts tho, I will adress mobile use in the near future

# you could have done x differently/your indentation sucks/oh no you didnt!
I know it could have been done differently. I did not design this for a code review, this was more of a 'what if' project. I know there are people in the FP camp who would scream at me for some of the hacks im using in my code. I know theres blatant abuse of prototypes. *I KNOW THIS CODE IS NOT PERFECT AND IT WILL SET OFF OCD ON MILLIONS OF CODERS AROUND THE WORLD*. Deal with it ;) This is not for a company, a business with defined code practices, etc. If there is something you can contribute that can improve the app in anyway, I promise I will listen.

# nuff sed
make some awesome art!
