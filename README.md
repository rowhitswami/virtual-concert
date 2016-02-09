Virtual Concert - Visualizing Music in VR

This is my first mini-project for a Virtual Reality course, a demo can be found here: http://cs.brandeis.edu/~arya/vr 

As well as being a Computer Science major, I am also studying Music and have taken many courses on Electronic Music, so I wanted my project to be a melding of the two diciplines. I wanted to take the act of listening to music and make it an immersive experience, so that someone could see the patterns happening, not just listen to the music.

I started out first by looking into Unity, but the project looked like it would be more adapted to WebGL, so I looked out for tutorials on the subject.

The first step was finding some way to get particles on the screen to manipulate visualization. I came across this tutorial for vizualising weather data from an API, and it was a great way to get started: http://www.sitepoint.com/bringing-vr-to-web-google-cardboard-three-js

A lot of time for me was spent analyzing the code, as I was unfamiliar with Javascript, and how a lot of it is asyncronous, with different functions running at the same time.

After I got familiar with that, I needed to modify the code so that instead of vizualizing the weather, it would show data for the music. I started by gutting out everything involving the API calls, and abstracting a lot of the features so that the code wouldn't break. Later I will go back and make the code cleaner, but this is just a demo.

After that, I needed to get the music playing at the same time as the audio. Just playing the audio wouldn't work, as there was some lag involved. I tried many things (including many placements of the line of code to play the audio), but it seemed like either the graphics would start before the audio or vice versa.

I then decided to try to get the actual time from the WebGL code - with little tinkering I was able to display the running time where the city name was previously displayed. Using this time, I tried to sync up the animation with the music, before finding these tutorials on music processing in Javascript:

http://www.patrick-wied.at/blog/how-to-create-audio-visualizations-with-javascript-html

https://www.bignerdranch.com/blog/music-visualization-with-d3-js/

At this point, I looked into these libraries, which do a FFT (fast fourier transform) on the music. And the amazing thing is that they line up exactly with the code! Because the code is interconnected with the music, this allowed me to just start the animation when the music was loaded!

The FFT allows me to query for the frequencies at any point in time, something that would be perfect for displaying. I decided to map the FFT to the color of the particles, as I was using electronic music and it seemed fitting.

After doing the FFT, I found out how to modify the values of the particles to change continuously. The problem with the weather system is that the data is static, so it didn't change over time. Eventually I found out how to change the animation constantly without too much lag, leading to the effects that are found now.

Things to do:

The big problem now is that I can't get it to load on mobile browsers, which sort of defeats the point. I am actively looking for help in fixing the issue, however. 

I also need to fine tune the values of the FFT, to make sure they map correctly to the RGB values of the particles - I have a suspicion now that some data is being lost.