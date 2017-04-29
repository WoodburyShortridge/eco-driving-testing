# SoundCardWebApp

## Demo

### See https://woodburyshortridge.github.io/eco-driving-testing/ for demo

For driving simulator prototypes see https://github.com/WoodburyShortridge/registerProj

## Overview of the README:
1. Overall Layout
2. Modifying for other tasks
3. Getting data ready for analysis

----------------------------------------

## Overall layout of the program

This program is made up of the three different pages: an intro, the tutorial page, and the test.

Index/Intro: includes a short text description of the overall layout, and generates the random order for the pages

Tutorial Page: includes descriptive text about the task itself (the drag and drop, this is a place to have a participant/user practice the task). They'll need to match a sound to each icon before they can go to the next page.

Test page: includes directions about the sound card sorting task at the top. Right now, there are 10 modals, with 8 sounds for each modal's page, to match to 8 icons. A user will need to match each sound to an icon (and only 1 sound per icon) to move on the the next page. At the end, you'll be prompted to fill in the filename. When you click the save button, it creates a text file.

Cookies (temp data storage for the browser session): A cookie is doing temporary storage for recording the responses from the user from each page. It's pretty easy to write to a file at the end and then import into excel.

File saving: A file is created at the end once a user has completed all of the modals.

# Modifying intro page (number of pages total) `intro.html`

There is only one section that needs to be changed. Around line 63 in the into.html page, you need to add to the line `var order =([1,2,3,4,5,6,7,8,9,10]);` If I were doing 15 trials, I would update it to show: `var order =([1,2,3,4,5,6,7,8,9,10,11,12,13,14,15]);`

## Modifying the tutorial page. `tutorialPage.html`

Sound icon + clips:

	<div id="8" class="sound">
		<img src="images/sound.png" class="soundController" class="img-responsive" 	height="30" width="30" alt="sound icon" data-audioid='8'>
		<audio class="audioController" id='a8'>
			<source type="audio/mpeg" src="soundTest/sputnik-beep.mp3" > Your browser does not support the audio element.
		</audio>
	</div>


and one of the dropzones:

	<div id="dropZone8" class="dropzone" data-selectid='0'>
		<p>Drag and drop sample sound here.</p>
	</div>

## Getting data ready for analysis:
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
