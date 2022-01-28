# Script

Hello,

In this tutorial, I will cover creating a basic alias to perform simple or repetitive tasks for you, as well how to make an alias with an optional argument to cast "cure wounds" on somebody else, or yourself if you don't specify someone.

To start, let's click on Aliases. You can see here on the left that there are several preinstalled aliases which come with Mudlet. I'll go over these in a later video, but for now let's click on "Add Group" and name this group "Alias tutorial", then click on save item. You will then need to click "Activate" in order to activate the group, as they start disabled. 

Let's now make our first alias by clicking "Add Item" and naming this alias "check pack". We then give it a pattern, which will determine when this alias is executed. I'm going to use "^cp$" (caret c p dollar sign) because I want to make sure this fires only when I type exactly "c p" as the command. For those who have not watched the basic regular expressions video, the caret matches the beginning of the string, and the dollar sign matches the end. 

Then, in the code box here at the bottom I will put send("look in pack")  and click "Save Item". The alias itself is automatically activated so long as no issues are found in the pattern or the script at the bottom. Then when I go back to the main window and type "cp" and hit enter, you can see that it sends "look in pack". When an alias matches in this way, the original text, in this case cp, is not sent to the game. So all your game knows is you sent "look in pack" as a command.

For an alias as simple as this, we could just type "look in pack" in this command line here, but for anything more complicated than sending a single command like this you'll need to use the script box, so I recommend getting used to using it from the start.

Now let's look at a slightly more complicated example. I'll click "Add Item" as before, and name this one "cure wounds". The pattern will start similarly, caret, c, w, but then it changes slightly. We'll add an opening parenthesis here to start a capture group, then a space and dot plus, and the closing parenthesis to end the capture group. I briefly touched on capture groups in the basic regular expression video, but this is going to let us use the information later. I'll then finish it with a question mark and a dollar sign. The question mark here is new. In regular expressions, a question mark means "0 or 1 of", so this alias will match on c w all by itself, or cw followed by a space and anything else, which will be the target. If you want the argument to be required, just leave the question mark off.

Here in the script box, we will put this into action. This is covered in the Basic Scripting video, but we start with the keyword local, followed by target. This tells Lua that this target variable is special to this alias, and it won't touch any other target variables or be touched by them. Then we set it equal to matches[2], which stores the the first capture group (`the space and whatever the dot plus matches), or  self if the argument wasn't included. The reason it is matches 2 and not matches 1 is that for all aliases and triggers, matches 1 holds the full match, which leaves the first capture group at matches 2, the second capture group at matches 3, and so on.

So this line says "make a special target variable just for me, and put the capture group in it if there is one. Otherwise, set it to self"

Then on the next line, we use send("cast 'cure wounds' on" .. target) to have it actually send the command. The dot dot tells Lua to add the string held in the variable target onto the end of the "cast cure wounds on" string, and then send sends the combined result on to the game.

Moving back to the main window, you can see if I type cw on its own, it casts cure wounds on self 
But if I type cw bob then bob is the target of the cure

These two examples should hopefully serve to guide you through many of the aliases you'll need to make in Mudlet.

In today's video, we went over how to create a simple alias, as well as how to create an alias with an optional argument you can pass in to change the alias's behaviour. In future videos we will begin covering the different types of triggers, and how to setup triggers and aliases which do the same things using functions. I hope this video was informative and helpful, and I look forward to creating and sharing the next one with you all. Until then, happing MUDding. 

## Link

https://youtu.be/Uz6EDvZYNvE