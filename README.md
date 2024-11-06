# Learning-unreal-engine

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





## Using this keyword And also how to use instigator
https://www.youtube.com/watch?v=vSI0vs-fvu0&ab_channel=PobatoTutorials

The instigator LET the projectile know who create this projectile, so when dealing damage, we can trace back to who spawned this projectile.

