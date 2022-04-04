# orator
A scripted oration management system meant to provide an immersive experience for running in-game Achaean rituals, orations, plays, presentations, meetings, and more. As I began to run more scripted rituals in-character, I found myself needing to copy-paste blocks of text from editors which was a bit unwieldy, and distracting from the in-game experience. So I ended up creating this package that allows for preparing smart canned *Orations* that can be delivered manually, or even on timers, leveraging concepts like placeholders as well. I hope this helps some folks - keep reading for details on how to install and use it.

## Installation 
1. Download the orator.xml file from the master branch (check back for updates if/when you need to)
2. Open Mudlet to your favourite Achaean profile
3. Click Packages > Install new package
4. Navigate to your locally saved orator.xml, and install it

## Orations
Orations are the top level entity that would be your ritual, play, or whatever you're using this system for. You can have many orations, and you can think of them as your script. Each one has a title, and a bunch of Segments (more on those later). Most of the editing that you might do on an Oration is hyperlink based, so the best way to get started is to enter `oration ls` to list out your Orations, and go from there. If you don't have any Orations created, you can use `oration new <title>`. From the Oration List, you can click to edit each of your Orations, which will drill down and allow you to create and organise its segments.

## Segments
If Orations are the scripts, then Segments would be the lines. Each Segment represents a command block sent to the game. A Segment's command could be anything from a SAY, EMOTE, CONJURE ILLUSION, YELL, SHOUT - anything you'd normally send to the game. When Presenting (more on that below), your Segments will be delivered in numeric order either manually or on a timer. 

## Editing Orations
When editing an Oration and viewing the list of Segments, the hyperlink buttons to the right of each Segment all have hover text that should make it clear how to get your Segments to do what you need.
* Clicking the up/down buttons will move Segments up or down respectively
* Clicking E will prefill your Mudlet input box with the command needed to replace the Segment command
* Clicking D will delete the Segment
* Clicking the alarm clock will prefill the input box with the command needed to set a delay on a Segment

At the bottom of all of the Segments you'll see a hyperlink to edit placeholders. You can optionally provide a SPACE-SEPARATED list of placeholders such as `person1 person2`. That will be important later in Presentations, and they can be referenced in your Segments' command bodies using the syntax `{person1}`. For instance your first Segment might be something like "SAY welcome everybody for the public shaming of {person1}." Placeholders are meant to make these Orations as re-usable as possible.

## Presentations
By default, Orations are in 'draft' status. This is just a helpful status for your own sanity to remember if you're finished with it or not. When your Oration is complete, you can run `oration ls` and click `publish` to toggle your Oration out of draft mode. When you do that, you'll now have a link called `load` which will prep your Oration for delivery. The next command you'd run to begin the delivery of your oration is `orate begin`. IF you have assigned any placeholders to your Oration (see Editing Orations) it will prompt you to fill in each placeholder for your current Presentation. Once all placeholders have been captured, you'll receive a message saying you're ready to begin, with a preview of the first Segment to be delivered.

Once a Presentation has begun, you can use the `orate` command to walk through your Segments in order. If your Segments have delays assigned (using the alarm clock icon in Editing Orations) that means the Segment immediately following it will AUTOMATICALLY fire after the input amount of seconds. This is handy if you're confident enough in your timing to automatically deliver an Oration. Otherwise, the Oration wll not continue until you manually `orate` for each step.

### Some handy Presentation commands
* `orate stop` - prematurely exit from an Oration and stop Presenting
* `orate status` - prints out all Segments in your current presentation (grey ones were already delivered, the yellow one is coming up next, green ones are coming up in the future)
* `orate step <number>` - deliver a specific Segment. This basically forces the Presentation into a certain step (handy if you need to skip one or more Segments, or if you need to go back)
* `orate pause` - if your next Segment will be delivered on a timer due to a delay that you configured, this will kill that timer and not progress until you manually `orate`
* `oration safemode (on|off)` - Turn SAFEMODE on or off. When in safemode, any oration segments delivered will be echoed to you instead of sent to the game. One time while practising an oration in the privacy of an office, a certain Divine was watching me and questioning my sanity. Hence the birth of SAFEMODE.

## Giving back
This is given freely to the Achaean community, and I'm hoping it helps people. If you want to contribute by making this better, please submit pull requests! If you have feedback for how this can be better but no time or desire to contribute code, let me know! If you want to say thanks with small credit donations, Tysel wouldn't mind that.
