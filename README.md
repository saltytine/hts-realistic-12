# another lil writeup of hts realistic 12  
this one was pretty easy  

The lil blurb that tells us what to do  
![image](https://github.com/user-attachments/assets/4a1730fe-8292-4807-8c33-1491ae3e5144)

This is the main page  
![image](https://github.com/user-attachments/assets/40756c65-4257-4165-9ba0-b3d5c524ca50)
Where there are 3 other main pages:  
Teacher Pages  
![image](https://github.com/user-attachments/assets/304075d8-90c7-4ddd-8f2d-ab989717116e)  
Student Work  
![image](https://github.com/user-attachments/assets/70bdf408-d7b1-4edd-adb4-00791698961a)  
And Testing Scores  
![image](https://github.com/user-attachments/assets/60358486-539d-4fbf-8bbf-5b756bc854c0)  
Just like realistic 11, it says pl in the search bar  
![image](https://github.com/user-attachments/assets/7d3bbb27-1380-48f9-8c22-db9c5af8e7b2)  
Which means more pearl  
If you enter pretty much anything into the web browser this page pops up  
![image](https://github.com/user-attachments/assets/e4674d58-3a55-4ae4-9d69-2782d15f604a)  
Thing is, browsers have more than an http protocol (which is the default when loading in), they have a file protocol  
We know its running on a win95 computer because OutThere said so, so if you stick this thing in:  
![image](https://github.com/user-attachments/assets/c7ceec6d-0a3c-4755-b0a8-8df5328414ca)  
You get the files on the windows computer  
![image](https://github.com/user-attachments/assets/480931eb-90e8-448e-9889-30ae8dd94cdf)  
The website is whats most important so we can go in the web folder  
![image](https://github.com/user-attachments/assets/3724b7f0-399e-4032-850c-a9f55a6f8775)  
I tried opening a few of the folders, cgi-bin and Perl were blocked, HTML was fine  
![image](https://github.com/user-attachments/assets/6db908df-93f2-4262-bf4f-3dd85f63c857)  
Whats interesting here is `heartlandadminpanel.html`, which if you stick in the url:  
![image](https://github.com/user-attachments/assets/44924131-9482-4455-bd42-0336c0001b9d)  
Gives you a very blank screen with a very small login thingie  
![image](https://github.com/user-attachments/assets/c35397e5-95ee-4707-ba45-55e45fab5e29)  
I tried random passwords for a little bit and sql injections but wasn't workin  
Looked in the page source and found smth interesting though  
![image](https://github.com/user-attachments/assets/cfa8d5c3-e798-4d58-a961-d8ef68329323)  
Tis sending a get request to `cgi-bin/heartlandadminpanel.pl`  
Can't get into it directly, so i spent a good chunk of time looking through all the pages  
Even Mr. Englebert (Humperdink)  
![image](https://github.com/user-attachments/assets/fa08062c-29e1-4308-bfb5-1b355c20d82b)  
Then I found Joey Simmons' page, who asked me to sign his "guestook"  
![image](https://github.com/user-attachments/assets/effbba19-dc6a-42a9-85b8-fcd0803f876a)  
Which looked pretty exploitable  
I tried to send a slur but it showed this error :<  
![image](https://github.com/user-attachments/assets/c92a963f-65c7-4ac2-a885-9d33a7a07f18)  
Looking at the page source we can see that its writing to some guest file  
![image](https://github.com/user-attachments/assets/a9a70f84-7f98-4366-a38f-52f26376e461)  
Given that this may be one of the worst websites ever made, if this thing can write it can probably read  
If we call the `guest.pl` script with the read function and point it to `heartlandadminpanel.pl` we can (in theory) read what is in `heartlandadminpanel.pl` and (in theory) get the creds for the admin panel in there  
![image](https://github.com/user-attachments/assets/1a82fb86-3eeb-4cc3-ab43-e8a6ba8caa31)  
And that takes us to  
![image](https://github.com/user-attachments/assets/a63ba925-1252-4168-b282-e7ceb45457c9)  
Wonderfully for us, the user and pass are hardcoded into the source, *twice*  
![image](https://github.com/user-attachments/assets/49626667-56eb-4495-97f3-0a6ee78ca24d)  
Stick it in the admin panel:  
![image](https://github.com/user-attachments/assets/f77a2973-e6c3-4b24-94b4-60d27f8d74c9)  
Which takes you to a page for managing all restrictions:  
![image](https://github.com/user-attachments/assets/eceb9acf-98c3-46de-9240-38fa4a4a0a3c)  
Just clear all and you are done  
![image](https://github.com/user-attachments/assets/abad4185-f35a-417a-9c9b-629d4378aa5a)  
