# The PAWN Language | Applying the Fundamentals

This chapter will mainly include practical applications of the fundamentals taught in the prior chapter. Demonstrating the use of different features of the language through examples, this chapter aims to teach the intricacies of the fundamental concepts, therefore, after carefully reading the examples and their explanations presented in this chapter, the reader should have a better understanding of the concepts and hence should be able to apply them flexibly.

- [Application 1](#application-1)



## Application 1
As a first application we will be creating a very simple weapon shop, where a player can buy from a list of weapons.
##### Code
```c
#include <a_samp>

public OnPlayerConnect (playerid)
{
    SetPlayerCheckpoint (playerid, 2158.4797, 943.1600, 10.8203, 1.0);
    return 1;
}

public OnPlayerEnterCheckpoint (playerid)
{
    ShowPlayerDialog (playerid, 1, DIALOG_STYLE_LIST, "Weapon Shop", "Desert Eagle (50$)\nAK-47 (150$)\nM4A1 (200$)", "Select", "Cancel");
    return 1;
}

public OnDialogResponse (playerid, dialogid, response, listitem, inputtext[])
{
    if (dialogid == 1)
    {
        if (response)
        {
            switch (listitem)
            {
                case 0:
                {
                    if (GetPlayerMoney (playerid) < 50) return SendClientMessage (playerid, 0xFFFFFFFF, "ERROR: You don't have enough money to buy this weapon.");
                    
                    GivePlayerWeapon (playerid, 16, 30);
                    GivePlayerMoney (playerid, -50);
                }
                case 1:
                {
                    if (GetPlayerMoney (playerid) < 150) return SendClientMessage (playerid, 0xFFFFFFFF, "ERROR: You don't have enough money to buy this weapon.");
                    
                    GivePlayerWeapon (playerid, 24, 30);
                    GivePlayerMoney (playerid, -150);
                }
                case 2:
                {
                    if (GetPlayerMoney (playerid) < 200) return SendClientMessage (playerid, 0xFFFFFFFF, "ERROR: You don't have enough money to buy this weapon.");
                    
                    GivePlayerWeapon (playerid, 26, 30);
                    GivePlayerMoney (playerid, -200);
                }
            }
        }
    }
    return 1;
}
```
### Explanation
In the above code you can see some new functions and callbacks which are explained below.
#### public OnPlayerConnect (playerid)
As in the last chapter, the OnPlayerConnect callback is called whenever a player connects to the server.
#### public OnPlayerEnterCheckpoint (playerid)
The OnPlayerEnterCheckpoint is called whenever a player enters a simple checkpoint. A checkpoint is a red colored circular area often seen in single-player missions. The function used to create a checkpoint for a player is SetPlayerCheckpoint () which takes in five arguments : (Add Open.MP Function Link Here)
```c
SetPlayerCheckpoint (playerid, Float: x, Float: y, Float: z, Float: z);

playerid - The id of the player subjected to this function.

Float: x - The x-axis coordinates for the checkpoint.

Float: y - The y-axis coordinates for the checkpoint.

Float: z - The z-axis coordinates for the checkpoint.
```
*Note: If we use this function twice in a row, the older checkpoint will be removed which shows that a player can have only one checkpoint visible / functional at a time.*

#### public OnDialogResponse (playerid, dialogid, response, listitem, inputtext[])
The OnDialogResponse callback is triggered when a player interacts with a dialog shown to them. Dialogs are a way to display information to the player and/or take input from the user. There are different types of dialogs namely simple text box, input fields or lists. The function to show a dialog to a player is ShowPlayerDialog : (Add Function Link Here, From Open.MP)
```c
ShowPlayerDialog (playerid, dialogid, style, caption, info, button1, button2);

playerid - The id of the player subjects to the function.

dialogid - The unique id of the dialog.

style - Style or type of the dialog.

caption - The caption or title of the dialog shown.

info - The main text or content in the dialog to be show.

button1 - Text of the first button.

button2 - Text of the second button.
```
Once we show a dialog to the player, we can get the player’s response from the OnDialogResponse callback which provides us with some useful data in the form of local variables.
```c
public OnDialogResponse (playerid, dialogid, response, listitem, inputtext[])

playerid - ID of the player who interacted with the dialog.

dialogid - The unique ID of the subject dialog.

response - Holds boolean value (true or false) indicating the button pressed. (True for button1, False for button2)

listitem - Returns the selected listitem (provided that the dialog was of such type)

inputtext - Returns the text input into the dialog's text field (provided that the dialog was of such type)
```
Now that we know how the purpose of the functions, we can start breaking down the program into smaller parts top to bottom, for a better understanding of how it works. On the top, like usual we add the <a_samp> header.
```c
#include <a_samp>
```
Afterwards, we have the OnPlayerConnect callback in which I’ve used the SetPlayerCheckpoint function so that whenever a player connects to the server, a checkpoint will be created for them. The second, third and fourth arguments are the x, y and z coordinates for the checkpoint and the fifth argument is the size, which is also a float (decimal) value.
```c
public OnPlayerConnect (playerid)
{
    SetPlayerCheckpoint (playerid, 2158.4797, 943.1600, 10.8203, 1.0);
    return 1;
}
```
Following the above code is OnPlayerEnterCheckpoint, which contains the code for showing the weapons list (dialog) to the player.
```c
public OnPlayerEnterCheckpoint (playerid)
{
    ShowPlayerDialog (playerid, 1, DIALOG_STYLE_LIST, "Weapon Shop", "Desert Eagle (50$)\nAK-47 (150$)\nM4A1 (200$)", "Select", "Cancel");
return 1;
}
```
In the second argument indicates the Unique ID of the dialog, which is 1. Each dialog must have a separate Unique ID, otherwise the responses won’t be accurately returned and bugs can arise. The third argument is a predefined constant which is included in the ‘a_samp’ header, it represents the ID of the dialog style of type ‘simple list’. Fourth argument is the title while fifth contains the main content. There are three weapons in the list along with their prices stated in brackets. Each weapon is separated by ‘\n’ which is an Escape Sequence generally responsible for shifting the cursor to the next line but in this case (in list dialog) it creates next/new ‘list item’ which contains the text that follows.

* This topic is unfinished, i'm working on it *
