# Let's see wifi password using python
Normally, in order to access a network when connecting to WiFi, we have to provide a password. However, we are unable to view the password we have previously entered, which is the password of the network that has been kept. In this Repo, we will look at how to use Python's subprocess module to get all saved WiFi names and passwords.
Wi-Fi is a wireless networking technology that makes it possible for mobile devices, wearables, laptops, and desktop computers to connect to the Internet.
By creating new processes, the subprocess module in Python (both 2.x and 3.x) is used to run extra programmes or applications that use Python code. Getting the input, output, error, and exit codes for different commands is also helpful.


## Steps for Implementation :
1. Import the subprocess module 
2. Get the metadata of the wlan(wifi) with the help of check_output method 
3. Decode the metadata and split the meta data according to the line 
4. From the decoded metadata get the names of the saved wlan networks 
5. Now for each name again get the metadata of wlan according to the name 
6. Start try and catch block and inside the try block, decode and split this metadata and get the password of the given wifi name 
7. Print the password and the wifi name and print blank if there is no password 
8. In except block if process error occurred print encoding error occurred 

## Contact

[<img target="_blank" src="https://img.icons8.com/bubbles/100/000000/linkedin.png" title="LinkedIn">](https://www.linkedin.com/in/shubhambhatia2103/) [<img target="_blank" src="https://img.icons8.com/bubbles/100/000000/github.png" title="Github">](https://github.com/shubhambhatia2103) [<img target="_blank" src="https://img.icons8.com/bubbles/100/000000/instagram-new.png" title="Instagram">](https://instagram.com/6eingshubham) [<img target="_blank" src="https://img.icons8.com/bubbles/100/000000/twitter-squared.png" title="Twitter">](https://twitter.com/whoodattboyy)
