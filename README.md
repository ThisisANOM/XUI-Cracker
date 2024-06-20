# x-ui Cracker
x-ui Cracker is a tool for cracking x-ui panels using a list of URLs, usernames, and passwords. It can be used to automate the process of testing multiple combinations of credentials against multiple URLs.

## Features
- Crack x-ui panels using a list of URLs, usernames, and passwords.
- Supports reading credentials from files.
- Saves successful login attempts to a file.
- Color-coded output for better readability.
## Requirements
- Python 3.x
- colorama library (install using pip install colorama)
## Usage
To run the script with default settings:

```
python x-ui.py -lf urls.txt
```
This will use default credentials (admin as username and admin as password) and test them against the URLs listed in urls.txt.

## Advanced Usage
To specify custom usernames and passwords files:

```
python x-ui.py -lf urls.txt -uf usernames.txt -pf passwords.txt
```
This will use the usernames and passwords listed in usernames.txt and passwords.txt respectively.

## Uncovering Default Credentials in V2ray system
Widespread filtering in countries like Iran leads many to use V2Ray servers. However, insecure configurations with default credentials make them easily exploitable, posing risks to user privacy
information gathering
To begin our journey in locating these panels, we require essential information about the panels themselves and their common traits. Identifying these patterns aids in their easy discovery across the internet.I've started exploring panels, and along the way, I stumbled upon several Telegram channels dedicated to sharing configurations for this v2ray system. Now, I'm on a quest to uncover something truly unique within these configurations.Here's what I've discovered

```
<a-form-item> <a-row justify="center" class="centered"> <div style="height: 50px;" class="wave-btn-bg wave-btn-bg-cl" :style="loading ? { width: '52px' } : { display: 'inline-block' }"> <a-button class="ant-btn-primary-login" type="primary" :loading="loading" @click="login" :icon="loading ? 'poweroff' : undefined"> [[ loading ? '' : 'Log In' ]] </a-button>
```
as you can see there is a string in the panel html soruce so i try to make a dork for it and here is the result of that dork 
```
body="[[ loading ? '' : 'Log In' ]]" && country="IR"
```
Now, we have the ability to utilize search engines such as Shodan, Fofa, and others to locate these panels on the internet.
![image](https://github.com/ThisisANOM/XUI-Cracker/assets/143174378/c7997946-d332-4dce-9e4c-68b233a870d8)
Result of FOFA search

We found 885 results that we can work on to test for default credentials, but wait, surely there are more of these panels. Why not try to find all of them to achieve better results?
Trying to find more : 
As you can see, the FOFA search engine provides us with the ability to search using icon hashes. So, why not test this functionality as well? here is the dork we use 

```
icon_hash="-1940576803" && country="IR"
```
![image](https://github.com/ThisisANOM/XUI-Cracker/assets/143174378/e46a103e-f667-4e8d-85c3-41958ef144b5)
shodan

![image](https://github.com/ThisisANOM/XUI-Cracker/assets/143174378/d1270770-1bd9-475c-8a82-ee011abca298)

