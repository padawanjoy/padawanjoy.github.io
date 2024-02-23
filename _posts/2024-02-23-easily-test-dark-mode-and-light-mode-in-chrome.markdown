---
layout: post
title:  "Easily Test Dark Mode and Light Mode in Chrome"
date:   2024-02-23 12:55:00 +0900
author: padawanjoy
image:  '/images/posts/2024-02-23-easily-test-dark-mode-and-light-mode-in-chrome/01.webp'
tags:   [dark-mode, light-mode, chrome]
# tags_color: '#844eae'
featured: true
---
In today's world, developing websites or hybrid mobile apps necessitates prioritizing user comfort, including protecting their eyes and reducing battery consumption. For these reasons, 'Dark Mode' has become an essential feature. Offering an interface that users can easily switch according to their preferences has become a critical skill for developers. This article will guide you step-by-step on how to easily test the dark and light modes of a website or app using Google Chrome.

## The Importance of Dark Mode and Its Trend

Dark mode is a design theme that darkens the background to make text and interface elements stand out. It reduces eye strain, improves readability in low-light conditions, and can reduce battery consumption on devices with OLED or AMOLED displays. Major operating systems like Apple's macOS, Google's Android, and Microsoft's Windows support this feature by default. Big services like Facebook, YouTube, and Twitter also offer a dark mode option based on user preference.

## Testing Dark Mode/Light Mode with Chrome

Chrome Developer Tools provide an easy way to test if a website supports dark mode. Here are the steps:

1. Open Google Chrome and navigate to the website you want to test.

2. Click on the three dots menu at the top right corner and select [More tools] > [Developer tools], or use the shortcut **`Ctrl+Shift+I (Windows)`** or **`Cmd+Opt+I (Mac)`** to open Developer Tools.
<br>
![[More tools] > [Developer tools]]({{site.baseurl}}/images/posts/2024-02-23-easily-test-dark-mode-and-light-mode-in-chrome/02.webp)
*Click on the three dots menu at the top right corner and select [More tools] > [Developer tools]*

3. In the Developer Tools tabs, select [Rendering]. (If it's not visible, find [Rendering] as shown in the images below.)

4. Once in the Rendering tab, you'll see various options related to page rendering. Look for the [Emulate CSS media feature prefers-color-scheme] option.

5. Clicking on this option allows you to choose from '**`no emulation`**', '**`prefers-color-scheme: light`**', or '**`prefers-color-scheme: dark`**'. If you want to check if dark mode is applied, select '**`prefers-color-scheme: dark`**'.
<br>
![prefers-color-scheme Options]({{site.baseurl}}/images/posts/2024-02-23-easily-test-dark-mode-and-light-mode-in-chrome/03.webp)
*prefers-color-scheme Options*

6. Based on the selected option, the website will instantly switch to dark mode or light mode. This allows you to check in real-time if the style of the website being developed correctly applies according to the user's system settings.

## Conclusion

For web and app developers, prioritizing the user experience is crucial. Properly supporting dark and light modes has become a fundamental element of user-friendly interface design. Testing dark and light modes with Chrome Developer Tools is a powerful tool for user-centered design and development. This guide aims to help you understand the importance of supporting dark/light modes in website or app development and apply it effectively. Happy coding!