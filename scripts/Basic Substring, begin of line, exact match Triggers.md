# Script

Hello,

In this tutorial, I will cover  the three different types of substring triggers in Mudlet and what the differences between them are, as well as some of the basic overall trigger features.

Let's start by clicking on Triggers to bring up the trigger editor. Then let's click "Add Group" and name this group "Tutorial Triggers" and click save. Then we'll click on "Add Item" to make a new trigger. Let's name this "Enemy Highlight"

We'll use this trigger to highlight our enemies, as the name implies. We really want them to stand out, so let's check off highlight here in the bottom right. We'll accept the defaults, red on yellow is VERY easy to see.

Now, let's imagine that Bob was recently caught stealing a cow from our farm, and boy does that make us mad. Bob is now our enemy! So let's add Bob's name to pattern 1 here of this trigger. Now let's click "Save Item"

In the Mudlet main window, we'll use the \`echo alias which comes preinstalled in Mudlet profiles for testing triggers to show the highlight.

\`echo Bob appears from across the horizon

As you can see, Bob is highlighted and his name just leaps out of the text at you. Let's try another one.

\`echo Bob and Bob Jr. appear from across the horizon

Oh dear, we see here that it's only highlighted the first instance of Bob. His son, Bob Jr, is likely to be caught up in this feud as well so we want to make sure he is also highlighted. 

Going back to the editor, if we check off "match all" here, then it will match for every instance on the line.

If we click save, then go back to the main window and repeat the previous echo, you can see that both Bob's are now highlighted. 

You can add another substring pattern below that for Jr. and save it. Now let's repeat the previous echo.
Hmmm. What if we try instead with

\`echo Jr. is a common suffix

It does highlight it.

Going back into the editor, I can explain why. When a trigger has multiple patterns in it, and multi-line AND is not checked, then it will check each of its patterns in order from top to bottom, and stops when it finds the first one that matches and fires on that. In this case, it encountered 'Bob' before 'Jr.' and fires for all instances of Bob on the line, but didn't keep checking any of the patterns after that. 

These patterns are both substring patterns, which means if the text in the box appears exactly like that anywhere in a line, it will be highlighted. 

Going back to the main window, we can see that 

\`echo Bobbin bobbed for apples

Highlights the Bob in Bobbin, but not the one in bobbed, because of the lowercase b.

Heading back to the editor, the other substring triggers are "Start of line" , which is the same as substring but it must start the at the beginning of the line only. There is also "Exact Match", which must match the entire line exactly from start to finish.

These three trigger types collectively are the fastest ones in Mudlet, and useful when you know exactly what text you're trying to match.

If you wanted to also have it play a sound, you could click the "play sound" checkbox here on the right, then "Choose file" and select the file you want to use. And if I resend the last `echo in the main window

And the sound is played.

The rest of the options in the trigger editor here we will go over in future videos, but they do not apply to the majority of triggers. In fact, for the majority of triggers you can click this arrow here and it will remove the options from the view and leave primarily the patterns, and the code block at the bottom. 

Which brings us to the code block. Any code which you put in here is executed when the trigger matches. So if we wanted to add an additional message echoed to the end of the line to -really- make sure we notice that dastardly Bob, we could add code in here like `cecho(f"<red>{matches[1]} is here! ")` so. Cecho is the function which you can use to echo coloured text to the console by color name, such as red in this instance. the F here is a function which allows you to insert the contents of a variable or outcome of a statement inside of text. To do so, you precede the string with f as shown, and then include the variables you want to have expanded into the string between the curly brackets as shown. matches[1] holds the text which the trigger matched, so if it matches on Bob, then it will says "Bob is here!" in red.

So let's hit "Save Item", then go back to the main window, and retry the last echo.

And now it shows that Bob is highlighted in Bobbin, the sound is played, and it tells us Bob is here as "Bob" is the text which was matched in the trigger pattern.

A couple last notes about triggers in general. Mudlet evaluates triggers from top to bottom in order. This doesn't turn out to be important often, but it can occasionally be helpful when troubleshooting issues when you're modifying the line in the main console in multiple triggers, and is a question we get asked a lot. Also, triggers are checked against the line as it came in from your game originally. Modifying the line via cecho as we did earlier will not change how any later triggers match. We could not make a trigger to match the "Bob is here" text we added in our example, for instance, as it's only added to the display.

In today's video, we went over how to create a substring trigger, the three types of substring trigger and what the differences are, as well as the basic trigger options. In future videos, we'll go over regular expression triggers which allow you to match text which changes very accurately, and extract pieces of it for use in the trigger's code block. We'll also go over the remaining types of trigger patterns which Mudlet supports, and even further down the line we'll explore some of the more advanced capabilities of Mudlet's Trigger engine. I hope this video was informative and helpful, and I look forward to creating and sharing the next one with you all. Until then, happing MUDding. 

## YouTube Description

A tutorial for basic substring triggers.

Download Mudlet at https://www.mudlet.org


## YouTube Link
https://youtu.be/jYjop54-Y3I
