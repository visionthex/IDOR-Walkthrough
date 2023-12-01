# Corridor - IDOR Walkthrough

As you go through the site you can see that each door goes to a different room. But each room has a closed off room as shown.

No alt text provided for this image
Each room corresponds with a hash value like this: Starting from left to right.

 - Door 1: c4ca4238a0b923820dcc509a6f75849b
 - Door 2: c81e728d9d4c2f636f067f89cc14862c
 - Door 3: eccbc87e4b5ce2fe28308fd9f2a7baf3
 - Door 4: a87ff679a2f3e71d9181a67b7542122c
 - Door 5: e4da3b7fbbce2345d7772b0674a318d5
 - Door 6: 1679091c5a880faf6fb5e6087eb1b2dc
 - Center Door: 8f14e45fceea167a5a36dedd4bea2543
 - Door 8: c51ce410c124a10e0db5e4b97fc2af39
 - Door 9: c20ad4d76fe97759aa27a0c99bff6710
 - Door 10: 6512bd43d9caa6e02c990b0a82652dca
 - Door 11: d3d9446802a44259755d38e6d163e820
 - Door 12: 45c48cce2e2d7fbdea1afc51c7c6ad26
 - Door 13: c9f0f895fb98ab9159f51fd0297e236d

Now we have to figure out what this all means and what this information can be used for in a hacker mind set. We can try changing a character and see if we get any results on the webpage. Changing a couple characters on this string for example, `8f14e45fceea167a5a36dedd4bea2543` to `8f14e45fceea167a5a36dedd4bea2577` would respond with:

> Not Found - The requested URL was not found on the server. If you entered the URL manually, please check your spelling and try again. 

With this information we can see that adding random numbers to the string will not respond with anything interesting. If we are looking into the source code, we can see the same results.

No alt text provided for this image

No alt text provided for this image

The source code is still showing only a total of 13 doors as well. After digging around I was able to find this as well.

No alt text provided for this image

This was showing a SHA384 encryption. So maybe the rest of the doors are also using some sort of encryption method as well. Doing some Googleing on encryption and hashing. I was able to find this link here.

We can submit the hash values into the search bar in Hash Type Identifier and see what we come up with.

No alt text provided for this image

After finding out it is using a MD5 encryption we can start using that with the doors and see what the results would be. I was able to go back to the home page of Hashes.com and search my results for Door 13. The results came back with `c9f0f895fb98ab9159f51fd0297e236d:8`. This would mean that each door is using a MD5 encryption the result in a single digit. This would mean that each single digit would corresponds to an MD5 hash.

So, let's submit each door and see what numbers correspond to what MD5 hash.
 - Door 1: c4ca4238a0b923820dcc509a6f75849b:1
 - Door 2: c81e728d9d4c2f636f067f89cc14862c:2
 - Door 3: eccbc87e4b5ce2fe28308fd9f2a7baf3:3
 - Door 4: a87ff679a2f3e71d9181a67b7542122c:4
 - Door 5: e4da3b7fbbce2345d7772b0674a318d5:5
 - Door 6: 1679091c5a880faf6fb5e6087eb1b2dc:6
 - Center Door: 8f14e45fceea167a5a36dedd4bea2543:7
 - Door 8: c51ce410c124a10e0db5e4b97fc2af39:13
 - Door 9: c20ad4d76fe97759aa27a0c99bff6710:12
 - Door 10: 6512bd43d9caa6e02c990b0a82652dca:11
 - Door 11: d3d9446802a44259755d38e6d163e820:10
 - Door 12: 45c48cce2e2d7fbdea1afc51c7c6ad26:9
 - Door 13: c9f0f895fb98ab9159f51fd0297e236d:8

Now that we have done that the next this is to find out what number beyond 1 - 13 can we use to access a different room. The two numbers we can use is 14 and 0. We would need to add those numbers to a MD5 Hash in order to get their value. I would use the terminal on Linux in order to get a MD5 value with the string of values.

No alt text provided for this image

Now that we came up with the same hash value as Door 1 we can now use different values to see what MD5 Hash values we come up with like 0 and 14.

No alt text provided for this image

 - `cfcd208495d565ef66e7dff9f98764da:0`
 - `aab3238922bcc25a6f606eb525ffdc56:14`

Now that we have done that, we can test it against the site and see what we come up with.

No alt text provided for this image

I came back with a 404 not found message for room 14. Next, we will try room 0 and see what pops up.
No alt text provided for this image

We finally found the Flag for the room exercise. From here you would submit the flag and complete the room. This was a great exercise to learn at the same time be able to figure out how to do a write up for this room as well.

I would like to give thanks to John H. for created this room.

![tryhackme](https://tryhackme.com/room/corridor)
