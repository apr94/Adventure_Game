#!/bin/bash

health=25
damage=0
has_key=false
visited_dungeon=false
visited_vault=false
has_potion=false
current_loc=forest
loc_exists=false
monster=""
objective="  1.) Find a student from Slytherin and grab some of his hair. []"
objective2=" 2.) Find the polyjuice potion."
objective3=" 3.) Find and destroy the horcrux."

echo "--Please enter your name: "
read name

echo "--Welcome to Hogwarts, $name. It is upto you now, at the eleventh hour to find the one last horcrux that remains. You will need to find it and destroy it to finish Voldemort once and for all. Are you ready to do what it takes?"

echo "--Hint: Enter y for yes or n for no"

while true
do
read yesno

case $yesno in

 y) echo "--A brave choice. Here is your wand, use it wisely..." 
    break ;;
 n) echo "--I always though that yer a wizard $name! Guess I was wrong. Escape with your invisibility cloak while the rest of us die..."

echo "--GAME OVER"
         exit 0 ;;
 *) echo Please answer with y/n.;;

esac
done

echo "--Your current location is the $current_loc. You can find out about your location by typing loc. You can move about by typing mov <location>"
echo "--Be careful. There are creatures of pure evil lurking in the hallways of Hogwarts. Should you duel them and die..."

while true

do

echo "--Enter command:"

read command location

case $command in

map) echo "--Here is the map of Hogwarts: "
     cat map ;;

loc) echo "--Your current location is the $current_loc." ;;

health) echo "--Your current health is $health points." ;;

