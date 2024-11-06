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

### The benefits of using the interface
Let's say we do not use the interface. In any of the blueprint that is supposed to be interactable, we specifically create a function Named is intractable or not, And then it returns the true or false value.            Then in the blueprint of the character, when we press X. We checked in the radius of one meters, whether we hit some actor or not, We need to cast the actor to all of the related blueprint types, and then check whether it has a function name Intractable or not.  The reason that we need to CAST because not every actor have this function.  In this case, we make a lot of extra unnecessary works to check whether an object is Intractable or not.
## Animation
https://www.youtube.com/watch?v=etRZu5UG_S0&ab_channel=RyanLaley

In animation blueprints, The event graph will help To set up some values of some variables.

The animation graph will usually make use of those variables To determine whether we should change from some state to another state.
In the animation graph, we might have a lot of state machines. Each state machine could be called a locomotion. Inside these state machines, we might have a lot of states, such as idle, such as walking. Inside of these states, we can set the real animation player, Which seems also tied to one specific skeleton only.

One animation blueprint is usually bounded to only one skeleton mesh.   




## Using this keyword And also how to use instigator
https://www.youtube.com/watch?v=vSI0vs-fvu0&ab_channel=PobatoTutorials

The instigator LET the projectile know who create this projectile, so when dealing damage, we can trace back to who spawned this projectile.

