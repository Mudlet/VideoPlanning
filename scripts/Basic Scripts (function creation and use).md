## Script

Hello,

In this tutorial we will be going over creating basic scripts for Mudlet. Mudlet uses Lua for its scripting. Lua is a light weight and speedy scripting language well suited for embedding in other programs.

Specifically, I will be covering how to create a script in Mudlet, how to write a function to group repeated actions together, and how to pass information into functions.

So let's get started by clicking on scripts to bring up the script editor. Then we will click on Add Group to create a folder to organize our scripts in. You can put code in these if you like, but I primarily use them to keep things tidy and organized in my script editor. I'll just name this 'Tutorial Scripts' or something obvious, and then we'll click on Save Item.

Then when we click on Add Item it will create the new script object inside of the folder we just created. Let's just give this a name and then save it. Now over here on the left, you can use the dropdown marker to show or hide the scripts in this group, which can make it a lot easier when browsing through things later.

Ok, over here on the right I just want to acknowledge the existence of the "Registered Event Handlers" and "Add User Event Handler" sections. These are used for dealing with events, which are a Mudlet feature which will get their own video soon, but in the meantime we can pretend these don't exist and concern ourselves primarily with this big box down here. This is where we will put all of our Lua instructions. Scripts are run every time you save them, and also once when the profile loads, so they're a great place to put functions which you will use later on in your triggers and aliases so they're already defined and ready to go by the time you connect to your game. 

If I type a basic instruction in here, such as send("hello"), and click save, you can see in the main screen here that it's performed that send immediately. Send is the Mudlet's basic function to send something to the game as though you'd typed it in as a command. What we're going to do now is create a function which will perform a couple different tasks and produce output, and which we can reuse any time we want to do that, whether it's in a trigger or alias.

We'll start by creating a table. You can think of a table as kind of like a filing cabinet to hold your stuff. In this case I'm naming the table 'demonnic' because that's my name, but you could use anything you think is unlikely to be used already. I'd steer clear of simple, obvious names like "HP" or "vitals" so you can avoid fighting over the name when you install someone else's scripts. Also, I write it in the form of "demonnic equals demonnic or " so that if the table is already defined, it does not redefine it. This way if I'm working on my scripts while playing I'm not constantly wiping out all the data. So this line says to Lua "create a variable named demonnic, and if demonnic already exists store that there, otherwise store an empty table there". Variables are like labels you put on information so you can find them again later. In this case, we're labeling this table as "demonnic" so when we look for "demonnic" we get this table.

The open and close curly braces tell Lua you're defining a table. When used like this, it creates an empty table. I'll go over other ways to make tables with prefilled data in a later video on tables, but for now just know that we're creating or reusing a table named "demonnic" to hold the function we're about to write.

Now let's define the function. You use the "function" keyword, following by the name you want to store the function under. In this case I use "demonnic dot testFunction" because that tells Lua to put testFunction inside the demonnic table. So it creates a drawer (variable) in the filing cabinet labeled "testFunction" and it will store the function in that drawer for us to get later. The "end" here denotes the end of the function. I go ahead and add it immediately, and then I never have to wonder if I closed the function, as I did it right away. Now whatever we put between this function line and this end line will be stored as "demonnic.testFunction". So let's put some stuff in there.

demonnic = demonnic or {}

function demonnic.testFunction()
  local time = getTime(true, "hh:mm:ss")
  echo("The time is: " .. time .. "\n")
end

For this first line, we start with the 'local' keyword. This tells Lua that you only care about the variable you're about to define inside this function. It will only exist while this function is running, and will not be accessible to anything outside of this function. But it also means it won't accidentally overwrite any other 'time' variable which has been created. getTime here tells Mudlet to tell us what time it is, and the hh mm ss tells it what format we want to see it in, in this case as hours, minutes, and seconds. I'll put a link to the information on getTime in the description if you're interested in more information on that. 

We then take this information and echo it to the main window. The double dots here tells Lua to add these two strings together. So it will add whatever is in the time variable to "The time is" , and then we add a newline, which is what the \n stands for. It's like telling the computer to hit enter in the output for you.

Now when we click save, you'll see nothing happens in the main window. But if I use the built in lua alias to run the function... and there's the output.

Now, let's say we want to have it echo the time in a color we can specify. Going back into the script, we would add what's called a parameter to the function, in this case we'll just call it color. Then we need to change echo to cecho, which allows you to use color names to colorize the echo output. We need to put the color name in angle brackets so that cecho knows it's an instruction to change the color, but otherwise it's still just adding strings together to make a bigger string. Now, let's save this and go back to the main window, where we can use the lua alias again to show what we've made. Notice I'm putting red in quotes here, if I did not put it in quotes it would try to look up the variable named "red" and use that value, but since it's undefined things would go wrong. And then when I hit enter, you see it prints the time in red. I can also use "blue" or "green" as you see here.

In today's video, we went over the basics of script objects in Mudlet, how to create variables and functions in a script, and how to write a function which can change what it does based on the information you pass into it. Future videos in this tutorial series will expand upon this information, but these basics of creating and interacting with Lua variables and functions  form the core of what you will need to know when working with other things such as triggers and aliases in order to get the most out of Mudlet's potential. I hope this video was informative and helpful, and I look forward to creating and sharing the next one with you all. Until then, happing MUDding. 

## Link

https://youtu.be/10mJUh4Hq-A