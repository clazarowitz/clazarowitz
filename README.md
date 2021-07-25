Most of my career has been in extremily closed source environments.  We have used open source tools for our systems, but all of the new code, linked code, etc, has been compliant closed source.

This, unfortunately, means most of the work I've done is not visible to the rest of the world, and since the products have been for obscure markets, you will not have even heard of any of them!  (Unless you happen to be in the exact same sub-segment of the industry!)

I do have some side projects though.  Mostly not programming....I work for 8 hours in code, its not like I want to come home and do the same!  However, I have the skills, so when the need arises, and the interest is strong enough, I can code for personal projects.  Most of the time, I keep these projects *VERY* small, and so they aren't really something to release.  Often enough, I wouldn't dare release :)  Like every other software engineer, my mind goes to code almost immediatly, and not to code design.  This can work for small projects that need no maintinace (Think arduino sketches), but not for much else.  I do have a few serious, ongoing projects, and do want a place to share/collaborate.

Most recently, I have two projects, one that I want to share some code back to another project, and one that isn't quite ready for upload.  The first is automating my lawnmower.  I'm using ardupilot, so its not like I'm writing an autopilot.  However, I am using large stepper motors instead of slow (huge for) hobby servos with massive gear ratios.  Since the autopilot puts out a PWM signal, I have to translate.  That part isn't hard, and hardly worth putting on github, although, I do have a more optimized/higher accuracy version for Atmel chips than what I found onlune (12us worst case ISR time, full 16 bit accuracy, and generally better, so maybe I'll fork the original project there as well....(Put here more as a reminder for myself.)  Unfortunately, the autopilot sends the PWM signals synchronously.  I can detect the start of both pulses on the atmel 2560 with no issue, but if they are just a few microseconds apart in length, the short pulse is measured to within 1 microsecond, the second pulse will have up to about 15 microseconds added to it because of the first ISR call, and the ISR call overhead.  Thats not ideal.  Its a tiny percentage as the hobby servo range is generally about 1000 microseconds, making this a 1.5% error.  For most things, this may be ok, but for a tight control system, its just too big for comfort.  So I switched to an arduino due.

Now where the first contribution comes in.  On the 2560, I was using the FastAccelStepper library, and it was working well with radio control.  The Due, has no FastAccelStepper support, just AVRs and the ESP32.  So I went about porting the library to the Due.  I'm not sure if its perfect yet, but it passes an easy to operate test case.  I plan to see if the original author will accept the code (and probably point out a few misunderstandings inside his code....this was a quick and dirty port where I tried to understand the minimum possible to become functional!)

The second project, which I generally only work on when in airplanes (which hasn't been often as of late), is a binary editor.  Not Hex (although I designed the system from the start....well, almost, I threw away the original non-designed code..., so yeah, from the start to be a framework with plugins.  The RasterView is what I plan to include, and the main reason for writing this, but one could just as easily write a HexView.), but a straight binary raster.  Conditions for initial release are the ability to display, zoom in/out, scroll around, highlight sections, flip bits, delete bits, insert bits, and set bits to a value.  I currently have up to the flip bits features done.  In addition, I have the ability to plugin "transformations" where a plugin will be given the binary data and the plugin can modify it as it sees fit.  (Things like packet framing, decryption, etc.  Encrypted/properly decrypted data is generally very obvious in a raster view!).  

Why a binary editor?  No, I won't publish the result of the project thanks to the DMCA, but I want to be able to take over my lutron casetta home automation system at the RF level.  The system is based on a rather odd bit rate.  It retransmits the same packet multiple times and just expects the receiver to get some bad bits because of the inability to properly synchronize (or so it seems, I'm still early in the investigation).  So when running my HackRF continuously, I get spurious bits.  I wrote a framer plugin, and so even when synchronizing, I get spurious bits.  I'd like the ability to generate "clean", "corrected" and trimmed files to work on the protocol.  Why the lutron system?  While the product is going strong right now, companies have a habit of bricking devices when they are "no longer profitable", and since there is no monthly fee, you *KNOW* thats coming eventually!  I want to be ready.  If/When Lutron does brick everything, assuming I have a working solution, I will check with an attorney and see if I can release details on how to unbrick the devices using your own server.  (I believe if they shut things down, its considered abandonment, and fair game, but I'm not a lawyer!) In addition to that motivation, the lutron pico switches are about the best remote IOT/Home automation switches I have found.  The Hue switches, as an examble, are downright awful.  they are huge, don't fit in standard electrical boxes, come with double sided tape that ruins paint (instead of command strips).  They're terrible.  Worse, they're unreliable.  I get the red light more often than I care to report.  I like my bulbs in the rooms I use them in, but the rest of the ecosystem is horrible.  It would be nice to have a local hub able to read the pico switches and control the hue.  That's what I'm looking to do :)

SO that's a little about me and my projects.

Other hobbies list is massive.  To start, I have a CNC machine shop, a 60x90 laser cutter, an inverter powered tig welder (so I can weld aluminum), a large 3D printer.  Between that list and the arduinos/electronics/programming, its pretty clear I identify with the "maker movement"!  I'm also into digital photography, specifically with interesting post processing techniques like HDR and Focus Stacking, cooking (I have a few of my own original recipes), fitness, investing, robotics, IT/Networking (I have a dual xeon server and 2 nexus 3K switches, and a PFSense machine running my network housed in a 72U rack, cooled by a 27 SEER mini-split air conditioner), and more I can't think of now :)  I'm in programming mode :)


