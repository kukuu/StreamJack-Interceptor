# StreamJack


**Author: Alexander Adu-Sarkodie** 
<!--_Turning Video Endings into Revenue Engines_-->  
 
StreamJack is a post-video monetization platform that captures viewer attention the moment content ends and seamlessly continues the experience with relevant, revenue-generating video.

By targeting high-intent viewers at peak engagement, StreamJack increases session time, ad exposure, and conversion rates—without interrupting the viewing experience.

## Overview
 
_Turning Video Endings into Revenue Engines_   

This innovation represents a sophisticated middleware layer that fundamentally alters the video playback experience by intercepting the native video workflow at a critical juncture. Rather than for example  allowing a YouTube's default behavior of displaying related videos and end-screen recommendations which may be irrelevant, it implements a polling mechanism that continuously monitors the player state and current playback position. When the video nears its conclusion  the system takes over the player instance, clears the container DOM elements, and injects custom rich media promos component - all before the native end-screen has a chance to render. This creates a seamless transition from content to partner promotions without the jarring appearance of it's own recommendations.

The technical implementation leverages the  API's event system combined with a high-frequency polling interval (150ms) to detect the precise moment before video completion. A `forceShowPromos()` function executes a multi-step takedown: first visually hiding the system's container with CSS transformations (opacity:0, pointer-events:none), then recursively removing all child nodes from the container, nullifying the player instance, and finally updating React state to render the partner promo content. This aggressive cleanup ensures the system can't regain control or display any of its own UI elements, effectively creating a walled garden where the partner content has exclusive access to the user's attention at the most valuable moment - immediately after content consumption.

What makes this approach particularly elegant is how it maintains the illusion of a native system experience while completely extending its behaviour both event-based detection (`onStateChange: 0`) and time-based polling (`(duration - currentTime) < 2.5`). StreamJack  creates a redundant detection system that guarantees its promos or partner content  will appear regardless of the system to assert its own UI and serve irrelevant content. The conditional close button logic further refines the experience, ensuring users only see a single, consistent close button whether watching videos or viewing partner promotions.

Watch how this works when videos finish playing or skip to the end:

 - https://www.azzottomovies.com/lounge

## Snapshots

<img width="1423" height="677" alt="streamjack-injector-1" src="https://github.com/user-attachments/assets/0559de02-b27a-4baa-a9cb-18d263f4caee" />

<img width="772" height="417" alt="streamjack-injector-2" src="https://github.com/user-attachments/assets/1ab7f5ae-7720-4aeb-bf3e-f76f5076e07c" />

## Vault (Code)

https://github.com/kukuu/streamjack-vault  (**PRIVATE**)

## Portfolio
https://github.com/kukuu/portfolio/blob/main/README.md
