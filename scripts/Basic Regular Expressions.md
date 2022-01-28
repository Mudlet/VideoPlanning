# Script

Hello,

In this tutorial we will be going over the basics of regular expressions. Regular expressions are use repeatedly for triggers and aliases, so I felt it important to cover this topic before those. 

This website is regex101.com, and is my favorite website for creating and testing regular expression patterns. It breaks your pattern down and allows you to test it against one or more test strings. It also has a nice reference for what the different wild cards and symbols mean within a regular expression. Mudlet uses the PCRE regular expression engine, so you'll want to select PCRE over here on the left.

In a nutshell, regular expressions allow you to match text which changes, and capture information out of them. For instance, if your game sends "A goblin falls over dead." like so, you can match it with "A (.+) falls over dead". Putting it in parentheses tells it you want to capture that information. Which is why it is called a "capture group". the dot is a wildcard which can stand in for anything, and the + tells it to match one or more. So in "A goblin falls over dead" the first capture group would be "goblin". 

This is a very simple way to capture things, but where possible you should try to be more specific. If all mob names are letters or numbers only, you could instead use (\w+) here. \d is used in place of number, and can be used to match something like "You have 100038 gold on you" with "You have (\d+) gold on you". If the number might have a , in it, then you would instead want to use ([\d,]+) The brackets allow you to define your own groups how you want, in this case we add the comma to \d so it will catch any number of digits or commas. \s will match whitespace characters such as spaces or tabs. And it's often good to use the ^ (caret) to anchor to the beginning of the string, so your trigger doesn't match if the text appears in a room description or comes up during conversation. In a similar vein, $ matches the end of the string.

I'll put a link in the description to regex101, and we'll have a future video on more advanced regular expression usage, but these are the basics you'll run into the most while making aliases and triggers using regular expressions.

In today's video, we went over the basics of regular expressions, what they are, and how to use them, and I shared with you my personal favorite site for creating and testing regular expressions. In future videos, we will use this knowledge to create aliases and triggers in order to have Mudlet help you with the interactions between you and your game. 

I hope this video was informative and helpful, and I look forward to creating and sharing the next one with you all. Until then, happing MUDding. 

## Link

https://youtu.be/KFoax1Q0ltw