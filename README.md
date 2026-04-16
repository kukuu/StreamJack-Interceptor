# StreamJack


**Author: Alexander Adu-Sarkodie** 
<!--_Turning Video Endings into Revenue Engines_-->  
 
It's essentially an automated agentic intelligent video monetization engine that ensures viewers see valuable content when a user finishes watching something they care about. StreamJack automatically continue their journey with monetized content. Serving as an auto-play funnels for high-intent viewers.

## Overview
 
_Turning Video Endings into Revenue Engines_   

This innovation represents a sophisticated middleware layer that fundamentally alters the YouTube playback experience by intercepting the native video workflow at a critical juncture. Rather than allowing YouTube's default behavior of displaying related videos and end-screen recommendations, I implemented a polling mechanism that continuously monitors the player state and current playback position. When the video approaches its conclusion (within 2.5 seconds of completion), my system forcefully destroys the YouTube player instance, clears the container DOM elements, and injects my custom IframeVideoPromos component - all before YouTube's native end-screen has a chance to render. This creates a seamless transition from content to partner promotions without the jarring appearance of YouTube's own recommendations.

The technical implementation leverages the YouTube IFrame API's event system combined with a high-frequency polling interval (150ms) to detect the precise moment before video completion. My `forceShowPromos()` function executes a multi-step takedown: first visually hiding the YouTube container with CSS transformations (opacity:0, pointer-events:none), then recursively removing all child nodes from the container, destroying the player instance, and finally updating React state to render the partner promo carousel. This aggressive cleanup ensures YouTube can't regain control or display any of its own UI elements, effectively creating a walled garden where my partner content has exclusive access to the user's attention at the most valuable moment - immediately after content consumption.

What makes this approach particularly elegant is how it maintains the illusion of a native YouTube experience while completely subverting it. Users click what appears to be a standard YouTube video, but unbeknownst to them, my middleware is standing ready to hijack the playback flow. By implementing both event-based detection (`onStateChange: 0`) and time-based polling (`(duration - currentTime) < 2.5`), I've created a redundant detection system that guarantees my promos will appear regardless of how YouTube attempts to assert its own UI. The conditional close button logic further refines the experience, ensuring users only see a single, consistent close button whether watching videos or viewing partner promotions.

Watch how this works when videos finish playing or skip to the end:

 - https://www.azzottomovies.com/lounge
 - https://www.azzottomovies.com/lounge-africa
 - https://www.azzottomovies.com/lounge-asia

## Snapshots

<img width="1423" height="677" alt="streamjack-injector-1" src="https://github.com/user-attachments/assets/0559de02-b27a-4baa-a9cb-18d263f4caee" />

<img width="772" height="417" alt="streamjack-injector-2" src="https://github.com/user-attachments/assets/1ab7f5ae-7720-4aeb-bf3e-f76f5076e07c" />

## Vault (Code)

https://github.com/kukuu/streamjack-vault  (**PRIVATE**)

## Portfolio
https://github.com/kukuu/portfolio/blob/main/README.md
