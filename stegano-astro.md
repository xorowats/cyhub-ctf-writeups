# Astro Stegano

This was one of the easier challanges.
If we look at the hint, the only reference to an astronauts is the CTF banner. Lets take a look at the ctf website.
Could'nt seem to find the banner image in the html sources so I took a look at whats beeing loaded in the developer tools network tab, and here it was.
![Banner](images/ss1.PNG?raw=true "ss1")

Let's download the image and see if there's anything hidden inside. We can do this with binwalk.
![Banner](images/ss2.PNG?raw=true "ss2")

We can see that there's a zip file inside the png and it has a flag.txt file inside. We can extract the files found inside the png with -e option of binwalk.
![Banner](images/ss3.PNG?raw=true "ss3")

Now we can cat the file and see if we get the flag.
![Banner](images/ss4.PNG?raw=true "ss4")

Yup, there it is
