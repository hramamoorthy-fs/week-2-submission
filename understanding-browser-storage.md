Understanding and Exploring Browser Storage

 Step 1 – Core Concepts

1. What is the purpose of browser storage?
Browser storage allows websites to store data on a users device so that they can remember the information, improve performance, support offline while in the network down and provide the smooth experience without communicating with the server.

2. localStorage
Local storage is the browser storing mechanism and that stores as the key-pair values and keeps the data even the browser is closed. It is commonly used for the saving user preferences.
Size Limits: 5-10 MB
Common Use Cases:
User preferences (theme, language)
Saving application settings
Storing non-sensitive data

3. sessionStorage
Session storage is similar to the local storage but the storage mechanism it stores the data from the single tab or window but the data exists only in that tab remains open.
Size Limits: 5 MB
Common Use Cases:
Temporary form data
Multi-step form progress
Session-specific state

4. Cookies
Cookies are the small pieces of data stored in the browser that helps the websites remembers the users, manage sessions, authenticate users, save preferences. This is having the unique feature is that was it automatically included  in http request to a server 
Size Limits: 4 KB.
Security considerations:
Vulnerable to theft if not secured properly.
Use HttpOnly to prevent JavaScript access.
Use Secure to transmit only over HTTPS.
Use SameSite to reduce CSRF risks. 

5. IndexedDB
A client-side NoSQL database built into browsers.
When storing large amounts of structured data. It having the fast searching and handles large datasets much more efficiently.

Advantages over localStorage:
Much larger storage capacity
Supports indexing and searching
Handles complex objects
Asynchronous operations
Better performance for large datasets

6. Cache Api
The Cache api is a browser feature that allows the web applications to store the network requests and their responses locally in the browser
for example firstly you visiting any website the browser requests to download the files like index.html,any other files the downloaded files are stored in the cache and then u revisits that webpage the now the browser will not go the server instead of these browser will check to the cache.
advantage 
Faster loading improving performance
less network usage.

role in offline-first apps
new application : the user reading a new article the that articles and resources are now cached . Then u are in a offline the user opens the new application and it will display previously cached articles even without the internet we can accesible.

Step 2 – Practical Exploration

localstorage
localStorage.setItem("username", "Hari"); set command
localStorage.getItem("username"); get command
persits after refresh: yes
persit after browser close: yes

sessionstorage
sessionStorage.setItem("username", "Hari"); set command
sessionStorage.getItem("username"); get command
persits after refresh: yes
persit after browser close: no

cookies
document.cookie = "username=Hari"; set command
document.cookie ; get command
persits after refresh: yes
persit after browser close: depends on the expiry

IndexedDB
store.add({id:1,name:"Hari"}) ; set command
store.get(1) ; get command
persits after refresh: yes
persit after browser close: yes

Step 3 – Analysis

1. Which storage types persist across sessions?
The storage types persist across browser sessions are localstorage, IndexedDb, Cache Api and cookies with expiry date.
2. Which storage types are automatically sent to the server?
Cookies are only one browser storing mechanism that is automatically sent to the server.
3. Which storage type is most secure for sensitive information (and why)?
The most secure storage type for sensitive information is cookies is configured by the httponly, secure, samesite flags.
this helps to protect from the cross site scripting attacks and forgery 
Set-Cookie: sessionId=abc123; HttpOnly; Secure; SameSite=Strict
4. Which storage type is best for large datasets?
IndexedDb is the best for storing large datasets. Because it is designed for browser based db for structuring large datasets.
5. Which should be avoided for authentication tokens (and why)?
localstorage and sessionstorage are avoided for authentication token 
both storage are accesible through javascript. If a website becomes vulnerable or any attack or malicious attack can read the shared tokens and send them to a attacker.
Because of the risk the tokens are usually stored in secure httponly cookies for safety

Key Takeaways
Browser storage works like allow the websites to store the data locally on users device for improving performance, remembers user preferences.
Cookies(4kb) is automatically sent to the server, localStorage(5-10MB) persists across browser sessions, sessionStorage(5MB) only works in the current tab session, and IndexedDB for large datasets.
Sensitive data should be stored in the httponly cookies its is security concern and for efficient storage we can use indexedDb best for large datasets.

