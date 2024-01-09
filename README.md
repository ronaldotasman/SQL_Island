# SQL Island

SQL Island is a text-adventure game to learn the database language SQL.<br />
This site you can be found [here](https://sql-island.informatik.uni-kl.de/).

✨ This my [Certificate](http://sql-island.cs.uni-kl.de/cert.php?id=1e9ae14b90) of Completion you can be found ! ✨
<br />
<br />
### The QUESTION and ANSWER

Q : It seems there are a few people living in these villages. How can I see a list of all inhabitants?<br />
A : ```SELECT * FROM inhabitant;```
<br />

Q : Thank you, Edward! Okay, let's see who is friendly on this island...<br />
A : ```SELECT * FROM inhabitant WHERE state = 'friendly';```
<br />

Q : There is no way around getting a sword for myself. I will now try to find a friendly weaponsmith to forge me one. (Hint: You can combine predicates in the WHERE clause with AND)<br />
A : ```SELECT * FROM inhabitant WHERE state = 'friendly' AND job = 'weaponsmith';```
<br />

Q : Oh, that does not look good. Maybe other friendly smiths can help you out, e.g. a blacksmith. Try out: job LIKE '%smith' to find all inhabitants whose job ends with 'smith' (% is a wildcard for any number of characters).<br />
A : ```SELECT * FROM inhabitant WHERE state = 'friendly' AND job LIKE '%smith';```
<br />

Q : No need to call me stranger! What's my personid? (Hint: In former queries, the * stands for: all columns. Instead of the star, you can also address one or more columns (seperated by a comma) and you will only get the columns you need.)<br />
A : ```SELECT personid FROM inhabitant WHERE name = 'Stranger';```
<br />

Q : I can offer to make you a sword for 150 gold. That's the cheapest you will find! How much gold do you have?<br />
A : ```SELECT gold FROM inhabitant WHERE name = 'Stranger';```
<br />

Q : Damn! No mon, no fun. There has to be another option to earn gold other than going to work. Maybe I could collect ownerless items and sell them! Can I make a list of all items that don't belong to anyone? (Hint: You can recognize ownerless items by: WHERE owner IS NULL)<br />
A : ```SELECT * FROM item WHERE owner IS NULL;```
<br />

Q : Do you know a trick how to collect all the ownerless items?<br />
A : ```UPDATE item SET owner = 20 WHERE owner IS NULL;```
<br />

Q : Now list all of the items I have!<br />
A : ```SELECT * FROM item WHERE owner = 20;```
<br />

Q : Find a friendly inhabitant who is either a dealer or a merchant. Maybe they want to buy some of my items. (Hint: When you use both AND and OR, don't forget to put brackets correctly!)<br />
A : ```SELECT * FROM inhabitant WHERE state = 'friendly' AND job = 'dealer' OR job = 'merchant';```
<br />

Q : I'd like to get the ring and the teapot. The rest is nothing but scrap. Please give me the two items. My personid is 15.<br />
A : ```UPDATE item SET owner = 15 WHERE item = 'ring' OR item = 'teapot';```
<br />

Q : Unfortunately, that's not enough gold to buy a sword. Seems like I do have to work after all. Maybe it's not a bad idea to change my name from Stranger to my real name before I will apply for a job.<br />
A : ```UPDATE inhabitant SET name = 'Ronaldo Tasman, S.Kom' WHERE personid = 20;```
(NOTES : You can write your real name for your Certificate)
<br />

Q : Since baking is one of my hobbies, why not find a baker who I can work for? (Hint: List all bakers and use 'ORDER BY gold' to sort the results. 'ORDER BY gold DESC' is even better because then the richest baker is on top.)<br />
A : ```SELECT * FROM inhabitant WHERE job = 'baker' ORDER BY gold DESC;```
<br />

Q : Is there a pilot on this island by any chance? He could fly me home.<br />
A : ```SELECT * FROM inhabitant WHERE job = 'pilot';```
<br />

Q : Thanks for the hint! I can use the join to find out the chief's name of the village Onionville. (Hint: In the column 'chief' in the village table, the personid of the chief is stored)<br />
A : ```SELECT inhabitant.name FROM village, inhabitant WHERE chief = personid AND village.name = 'Onionville';```
<br />

Q : Hello Ronaldo Tasman, S.Kom, the pilot is held captive by Dirty Dieter in his sister's house. Shall I tell you how many women there are in Onionville? Nah, you can figure it out by yourself! (Hint: Women show up as gender = 'f')<br />
A : SELECT COUNT(*) FROM inhabitant WHERE gender = 'f' AND personid = 3;
<br />

Q : Oh, only one woman. What's her name?<br />
A : ```SELECT name FROM inhabitant WHERE gender = 'f' AND villageid = 3;```
<br />

Q : Oh no, baking bread alone can't solve my problems. If I continue working and selling items though, I could earn more gold than the worth of gold inventories of all bakers, dealers and merchants together. How much gold is that?<br />
A : ```SELECT SUM(gold) FROM inhabitant WHERE job = 'baker' OR job = 'dealer' OR job = 'merchant';```
<br />

Q : Very interesting: For some reason, butchers own the most gold. How much gold do different inhabitants have on average, depending on their state (friendly, ...)?<br />
A : ```SELECT state, AVG(gold) FROM inhabitant GROUP BY state;```
<br />

Q : Heeeey! Now I'm very angry! What will you do next, Ronaldo Tasman, S.Kom?<br />
A : ```DELETE FROM inhabitant WHERE name = 'Dirty Diane';```
<br />

Q : Yeah! Now I release the pilot!<br />
A : ```UPDATE inhabitant SET state = 'friendly' WHERE personid = 8;```
<br />
<br />
##### THE GAME IS OVER !
Hope it can help you in your learning, and thank you.
