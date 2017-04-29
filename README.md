# SoundCardWebApp

## Demo

https://woodburyshortridge.github.io/eco-driving-testing/

## Overview of the README:
1. Overall Layout
2. Modifying for other tasks
3. Getting data ready for analysis


----------------------------------------
----------------------------------------


1. Overall layout of the program

This program is made up of the three different pages: an intro, the tutorial page, and the test.

Index/Intro: includes a short text description of the overall layout, and generates the random order for the pages

Tutorial Page: includes descriptive text about the task itself (the drag and drop, this is a place to have a participant/user practice the task). They'll need to match a sound to each icon before they can go to the next page.

Test page: includes directions about the sound card sorting task at the top. Right now, there are 10 modals, with 8 sounds for each modal's page, to match to 8 icons. A user will need to match each sound to an icon (and only 1 sound per icon) to move on the the next page. At the end, you'll be prompted to fill in the filename. When you click the save button, it creates a text file. MAKE SURE YOU CLICK THE BUTTON TO DOWNLOAD THE TEXT FILE/DATA. THIS WILL RESET IF YOU LOAD THE INTRO PAGE AGAIN/REFRESH THE ~~INTRO~~ PAGE OR CLOSE THE BROWSER WINDOW.

Cookies (temp data storage for the browser session): A cookie is doing temporary storage for recording the responses from the user from each page. It's pretty easy to write to a file at the end and then import into excel.

File saving: A file is created at the end once a user has completed all of the modals.



----------------------------------------
----------------------------------------



2. Modifying for other tasks

AKA how to add/remove "pages" (modals) + sounds + icons

Scenario: This is written to work with 10 pages, currently, but what if I wanted to do 15 different sets of sound card sorting, instead of 10?

RECOMMENDATION: Go download Notepad++ to open/edit these files. It's awesome and color codes things.


----------------------------------------


2A. Modifying intro page (number of pages total) [intro.html]

There is only one section that needs to be changed. Around line 63 in the into.html page, you need to add to the line "var order =([1,2,3,4,5,6,7,8,9,10]);" If I were doing 15 trials, I would update it to show: "var order =([1,2,3,4,5,6,7,8,9,10,11,12,13,14,15]);"

Make sure you save the file, and that's it!


----------------------------------------


2B. Modifying the tutorial page. [tutorialPage.html]

Right now, I have it with 8 different sounds. You probably don't need to make changes to any of these, but if you want to do less than 8, you'd delete one of these (a sound icon + clip):

<div id="8" class="sound">
	<img src="images/sound.png" class="soundController" class="img-responsive" 	height="30" width="30" alt="sound icon" data-audioid='8'>
	
	<audio class="audioController" id='a8'>
		<source type="audio/mpeg" src="soundTest/sputnik-beep.mp3" > Your browser 			does not support the audio element.
	</audio>
</div>


and one of the dropzones:


<div id="dropZone8" class="dropzone" data-selectid='0'>
	<p>Drag and drop sample sound here.</p>
</div>

It doesn't really matter which you delete, but I would recommend removing ones from the end of the list first. You probably don't need to change this, since it's just a tutorial.
       

Make sure you save the file, and that's it!


----------------------------------------


2C. Modifying the test page [test.html]

This is the more complicated page, but it's still fairly easy to update. 

Back to our example scenario for 15 "pages" (modals) instead of 10. 

To make it easier, anything in the ["stuff goes here"] stays the same and you can copy it exactly.

1- If you want to change the directions, simply change the text inside of the paragraph (<p></p>) tags. I could change [<p> Pandas! </p>] to [<p> To listen to each of the sounds, double click on the sound icon. </p>]

2- If you want to add to the number of pages, scroll down to around line 1341, and copy the entire div that's there (the "<div class="modal fade" ... id="modalId10"> down to it's matching </div> at line 1471.) 

Once you have that copied, there are a few things you need to do:

1) For  that top <div class="modal fade"...> update the [id="modalId10"] to [id="modalId11"] (or 12-15)

2) In the <div class="panel-body" id="modalContainer10"> update this to [id="modalContainer11"] 

3) Update all 8 of the <div id="#" class="sound"> to the new, unique numbers. Right now, throughout all 10 original modal pages, I used id values of 1 - 80. If you're doing modal 11, you'll number them 81-90. This mean's you'll do: [id="80"] to [id="81"].

4) You'll need to update the <img> tag's [data-audioid='80'] to [data-audioid='81'] and the <audio> [id='a80'] to [id='a81'].

5) If you want to change the audio files, go to the <source> tag and change the [src="soundTest/fog.mp3"] to [src="soundTest/ewokCall.mp3"]. You'll need to make sure you copy the file into the soundTest folder in the SoundCardWebApp main folder. 

Also, you can use .wav or .mp3s. These lines will either look like:
<source type="audio/mpeg" src="soundTest/pandaCall.mp3">  or <source type="audio/wav" src="soundTest/wookieCall.wav" >

6) If you want to update the images for matching the sounds to in the dropzones, you'll need copy them into the images folder that's inside the SoundCardWebApp project. Then here, you'll change the [src="images/sunny.png"] to whatever the new image is, such as [src="images/lolcats.jpeg].

7) You would need to do this process for the rest of the pages (if you were going up to 15 modals). 

8) Make sure you have unique IDs for things!

9) You can also add to the number of sounds and dropzones/icons for any page. Do the same process as before, but *inside* the current modal instead of in a new one.
             


                                                 
----------------------------------------
----------------------------------------



3. Getting data ready for analysis:
AKA Text importing into excel:

MAKE SURE TO SELECT AN OPEN CELL IN AN OPEN ROW
1. Go to Data tab
2. Select "Get External Data from Text" 
3. Select the text file
4. Choose "delimited"
5. Select all text boxes, and add "=" for other.
6. Leave it as "general"
7. Hit ok. 

** Modified from these directions: 
https://support.office.com/en-za/article/Import-or-export-text-txt-or-csv-files-5250ac4c-663c-47ce-937b-339e391393ba
