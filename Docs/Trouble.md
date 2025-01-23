# NOTE!

This document was setup when the game still ran in Apollo. 
I will need to revise (or perhaps even rewrite it) once the operation is done, or at least in a state that I know more of all consequences of this operation!

# Troubleshooting

In this document you will find some trouble you may encounter or which may get you some questions. The stuff noted in this document is stuff you should not make note about in the issue tracker, as your issue is likely to be closed without paying it further notice.



## I notice a few slowdowns whenever I load the menu and some of its sub-parts for the first time.

The game uses for nearly all its components a "load-on-demand" system. Most components are only loaded the first time they are needed. After that they will remain in the memory until you shutdown the game (unless it handles stuff that is after the first time usage no longer needed).
This saves time during the game's start up, but it also prevented me a crap-load of trouble during the game's creation and debugging sessions.
Since everything is composed out of Neil scripts, the scripts need to be loaded, translated and then compiled, and this can require a little more time, however this comes back in stability and no needless loading of stuff never used at all.

Of course this does not only handle the scripts, but most of the assets as well. And since the inventory uses a lot of different icons which all need to be loaded, well, you get the picture.

## Sometime the game slows down when there are a lot of enemies in the field

I've done all I can to speed this up. The maps where this was very terrible has an underlying "REJECT" system which rejects enemies not in the same reject-zone as you are, saving time in the process, however this is not exactly waterproof. This was already a bit of an issue in the original game and kept on haunting me in this remake. One of the reasons I went back to random encounters in all RPG games I wrote later, however I had to keep it in this remake to keep the original game's setup alright.
If you think you can do a cool job in getting this stuff faster, lemme know. The scripts are open-source for a reason.

## Does the game work well on Linux and Mac?

On the moment I wrote this document, neither system has been tried at all. The Apollo engine was written in VisualStudio, however Microsoft saw fit in "deprecating" (read: blocking) many feature GCC (which is far more common on Unix systems) heavily relies on. Most of this handles stuff I set in separate libraries though, and I hope it shouldn't be too hard to make the source that way it can compile in both VS and GCC. My prime concern however was to make sure the Windows version did at least work. All platforms I could support later are bonus.
Since I only have Linux in a VM, and I no longer have a working Mac, I cannot give any active support for either platform, meaning I cannot fix any bugs that are specific these platforms. If you encounter a bug that is clearly the result of bad scripting (and therefore platform independent) it's of course a different story.

## How can I make the game contact the Game Jolt API?

You can't! I removed the Game Jolt API from the game, for many many reasons. And don't even think about trying the old game for this, as I blocked it from furhter access.
(If you read this document prior to the open alpha/beta, the old game still has this access, it will however be blocked once the open alpha/beta of this game is about to start).

I am not planning to bring this back not even by popular demand. The only reason why DYRT.NET still offers GJ trophies is due to the issues making me come to this decission came up when that game was so close to completion it was too late to start removing them on such a short notice.
Alternatives for the Game Jolt API may be considered, if they are not too hard (and free!) to implement.


## How can I download the game on Chromebook?

You can't. ChromeOS is only a browser disguised as an OS. Ever wondered how you could get Chromebooks so cheap?
Even if you were succesful downloading and even starting the game on Chromebook it will likely be slow as hell, as the hardware of Chromebooks is very minimal, which is logical, since Chromebooks were NEVER designed for gaming. 
Chromebooks can be wonderful devices, but only if you purchase them for their intended purpose. Buying a Chromebook when you want a computer for gaming is like buying a hammer in order to saw a plank.... Does that make a hammer useless? For sawing, yes, but but if you buy a hammer for the job hammers are intended, they are very useful. Chromebooks are much the same.


## Apple blocks me from playing the game on Mac.

First of all note this, no Mac release will be official unless I announce otherwise. But since Apollo is open source, everybody is free to port it for Mac.

Second, since I don't pay over $100 a year to Apple ~in order to fill their pockets~ in order to "prove" you can trust me, Apple blocks anything I have to offer by default and brings it up like the most horrible malware imaginable... Well they don't say it, but the way they block stuff from developers who don't couch up the cash, strongly implies that.
You should be able though, to right-click the application and then choose "Open" from the pop-up menu. If you have a one-button mouse use ctrl-click in stead of right-click. Now MacOS X should still moan about unknown developer and stuff, but still give you the option to open the game. Once opened succesfully Apple should not throw these blocks again, unless either the game or MacOS X itself comes up with an update.

And don't send me messages saying that "MacOS X" is no longer the name, as I don't care. Apple changes the name of their OS so often that I can't be arsed to change my documentation about it all the time, so go whine to Apple about it and not to me. I don't think they'll care though (since they don't care about their customers at all, as far as I noticed).

This is the only Mac specific issue I can help with, as this is a very general issue with free applications on Mac in general. Technical items I cannot help with, and you'll have to bother the makers of the Mac port about that, I'm afraid.


## I see my Max HP go down over time

That is not a bug. This only happens if a character is under the influence of a HP buff, which temporarily raises the maximum of you HP. This will gradually go back to its official unbuffed value. Once that value is reached the 
going down will stop. The reason I note it here, is because this may appear a bit frightening when you see this happening without any explanation.
