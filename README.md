# no_code
Most of the programs on this list will be either on-going projects for research mentors or partially written projects. Without further ado, feel free to check out the documentation I've written below.

# N-Body Simulation (Leapfrog Integration)

### What is it?

A bunch of different code that all works together to do gravitational simulations. Since physics can simulate future events (and past events, given the right conditions), a simulation can be written to determine future positions and velocities of objects in space.

This code is split into multiple parts, but the most impressive is the visualization, which can be seen below. The visualization can run in real-time. (The data can also be calculated in parallel with the visualization, but it doesn't run as quickly and makes the code less accessible.)
![About 200 gravitational bodies](http://i.imgur.com/9QzrtuL.png)

### Why is the source not shared?

This is an on-going project with [Laura Sales](http://www.physics.ucr.edu/people/faculty/sales.html) and [Peter Creasey](http://astro.ucr.edu/members/postdocs/) at UCR. The code is going under significant changes at the moment and the project is not complete. The source will likely be shared at the completion of the project.

### How was it written?

[Processing](https://processing.org/) is an extremely nice program, which makes visual work much more intuitive. For part of the project, the N-Body code was written in [processing.py](http://py.processing.org/), which is a variant of Processing that uses Jython to push the Python code to Java. However, this approach has been moved away from, and the numerical portion has been put into a separate Python program. The numerical portion outputs text files, which are then read by a visualizer written in Processing (Java). For camera movement and overall interactiveness, the program uses [peasycam](http://mrfeinberg.com/peasycam/).

The numerical code is based around [Leapfrog integration](https://en.wikipedia.org/wiki/Leapfrog_integration), which is a second-order method of simulating future events. The integration method is sympletic, which means time can run in the opposite direction and it will still work properly (as long as the timestep is constant).

# [Orbach Library](https://library.ucr.edu/libraries/orbach-science-library) Room Reservations

### What is it?

A piece of code that automatically reserves study rooms at Orbach Library at UCR. It takes approximately 17 seconds per room reservation. This is especially useful during finals week, since it basically ensures we have a room.

### Why is the source not shared?

There are approximately 25 rooms open for reservation at Orbach. They are open from 8:00AM to 12:00AM most days, which means there are 16 hours to work with. The maximum amount of time one can reserve a room is 3 hours. Therefore, approximately 5 reservations could reserve a room for a full day. 5\*25 = 125, which is the maximum number of people who can have this code before the Orbach room reservation system is completely deadlocked (assuming everyone reserves the maximum time each day). There are 21,539 students at UCR. Sharing the source would almost certainly result in reservation deadlock.

### How was it written?

This program was written in [selenium](http://www.seleniumhq.org/), so it takes arguments such as the room number, last name, preferred room and times, and phone number and then does the reservation itself. I can send a command to it like this:
```
reserve(<librarycardnumber>, <lastname>, <preferred_time>, <preferred_rooms>, <phonenumber>)
```
It's fairly input tolerant, allowing for strings or arrays, and if the values are arrays, it will iterate over them.

Once the reservation is done, it will output this:
```
Reserved Room <no> at <time>,
Using <name>'s card, with number <librarycardnumber>
```
Running the code requires the use of a browser (since selenium is built for browser automation). This code was written using [ChromeDriver](https://sites.google.com/a/chromium.org/chromedriver/).
