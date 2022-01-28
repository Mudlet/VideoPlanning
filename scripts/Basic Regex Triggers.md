# Script

Hello,

In this tutorial, I will cover regular expression, or "perl regex" triggers in Mudlet, how to use them to extract information from your game, and some things to keep in mind when making use of them.

We have a basic regular expressions video as well as a basic substring trigger video which you may find it helpful to view first. There are links in the description for them if you'd like to review them before moving on. There are also links to some helpful resources for learning more about regular expressions, as well as testing and analyzing regular expressions which are touched on in the basic regular expressions video.

Now with the preamble out of the way, let's begin by clicking Triggers to open the script editor up to the Triggers page. I'll start by making a group to keep my triggers organized, call it "Basic Regex Triggers", and click "Save Item". Then let's click "Add Item" and name this one "Regex1". Then let's click the dropdown next to the first pattern and change it from substring to perl regex. The color for this pattern line changes from black to blue to give a visual clue as to what type of trigger it is.

It needs a pattern, so let's go with something simple for now, `You pick up (\d+) gold\.$`

We will use this pattern to track the gold we've picked up this play session. Let's click on "Save Item" and get started on the script that will handle the tracking for us. The information in the Basic Scripting video holds true for triggers as well, so let's start this with `demonnic = demonnic or {}` which creates a table to hold our variables if it hasn't been created yet, or if it has will use the one which has already been created. This keeps us from wiping out the information we've already collected every time the trigger goes off.

We'll then add `local gold = tonumber(matches[2])` . Things matched by triggers are text rather than numbers by default, so tonumber gets the number equivalent. This way we avoid potential future issues when we try to do math with it. And we use matches[2] because matches[1] stores the entire match, then matches[2] is the first capture group, matches[3] is the second capture group, and so on. So this line says "Create a local variable named gold, and store the value in the first capture group as a number in that variable"

So on the next line, let's add this number to our total. `demonnic.gold = (demonnic.gold or 0) + gold` This line tells Lua "take the value from demonnic.gold, or 0 if demonnic.gold doesn't exist yet, add gold to it, and then store the result as demonnic.gold. Let's click "Save Item" again to save our work. Now, I've prepared an alias in advance which will feed that line to the trigger engine with an amount of gold I specify. if we use it to say we picked up 20 gold
(typed)
`pug 20`

And then check the value using the lua alias
(typed)
`lua demonnic.gold`

It prints 20. If we pick up another 45 gold and check again
(typed)
`pug 45`
`lua demonnic.gold`

It prints 65, so it's keeping track of it for us. But I don't want to have to type that out every time I pick up gold to see the total. Let's go back to the trigger and make it display for us. At the bottom of the current script, let's add `cecho(f" <gold>{demonnic.gold}")` cecho lets us print color text to the screen, and f is a function which lets you do string interpolation. The value of whatever it finds between the curly brackets in the string you feed to it will be used in that place in the string. Lua allows you to omit the parentheses when you call a function with only a single string or table parameter, but it is generally not considered best practice to do so, and using f for string interpolation like this is the only place I typically use this capability myself.

And now back in the main window, we get the information echoed back to us when we use our alias

(typed)
`pug 103`

Now for regex triggers if you check off highlight it will highlight the capture groups for the trigger only. If you want to highlight the entire match this way, you can put parentheses around the entire pattern  which will make it all a capture group as well, and thus highlighted. This does shift around the location of the captures in your matches table, though. Which leads me to the next feature, named capture groups. To avoid having to change my code if the pattern changes, let's change the pattern to this instead
`^you pick up (?<gold>\d+) gold\.$`

And now we change matches[2] in the script to matches.gold. This can often make it much easier to work with your capture groups. Let's click "Save Item", then go back to the main window and pick up some gold
(typed)
`pug 39`

Excellent. Now let's try one more. This one will auto heal us if we're under 50% health. Let's click "Add Item", then name it "Heal self" and put in the pattern `^HP: (\d+)/(\d+)` 

Then in the script box, let's add some code
```
local current = tonumber(matches[2])
local max = tonumber(matches[3])
local hpPercent = current / max * 100
if hpPercent <= 50 then
  send("cast 'cure wounds' on self")
end
```

From the top, we change the first capture group to a number and store it in the local variable current, then store the second capture group in the local variable max. We then get the percentage by dividing the current by the max and multiplying it by 100. Then if that number is less than 50, we cast cure wounds on ourselves. 

Back in the main window, we can test it using
\`echo HP: 39/100
\`echo HP: 83/100
\`echo HP: 1283/2000

And only the first one makes it cast, as it's the only one which is under half full on HP.

In today's video, we went over how to create a basic regular expression trigger and use it to store information captured from your game. We also went over some of the differences between a regex trigger and the substring trigger types, and how to use named capture groups for easier access to your information and easier to read code. I hope this video was informative and helpful, and I look forward to creating and sharing the next one with you all. Until then, happing MUDding.


## Links
```
Regular Expression analysis and test         : regex101.com
Good site for learning regular expressions: regexlearn.com
Basic Regex video                                       : https://youtu.be/KFoax1Q0ltw
Basic Substring Triggers video                    : <tbd>
```