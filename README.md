**Note:** Please do not fork this repository. Just clone it.

# Overview

This purpose of this exercise is to recreate part of a service we currently have in our production systems. It is to help you get your hands dirty with tasks we've had to tackle before (in a reasonable amount of take-home time) and it is for us to understand your ability to bring requirements to life with code.


# Background

Because Resolve is a VR application we have to work in 3D dimensions when creating interfaces for customer interaction. Our buttons, lists, etc. have dimension to help our customers easily explore content in an immersive environment. We also have to deal with large amounts of cloud data that is fetched from web servers dynamically and populate the Unity scene at runtime. The challenges with new features don't end there. We always have to be mindful of the resource constraints we're dealing with on the standalone Oculus Quest. 

The image below shows the *Annotations* menu in our VR app. It allows you to explore annotations that have been left in the model via speech-to-text. This is one example of the many pieces of content we display to our users in the VR UI. We also show minimaps, sketching palettes, settings, and other active collaborators. 

Getting this feature to work in our app has a lot of moving parts and we'd like to see how you would tackle a small part of it. 

![](https://drive.google.com/uc?export=view&id=1GdGBNylCIi_da0f8kPFV8PKSJwD1E9Yh)

# Objectives

You will build a 3D worldspace interface in Unity that dynamically loads data from a JSON file and allows the user to explore it.  **Once complete please share a video of your working implementation + your code for us to review.**

Requirements:

1. Read data from a JSON file and use it to populate elements in a worldspace UI. Do not display all the elements at once. Only show 4 annotations at any given time. Each item in the list displayed should contain the text in the `text` field of the JSON item it corresponds to and the `authorName` too. If we test your code with 100+ annotation make sure it doesn't lock up when initializing. Make efficient use of gameobjects with pooling - try not to spawn 100 gameobjects and hide them.
The sample JSON data to use is hosted here: https://resolve-dev-public.s3.amazonaws.com/sample-data/interview/sample-data.json
2. You don't have to make this work in VR, but to simulate the experience the user should be able to interact with the displayed annotation by clicking on the button **in worldspace**. The camera should be able to move around while the UI stays in a fixed position in worldpsace but it should still respond to mouse interaction from any angle. When an annotation is clicked, your application should display the coordinates corresponding to that item's `globalVRState.user.position` field and the button should have a "pressed" state while it's being clicked.
3. The list should be explorable with a scrollbar. The scrollbar should iterate through the list of annotations. Like any scrollbar it should have arrows to assist with fine grain control.
4. Items in the list should be three dimensional and have depth to them as displayed in the images of the VR UI below. They should not just be simple 2D canvas elements. See the video below for an example of this.
5. Please consider performance in your implementation. Minimize the number of draw calls, gameobjects, and expensive methods that would lock up rendering.

Please complete as much or as little of the project as you'd like. We'll use your implementation as a basis for discussion at a later date so keep track of any ideas, bugs, or improvements we can discuss together.

If you find yourself wanting more here are some bonus things you can consider:
- When scrolling partially hide the 3D elements that are not fully visible. Figure out a way to hide part of the 3D button mesh that is not in the active menu window as it scrolls into view.
- Animate the list elements as you hover over them or click on them.
- Write tests for the parts of the code that make sense to test.

## About our current system

Our current VR UI is made up of 3D elements to take advantage of the additional dimensions in VR. The menu is anchored to a user's hand so they can interact with it as they explore their models. Here is a video of how our current Annotations menu in the VR UI works in our production application for reference: https://drive.google.com/file/d/1e5Z-OVU71mzzOy0kx1yXvO1I62fqIdvq/view?usp=sharing

![](https://drive.google.com/uc?export=view&id=1bYenH4kW_vGwo4GNvTQ3mTxWhW2Ek3UB)
