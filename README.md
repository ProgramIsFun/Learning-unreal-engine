- [Learning-unreal-engine](#learning-unreal-engine)
  * [The official Example of a First person CPP project In unreal engine, 5.2 .1.](#the-official-example-of-a-first-person-cpp-project-in-unreal-engine--52-1)
  * [The official Example of a First person CPP project In unreal engine, 5.2.1  Blueprint version](#the-official-example-of-a-first-person-cpp-project-in-unreal-engine--521--blueprint-version)
  * [C++ Delegates for Unreal Engine in 5 Minutes!](#c---delegates-for-unreal-engine-in-5-minutes-)
  * [blueprints Related delegates](#blueprints-related-delegates)
  * [UNREAL ENGINE | EVENT DISPATCHERS (BP) + DELEGATES (C++)](#unreal-engine---event-dispatchers--bp----delegates--c---)
  * [Event Dispatchers | Blueprint Communications | Unreal Engine 5 Tutorial](#event-dispatchers---blueprint-communications---unreal-engine-5-tutorial)
  * [How to use Blueprint Interfaces in Unreal Engine 5 in less than 3 minutes](#how-to-use-blueprint-interfaces-in-unreal-engine-5-in-less-than-3-minutes)
  * [Using this keyword And also how to use instigator](#using-this-keyword-and-also-how-to-use-instigator)

<small><i><a href='http://ecotrust-canada.github.io/markdown-toc/'>Table of contents generated with markdown-toc</a></i></small>

# Learning-unreal-engine 

##  Notice about redirectors when moving things or renaming things.
 
https://www.youtube.com/watch?v=mIf4tgg0aD8&ab_channel=Z-AxisUp
## Good tutorial about material editor
https://www.youtube.com/watch?v=FnycYhPiIt0&ab_channel=ChrisBromley

## Don't use too much Canvas panel.
It seems using only one campus panel is enough, using more will harm your frame rate.
https://www.youtube.com/watch?v=_A8b-WkJkxI&ab_channel=Spacemarine658  This example right here, he used only one canvas panel in the ferry outer layer, and all the insights could be overlay.
## 
each player is typically assigned a single PlayerController.  

One widgets will have only one owner, which is a player controller.

one player controller could only have one HUD   .    
## Notes when copying source code of the engine to your own usage.
UCLASS         GENERATED_BODY        Make sure these tools are used instead.    https://github.com/ProgramIsFun/ue5-force-graph/commit/5aa710133c03183c35286e194b8ab85e58b7eb5e
## Difference of micro and functions and blueprint.
Function are like functions in a programming language. Can be called from outside, has state, supports inheritance, but no latent nodes (like delays) are allowed.

Macro is like copy pasting your code. Can't be called from outside of the class, can't have state, inheritance, but can have latent nodes and you can make them execless or with multiple execs (exec is a white line with a triangle that connects nodes and defines flow). Note that you can't use macro in functions if macro contains latent nodes (because it's basically copy pasting and functions can't have latent nodes as stated above).
## https://github.com/CHPrado/first-person-shooter
Everything purely in blueprint.
Pretty good example and demo a very simple first person shooter.
In the character blueprint, when initialized ,  HUD will be created and added to the variable.
It deal with simple animations, Which is aiming or not aiming.
It deal with basic input actions because when we move left or right or aim at different directions.
It deal with some health counts AMMO count. and also some HUD usage.
When we want to change something in the HUD, we usually want to get the variable in the blueprint and then access some property within that variable and do Something like Set teXt.
It separates HUD into two blueprint. One is character XUD, another one is Game mode XUD. The former one display things related to characters such as health and ammo, The later one display some global things such as the announcement, which is the counter of the timer in warm up time, and also. the numbers of enemies, etc.

We could classify the project's materials into certain parts.   
- One is the Game mode blueprint. On every TICK it checked the section states on whether it is Warm up or playing, And update the timer Respectively by calling the function. The function is defined in itself.    In the function update warm up timer, Eventually, it will trigger the beginplay function.
  - In the beginplay function, it will first modify the ENUM variable, Which is the game section state.     And then it will retrieve the PAWN from global state, And then get the controller of this PAWN.  And then it will cast to Player controller, And then it will enable the input for that PAWN.  And then it will set the announcement of the widgets to be an empty text, which is originally used to display the countdown in the warm up time.
 
 
- One is the DROWN blueprint
  - In the blueprint, it has two severe surrounded, The lodge and the smaller one, and all of them has an uncollied event.
  - Events.
    - When begin play event kickstart we will bind the event on TAKE damage, And then it will run the PATLOL Micro.  This macro responsible for moving the drone toward different locations.
      - Two LATENT node is used. So this thing has to be a macro, but not a function.  One of them is to move Itself to a specific actor. When finished, it will continue the execution.     But one of them is the delayed node, which has continued the execution after one second.    
    - the large severe when it is collided, when with the user, then the BOT will start moving toward the player.
    - When the small severe collide with the player, then it will explode.  Which will play some sound and effects at the location of the player.  It will also apply damage and notice the node of applied damage only runs on the server.       And noticed when exploded, The drone blueprints will try to get the current game mode and cast it to the game mode that we are actually using.  it will triggered the function in The Game mode blueprint, which is the game mode. After the function is completed, it will destroy itself.
    - On TICK.  Although the ai will help us navigate the DROWN to walk the player, but we have to manually set the rotations so that the drone could be facing the player.
      




## https://github.com/everythingallaccount/Ultimate-CommonUI-Menu-System-Backup
Everything purely in blueprint.
A very good guide on I'm making a menu.
First of all, the map it default has a world override blueprint. Which override the game mode       

And also in this blueprint, it will set the player controller class to another blueprint.  

The player controller class will First of all trigger the begin play event in the apparent controller class, And then it will create the main ui when begin play is detected. Which is a widget class

Right now, there is still a lot of things that I don't understand. Maybe I could start from basics on how to create a widgets, how to push The widgets etc.



## How to avoid the engine adding starter content automatically?
[StartupActions]
bAddPacks=False
InsertPack=(PackSource="StarterContent.upack",PackName="StarterContent")

## How to delete the started Starter content in the correct way
First of all delete map.  And then the architecture.  And then SH, APE.   And then blueprint.  And then PROPS.  And then materials.  And then particle. 

## Static Mesh Component     Skeletal Mesh Components      
Static Mesh Component is the actual figure of a thing. It also cannot be animated. Skeletal Mesh Components can be animated.
## How to re-compile CPP
If any source file is changed, we need to recompile so that the engine could be notified.
live-coding Is one of the quick ways.  

https://forums.unrealengine.com/t/live-coding/763051

https://www.youtube.com/watch?v=QxBuQxaU-_k&ab_channel=techHow


## good Tutorials
https://www.youtube.com/@AliElZoheiry/videos
## The official Example of a First person CPP project In unreal engine, 5.2 .1.
In the pick up Blueprints that is put on the ground, 

Number1. UTP_WeaponComponent Is the root component of such a blueprint, Which details is implemented in CPP,    By the way, it inherits USkeletalMeshComponent.

Number2. And we have attached UTP_PickUpComponent Toward this root component. By the way, it inherits USphereComponent, Which inherits UShapeComponent, Which is usually could be considered to deal with the on overlap thing.

Because we want the player when it's step on the Number two, The character will pick up a weapon,
So in the beginplay function of the Number two in CPP implementation,  	OnComponentBeginOverlap.AddDynamic(this, &UTP_PickUpComponent::OnSphereBeginOverlap);     By the way,  OnComponentBeginOverlap Is a variable which is a Delegate type define in  Primitive component header. 

For the function OnSphereBeginOverlap Which receive a number of parameters, including what actors step on this thing.  In this function, We first cast the actor to see whether it is a character. If casting is Successful , OnPickUp.Broadcast(Character);  

So, in simple terms, We are binding a function OnSphereBeginOverlap To a OnComponentBeginOverlap Variable, which is a delegate that is defined in our Parent class. And we will broadcast a variable OnPickUp Which is a delegate type In this OnSphereBeginOverlap Function If the Actor that overlap with this component is a character. 

And where to receive this on pickup event.  There is actually in the blueprints that contain these two components.   For this event, because we broadcast it with the character.   So from the red node of this event, the character output Will be used to call the void AttachWeapon(Aue521fpscale37Character* TargetCharacter); Which is defined in our Number one component.  Because we have the pointer of that characters.      The number one component will call AttachToComponen(Which is a method defined in USceneComponent) To attach itself To the character USkeletalMeshComponent.     In the function  AttachWeapon, We also check the controller of the character, If it is a player controller, we also add a mapping contest class UInputMappingContext* FireMappingContext Which defined what physical button will trigger what intended action.     And we also add a mapping which Defined a specific action will trigger what function.
<img src="https://github.com/user-attachments/assets/38120233-cbc9-47e6-8c29-438ee254e356" width="700" >

A good thing to ask as ourself is When the attached weapon function of the number one component get called, it attach to the character actor.  Does it bring the number two component altogether? Or number two component Will now be the root component of that pick up rifle blueprint on the ground.


## The official Example of a First person CPP project In unreal engine, 5.2.1  Blueprint version

This works a little bit different.
The pick up blueprints Still contains number one component and number two component.    However, this time, the number one component is purely USkeletalMeshComponent. It does not contain any of our customization.

And in the Pick up blueprint. We have an overlapped event defined for number two component.
1. And if it is triggered
2. casting of the other Actor to character is successful
3. We set a variable To contain that character pointer.
4. And then we will attach a new blueprint object(BP_Weapon_Component), Which extent USkeletalMeshComponent,  To the Character that the pointer points to. And BP_Weapon_Component is another blueprint we define elsewhere. This is simply as saying that we want to create an object,BP_Weapon_Component, and attach to that character. The exact behavior on what to do Will be separately defined after the begin play event in BP_Weapon_Component.
5. Starting from this point, the things happened in a new blueprint, BP_Weapon_Component
6. When the new blueprint object is created and the begin play is triggered,
7. We find the owner Actor,
8. Trying to CAST to the character.
9. If successful, we store the character pointer in a variable.
10. We tried to READ. the mesh component variable Of the variable.
11. We call the attach component to component, The target Is SELF, The parent will be the variable we found in the previous step.
12. Has RIFLE variable Of the character to true,  This is because we want to change the animation of the character.
13. We try to get the controller of the character That's the character pointer points to.
14. Trying to CAST to player controller
15. Get the enhanced local player subsystem from the player controller.
16. Add a new mapping contest To the subsystem.  The mapping contests simply map those physical keys to a specific action.
17. If the action is fired,   Then we spawned the actor Offthe projectile and. play sound, etc.
    

We can see that in the cpp version, Inside the pickup Blueprint. the number one component is directly the cpp class that we customize. However, in this blueprint version start template, The number one component simply Serve The appearance. 




## C++ Delegates for Unreal Engine in 5 Minutes!
https://www.youtube.com/watch?v=FDc2jUiwFoc&ab_channel=PobatoTutorials
<img src="https://github.com/user-attachments/assets/afccbbef-ed14-446e-81f0-2b4010f1b418" width="700" >

If you want to bind a function to a delegate, write this in Cpp.
![image](https://github.com/user-attachments/assets/f1989b72-2d25-4e73-a9ce-964e1d2c441c)

## blueprints Related delegates
https://www.youtube.com/watch?v=PQ7NvNbcHtY&ab_channel=PobatoTutorials
 
![image](https://github.com/user-attachments/assets/45347113-3af3-436e-b963-163ad72129b1)

Use blueprint assignable if you want to react to this delegate inside blueprint.
Use blueprint callable if you want to trigger this Delegate

## UNREAL ENGINE | EVENT DISPATCHERS (BP) + DELEGATES (C++)
https://www.youtube.com/watch?v=OEmGbMEbqZo&t=12s&ab_channel=KITATUS

https://github.com/KITATUS/KFEventDispatchers
 
In the first example, pure blueprint is used.
In the second example, we have a CPP class for the pick up component and also the widget.  The TEST render component on the WALL is a blueprint.

In simple terms.  If we want to fire some events from some class. In that class, we'll define a variable which is a delegate TYPE.   The delegate type will be defined outside function using the MACRO.       For example, for the coined on the ground, we want to file an event on pickup when the user step on it. Let's call this pick up Class A. What we can do is Inside Class A.  	SphereComp->OnComponentBeginOverlap.AddDynamic(this, &AAKF_Pickup::OverlapStarted);  Which will file a function When the user step on one of the components of that class,  And in the function that is triggered, we broadcast the delegate. 	OnCoinPickup.Broadcast();             		And then for class B to be able to subscribe to this event.  We can use some function That will return a actor of a specific type, which Give us an act pointer, such as TempCoin.     Inside Class B, We write something like TempCoin->OnCoinPickup.AddDynamic(this, &UUW_CoinWidget_Base::CoinCollected);
             
 


## Event Dispatchers | Blueprint Communications | Unreal Engine 5 Tutorial
https://www.youtube.com/watch?v=5GYsTTcGGJo&ab_channel=BuvesaGameDevelopment


## How to use Blueprint Interfaces in Unreal Engine 5 in less than 3 minutes
https://www.youtube.com/watch?v=Ba_gEz229Wg&ab_channel=JoeyChimney

So basically we have a cube blueprint Called boost.  And a character blueprint.
What we want to achieve is when the character walk into the cube, It will be launched into the air.
So we first create a blueprint interface, And we create a function called boosting.
Then we go to the two blueprints that will use this interface, We click class settings and we implement the interface.

And then in the Boost, In the event that is preset in the event graph, which is called actor being overlapped,  We will trigger the action, which is the function in the interface as a message.   And there has to be an Target for such message, We simply find the character class and let it be the target.

And then in the character blueprint, We will add a Event node which will present the interface event, And we will launch the characters If this Events happens. 
## Interface.
https://www.youtube.com/watch?v=EQfml2D9hwE&ab_channel=AliElzoheiry
Basically, we can define a interface Blueprints, By setting some function name and also the input and output. For example, a function name interact.
Then we go to all the Blueprints that should be Intractable, And in the right side menu, we Signal that this blueprint will. implement the Interface By clicking the button.   And then we should implement what it should does when the event interact happened. 

Because this interface thing must be dispatched somewhere,  Let's say a character when The bottom X is pressed. We check in the radius of one meters, if there are any objects that Has implemented the interact interface, If true, we dispatch this interface.


The benefits of using the interface

Let's say we do not use the interface. In any of the blueprint that is supposed to be interactable, we specifically create a function Named is intractable or not, And then it returns the true or false value.            Then in the blueprint of the character, when we press X. We checked in the radius of one meters, whether we hit some actor or not, We need to cast the actor to all of the related blueprint types, and then check whether it has a function name Intractable or not.  The reason that we need to CAST because not every actor have this function.  In this case, we make a lot of extra unnecessary works to check whether an object is Intractable or not.

In the image down below left and right, The Red Node Represent same events.   They both represent that there is an event dispatcher call on death, defined in that component. And the red node event represents. that dispatcher has indeed been dispatched.       But the right side style, which consists of three nodes. Has an advantage, which is we can actually unbind events
![image](https://github.com/user-attachments/assets/188c4399-9677-4a9d-a340-83d67b42b689)

The similarity of EVENT dispatchers and interface. They are all shouts Something to somewhere. For event dispatchers, We do not need to care who has listen to this event.  However, if we Use interface. We assume that something has implemented this interface.       So I would say that the event dispatcher method give us more freedom, because we are not forced to implement the interface for something that has to be responsible to the event. We simply needed to define the on events of that specific class that invoke the event dispatchers.


## Animation
https://www.youtube.com/watch?v=etRZu5UG_S0&ab_channel=RyanLaley


In animation blueprints, The event graph will help To set up some values of some variables.

The animation graph will usually make use of those variables To determine whether we should change from some state to another state.
In the animation graph, we might have a lot of state machines. Each state machine could be called a locomotion. Inside these state machines, we might have a lot of states, such as idle, such as walking. Inside of these states, we can set the real animation player, Which seems also tied to one specific skeleton only.

One animation blueprint is usually bounded to only one skeleton mesh.   




## Using this keyword And also how to use instigator
https://www.youtube.com/watch?v=vSI0vs-fvu0&ab_channel=PobatoTutorials

The instigator LET the projectile know who create this projectile, so when dealing damage, we can trace back to who spawned this projectile.