mov) loc_exists=false
     for i in "$current_loc"/*;
     do 
     if [ "$current_loc/$location" == "$i" ]; then
     loc_exists=true
     fi
     done

     if [ "$loc_exists" == "true" ]; then

case $location in

underwater) 


 if [ "$has_potion" == "true" ]; then
current_loc=$location
echo "--You are now in the $location"
echo "--At long last you have entered the very room where the last of voldemert remains. You look around for a horcrux, when you notice that Voldemort himself is present!"
echo " "
echo "Voldermort: At long last we meet, $name. There is no horcrux, it was just a ruse to trap you!"
echo "$name: " 
read answer
echo "Voldermort: Ha, I knew you would say that, $name. But such things dont matter anymore, for I am going to kill you myself right now."
echo "--Voldemort is about to kill you. What will you do: run or fight?"

read action

case $action in 

run)
echo "--Voldemort rushes towards you. After being scared out of your wits, you drop the container and run away. Suddenly you notice a big thud. You look back and see Voldemort lying on the ground, withering in pain. He had slipped on the glass container that you had dropped."
echo " "
echo "Voldemort: I..will...kill.....y"
echo "--And with those words, Voldemort breathed his last. Who would have thought that a glass container could have kiiled the Dark Lord?"
echo " "
echo "--You have completed the quest successfully, $name. People for generations will be talking about your bravery and magical capabilities!"
echo "----GAME OVER----"
break;;   

fight) echo "--Voldemort uses Avada Kedavara on you. It was super, super effective because you are now dead. What were you thinking?"
echo "---GAME OVER"
exit 0;;

*) echo "--Enter a valid action."

esac

else echo "--You do not look like a Slytherin yet! Use some polyjuice potion."
fi;;

vault) 
  
echo "--You are now in the $location"
  
echo " "

for i in "$current_loc/$location"/*;
     do 
     damage=$(<"$i")
     monster=$(echo $i | cut -f3 -d/)
     done
     health=$(( health-damage ))
     echo "--Oh no, you have been attacted by a $monster! You have taken a damage of $damage points. Your new health is $health."

if [ "$health" -le 1 ]; then  
echo "You have lost all of your health and are dead. You have doomed all of wizarddom, but it is no big deal.."
break
fi

current_loc=$location

if [ "$visited_vault" == "false" ]; then

echo "--However you have found Malfoy in the Gryffindor vault! You will need to stun him and obtain one his hairs!"
echo "-- Get ready! Malfoy used the spell reducto on you! What spell will you use to protect yourself?"


read spell

case $spell in 

protego) echo "You used Protego! It was super effective! Malfoy's spell has rebounded against your shield and has temporarily stunned him. Now is the time to act! Try to stun malfoy unconcious.";;

*) echo "You needed to protect yourself, $name! Malfoy's spell has taken away all your health. So much for defeating the Dark Lord.."
exit 0;;

esac

while true 
do

read spell

case $spell in 

stupefy) echo "--You have stunned Malfoy! Now you can get a strand of his hair. Enter the spell to get some hair!"
break;;
*) echo "--You need to use the command to stun Malfoy! Hurry!" ;;

esac
done


while true
do 

read spell object

case $spell in

accio) case $object in

hair) echo "--You have got some hair of Malfoy! Now you can use your polyjuice potion...but first, you have to find it..."
                   echo "--Furthermore, you also got what you *really* came for: a case of firewhiskey! Your health now stands at 100 points!"
                   health=100
                   visited_vault=true
                   objective="  1.) Find a student from Slytherin and grab some of his hair. [x]"`echo -e "\n "` 
                   objective=$objective" 2.) Find the polyjuice potion. []"
                   break;;

*) echo "--What do you need $object for? Get some hair and fast" ;;
esac;;

*) echo "--You need to use the command to get some Hair! Hurry!" ;;

esac

done

fi ;;

dungeon) 

echo " "

for i in "$current_loc/$location"/*;
     do 
     damage=$(<"$i")
     monster=$(echo $i | cut -f3 -d/)
     done
     health=$(( health-damage ))
     echo "--Oh no, you have been attacted by a $monster! You have taken a damage of $damage points. Your new health is $health."
     
if [ "$health" -le 1 ]; then  
echo "You have lost all of your health and are dead. You have doomed all of wizarddom, but it is no big deal.."
break
fi

   current_loc=$location
     echo "--You are now in the $location"
if [ "$visited_dungeon" == "false" ]; then

echo "--The polyjuice potion is here somewhere among all these bottles. It there was only some spell to get it in an instant..."

while true
do 

read spell object

case $spell in

accio) case $object in

polyjuice) 

echo "--Finally in your hand you grasp container with the slimey greek liquid. After adding Malfoy's hair, you gulp it down in one go. It takes likes earwax, but you relish the taste. Then, you stare at yourself in the mirror. You have become...Malfoy. You carry the container of the potion with you. It is not Gryffindor's sword, but it might come in handy..."
                   
                   
                   visited_dungeon=true
                   has_potion=true
                   objective=$objective`echo -e "\n "` 
                   objective=$objective" 3.) Find and destroy the horcrux."

                   objective="  1.) Find a student from Slytherin and grab some of his hair. [x]"`echo -e "\n "` 
                   objective=$objective" 2.) Find the polyjuice potion. [X]"`echo -e "\n "`
                   objective=$objective" 3.) Find and destroy the horcrux. []"
                   break;;

*) echo "--What do you need $object for? Get the polyjuice potion and fast" ;;
esac;;

*) echo "--You need to use the command to get the potion! Hurry!" ;;

esac

done

fi ;;

*)   for i in "$current_loc/$location"/*;
     do 
     damage=$(<"$i")
     monster=$(echo $i | cut -f3 -d/)
     done
     health=$(( health-damage ))
     echo "--Oh no, you have been attacted by a $monster! You have taken a damage of $damage points. Your new health is $health."

if [ "$health" -le 1 ]; then  
echo "--You have lost all of your health and are dead. You have doomed all of wizarddom, but no big deal.."
echo "----GAME OVER"
break
fi

current_loc=$location
     echo "--You are now in the $location"

esac
     else echo "--Location not found"
     fi;;

pos) echo "--You can move to the following locations:"
     for i in "$current_loc"/*;
     do 
     posloc=$(echo $i | cut -f2 -d/)
     echo $posloc
     done ;;
 
   
obj) echo "--Voldemort's last horcrux is located in his one true home: The Slytherin's commonroom under the lake. But before you can enter the commonroom, you must tranform into a Slytherin using the polyjuice potion. But to use the potion, you will need hair from a student from Slytherin..."
echo "$objective" ;;
quit) echo "--You will return, won't you $name? Or will you leave us all in the mercy of the Dark Lord?" 
      exit 0 ;;
*) echo "--No such command exists" ;;
esac
done
