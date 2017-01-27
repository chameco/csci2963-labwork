Why is it important to choose a license?
----------------------------------------
It is important to choose a license because there are no "defaults" when it comes to copyright for an open-source repository. If you do not provide a license with your code, you implicitly reserve all rights to that code - if your intent was to allow others to make use of and contribute to your project, failure to provide terms for use is in perfect opposition to that intent.

Why is it important that you SHOULDN'T use a project that doesn't have an explicit license?
-------------------------------------------------------------------------------------------
As mentioned previously, a project without an explicit license has all rights reserved: the copyright holder retains full ownership of the project, and you as an outsider have no right to use any of the included code.

Why the Web Beat Gopher
-----------------------
I agree with the claim that a more open development climate helped to faciliate the dominance of HTTP over Gopher. The only major problem domains where proprietary software seems to win out are those where it becomes very large long before an equivalent open source product develops, establishing a network monopoly. Today, this can be seen in the desktop computing world: the majority ofdesktop software is written for Windows, so many people use Windows to have access to this software, incentivizing developers to write more software targetting Windows. Contrast this with the server and mobile computing domains, where open source solutions have dominant market share (via Linux distributions on the server and Android on mobile).

Android, Linux, Microsoft, Sailfish
-----------------------------------
Linux uses the GPL because a project of its scope would not be sustainable if commercial interestes were allowed to withold their changes. Linux relies on a huge number of drivers and other modules, at times developed by hardware companies themselves. Intel and Google number among the top contributors to the kernel: one might imagine a world where Intel would be allowed to withhold or sell their valuable kernel contributions, which would ultimately lead to duplicated and wasted effort.

Read these licenses GPL, LGPL and Apache/BSD and discuss which one will be better - for a developer, for a company and for the common good - write 5 to 10 sentences.
---------------------------------------------------------------------------------------------------------------------------------------------------------------------
I would argue that the GNU GPL is always the correct choice: for a developer, for a company, or for the common good. For a developer, the GPL effectively ensures a "return on investment": if someone makes use of your shared code, they are obligated to also share their work in return. For a company seeking to make use of a free software library, the GPL ensures a good ethical foundation by preventing that company from makingg the wrong choices. Using secrecy in a digital medium for most purposes, whether it is to protect copyright or to maintain some veil of security through obscurity, is almost never a good idea and almost always unethical. The GPL and other copyleft licenses encourage companies to follow better business models, such as selling support rather than selling ideas. This ties in with the benefit to the common good: the concept of intellectual property in general stymies human progress.

Create a repository and choose a license.
-----------------------------------------
https://github.com/reliquary/reliquary

Write five sentences about choosing a project to work on in this course, who will be users/customers of the project, and what license will you choose.
------------------------------------------------------------------------------------------------------------------------------------------------------
I wrote in some detail about a project in which I had an interest in the first lab assignment. There, I described a concatenative functional programming language I had been working on for approximately six months. I think this work is valuable for a few reasons. First, it explores an exciting niche in the world of programming language theory, one where not much other work has been done. Second, it will hopefully condense into a good environment in which to develop computer software: the techniques used in conditional concatenative languages such as Forth (for example, bottom-up development) have proven useful to develop system-level software, and I hope that they will be similarly useful in developing high-level software when mapped over a different set of primitive operations. Finally, I believe that it will help provide a simple introduction for newcomers in the field of type theory as applied to programming languages: this field is often difficult to approach for those without mathematical background, but the underlying concepts are not intrinsically more complicated than those found in other problem domains.
Users of this project would most likely be primarily be hobbyists and academics interested in the field of programming language theory, or anyone interested in learning more about that field.
I have selected the GNU GPL 3 for this project, as for most software I create today. This is driven by a fundamental belief that nonfree software is not ethically justifiable and is in fact harmful to computing as a whole. At this point in my life, I can afford to have the position that ethics are more important than creating good software: I would gladly sacrifice a few contributors to ensure that none of my work ever benefits the propagation of nonfree software.

Take 5 projects from Observatory or past RCOS Projects and create a table for which project has which license.
--------------------------------------------------------------------------------------------------------------

Website | License Present | License
---------|:----------|:-------
https://github.com/submitty/submitty | Yes | [Three Clause BSD License](https://en.wikipedia.org/wiki/ISC_licens://en.wikipedia.org/wiki/BSD_licenses#3-clause_license_.28.22Revised_BSD_License.22.2C_.22New_BSD_License.22.2C_or_.22Modified_BSD_License.22.29)
https://github.com/YACS-RCOS/yacs | Yes | [MIT](https://en.wikipedia.org/wiki/MIT_License)
https://github.com/AesaKamar/Pokedex | No | N/A
https://github.com/slickos/slickos | Yes | [MIT](https://en.wikipedia.org/wiki/MIT_License)
https://github.com/Behemyth/Soul-Engine | Yes | [GNU GPL 3](https://en.wikipedia.org/wiki/GNU_General_Public_License#Version_3)

![Creative Commons License](https://i.creativecommons.org/l/by/4.0/88x31.png) This work is licensed under a http://creativecommons.org/licenses/by/4.0/ Creative Commons Attribution 4.0 International License.
