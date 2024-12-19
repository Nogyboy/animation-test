# Animation Test App

## Live Demo
[Demo](https://animation-test-indol.vercel.app/)

## Technologies
Astro, Javascript, CSS, HTML, TailwindCSS

## Description
Simple app to add animation base on scrolling.
 - On load video will be playing for 3 seconds then will be paused and will be controlled by the scroll
 - Video control based on scrolling, pause when reaching the top and stop when reaching the bottom
 - Text appear depends on scrolling position
 - Icon animation at the bottom of the screen, pulse animation and when reaching the bottom of the screen turns 180 degrees

## Solution - Pre analyzing
- Optimized the assets to use to improve loading time
- Configure priority loading for the video
- Choose video base on window size
- Implement a event listener to detect when the user scrolls
- Control video playback based on scroll position
- Animate text based on scroll position
- Animate icon based on scroll position

## Memory
- I used Astro framework, because it's easy to create components and layouts, and also is really close to the web platform, and in the end, it's just HTML, CSS, and JS.
- Solving the background video was challenging, because I had to investigate about video properties and how it works. I found a really simple example [here](https://codepen.io/mpeach/pen/LbxGrj), however I was not able to implement with the video provided, so I tried modifying the Bitrate, resolution, and optimizing the video to reduce the size, but it didn't work. It seems the video needs to be optimized to be transferred over HTTP, and able to stream.
- After tried some solutions but didn't work, so I maintained the original video, and use requestAnimationFrame, which is an API to tell the browser when to repaint the screen, and match the display refresh.
- However, I found that the video was not playing smoothly on the first scroll, I discovered the video comes in chunks, and just when the file is completely loaded, the scroll synchronization works smoothly. So I think the problem is how the video format is exported, because with the above example, it works fine.
- Regarding the text animation, I use scroll driven animation. I found using CSS animations improves performance, because it works apart from the main thread.
- To solve this problem, I just use plain javascript. It's good practice to consider if all these APIs are compatible in the target browsers.