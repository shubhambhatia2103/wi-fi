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

## Python3

```bash
# importing subprocess
import subprocess

# getting meta data
meta_data = subprocess.check_output(['netsh', 'wlan', 'show', 'profiles'])

# decoding meta data
data = meta_data.decode('utf-8', errors ="backslashreplace")

# splitting data by line by line
data = data.split('\n')

# creating a list of profiles
profiles = []

# traverse the data
for i in data:
	
	# find "All User Profile" in each item
	if "All User Profile" in i :
		
		# if found
		# split the item 
		i = i.split(":")
		
		# item at index 1 will be the wifi name
		i = i[1]
		
		# formatting the name
		# first and last character is use less
		i = i[1:-1]
		
		# appending the wifi name in the list
		profiles.append(i)
		

# printing heading	 
print("{:<30}| {:<}".format("Wi-Fi Name", "Password"))
print("----------------------------------------------")

# traversing the profiles	 
for i in profiles:
	
	# try catch block begins
	# try block
	try:
		# getting meta data with password using wifi name
		results = subprocess.check_output(['netsh', 'wlan', 'show', 'profile', i, 'key = clear'])
		
		# decoding and splitting data line by line
		results = results.decode('utf-8', errors ="backslashreplace")
		results = results.split('\n')
		
		# finding password from the result list
		results = [b.split(":")[1][1:-1] for b in results if "Key Content" in b]
		
		# if there is password it will print the pass word
		try:
			print("{:<30}| {:<}".format(i, results[0]))
		
		# else it will print blank in front of pass word
		except IndexError:
			print("{:<30}| {:<}".format(i, ""))
			
	
			
	# called when this process get failed
	except subprocess.CalledProcessError:
		print("Encoding Error Occurred")

```
