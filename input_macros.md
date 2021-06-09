# Video

We have compiled a video to show off our work on the Word add-on and Chrome extension that we refer to as the "input macros" project.

<iframe width="560" height="315" src="https://www.youtube.com/embed/Atgob7W90cs" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<div>
  <a href="https://www.youtube.com/watch?v=Atgob7W90cs">https://www.youtube.com/watch?v=Atgob7W90cs</a>
</div>

# Responses

## Introduction

When Devva came and talked to us in class, she told us about how Microsoft Word had taken a backwards step in accessibility for her. At some point, she had noticed that Word had moved from a spellcheck emphasis to a grammar checking emphasis, and with that move, it became much harder to create autocorrect shortcuts. She uses autocorrect shortcuts to type long phrases briefly, allowing Word to expand her abbreviations. She asked us to bring back bits of autocorrect functionality that were now either missing entirely from Word, or hidden away in menus that took many clicks to access. Something that could translate her keyboard shortcuts into longform text in a customizable way.

For people who have disabilities relating to fine motor control, which can oftentimes affect typing and other similar small movements, having a way to type efficiently while minimizing the amount of keys you need to press can be really helpful. We wanted to build a solution that would enable those with fine motor control disabilities to type long words with fewer keystrokes.

In our research, we identified additional interesting aspects of this problem. For instance, a dictionary of abbreviations that make sense to one person may not make sense to another person, so this ends up being a fairly personal problem. So, with Devva's help and guided by our additional research, we additionally prioritized building a way for each person to build up their own abbreviation/expansion dictionary and import and export that dictionary to multiple programs, starting with Google Chrome.

## Related work

This style of typing using abbreviation expansions is nothing new -- Devva and others have been using this technique for a long time. There has even been research into automating the process of generating abbreviation and expansion pairs [1] which involved studying patterns in which abbreviations people choose and can understand. Additional research has been done to investigate the usability and feasibility of typing software that adapts to a users typing style, offering replacement suggestions while also allowing the user to define their own abbreviation expansions [2]. Success in this line of research would reduce the need for users to maintain their own autocorrect dictionary of abbreviation expansions. This amount of automation is out of scope for our project, but it’s important to note that there is potential beyond our project for improving the typing experience for users with motor disabilities. 

Interestingly, Microsoft Word used to have a feature that enabled Devva to customize her abbreviations within the autocorrect dictionary as she typed -- until the user interface was overhauled and this feature was hidden away. There is nothing state-of-the-art about keeping track of an autocorrect dictionary and giving the user access to editing that dictionary, but to many users, including Devva, this kind of feature is more useful than it’s replacement, which is an AI powered grammar, spelling, and writing style ‘Editor’ service [3]. The ‘Editor’ assumes spellcheck and autocorrect features will be used to fix errors when users attempt to type entire words, ignoring the class of users who had long been using autocorrect to apply abbreviation expansions. Thus, our focus is on giving users who employ the abbreviation expansion style of typing easy access to using and editing the autocorrect dictionary while typing. 

[1] [Informing Flexible Abbreviation Expansion for Users with Motor Disabilities](https://www.researchgate.net/publication/225159894_Informing_Flexible_Abbreviation_Expansion_for_Users_with_Motor_Disabilities)

[2] [A Shorthand Word Expansion System for
Dexterity Impaired Users](https://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.101.8147&rep=rep1&type=pdf)

[3] [Word 365 Editor Pane makes spellcheck take a very, very long time.](https://answers.microsoft.com/en-us/msoffice/forum/msoffice_word-mso_win10-mso_365hp/word-365-editor-pane-makes-spellcheck-take-a-very/3bc1f9e5-7b4a-4340-974f-e84844bd5cc5?page=1)

## Solution

For our project, we built this type of input macro functionality Word with an add-on and Chrome/Edge with an extension.

In Word, we built an add-in that shows up as an extra tab in the Word ribbon. In the ribbon is a section where you can add entries as pairs of abbreviations and expansions, a section where you can import and export abbreviation - expansion pairs in the form of a .tsv file, and a section where you can view the abbreviation-expansion pairs. There is extra functionality in the right-click menu when you have text highlighted that allows you to easily add a new expansion by writing the text you want your highlighted text to expand to in the correction text box that pops up on right click. 

<img width="502" alt="Screen shot of Word add-on. The usual ribbon at the top of the screen shows a section called 'AutoCorrect', with sections to add an entry, import and export configs, and view the config. The add entry section has a text box labeled 'Abbreviation', in which someone has typed 'ty', and a text box labeled 'Expansion', in which someone has typed 'Thank you'." src="https://user-images.githubusercontent.com/1192815/121298536-e8291700-c8a8-11eb-9759-141e92ed7db2.png">

In Chrome, we built an extension that allows a user to upload their .tsv file from Word in order to automatically expand the same set of abbreviations that they used in Word. The functionality intentionally attempts to mirror the bahaviour seen in the Office suite: an abbreviation is expanded when a non-word character is typed, and expansion can be immediately undone with Ctrl-Z if the expansion is not needed. This works on most simple websites, any time the user types in an `input` or `textarea` HTML element. The extension also intentionally has large buttons for easy targeting and click, and can be toggled on and off to prevent unwanted expansions.

<img width="251" alt="Screen shot of Chrome extension. Two large buttons say 'Import Config' and 'Export Config', a label indicates that autocomplete is currently turned on, and a switch is available to toggle the extension off." src="https://user-images.githubusercontent.com/1192815/121298393-a8622f80-c8a8-11eb-97e3-79a5532a1489.png">


## Validation

Our approach was validated with user testing. Once we had boths solutions working to some degree, we reached out to Devva and solicited feedback. She was a primary driver of the feature design, so it made sense that she would also be the primary source of validation.

Prior to development, we had a call with Devva to determine the requirements of what she was hoping we would build. We prioritized features based on her requirements and our own evaluation of feasibility, and began building up prototypes. Once these were ready, we sent videos of the features at work and sent them to her in order to get more information about what she liked and disliked about the product we built.

We were happy to get her response back, with “BOTH LOOK VERY COOL AND I WOULD USE THEM”. She liked the fact that both the add-in and extension could use a .tsv, and asked a few questions about the experience. Namely, is there an easy way to view the full configuration? Do configs get merged on import? How do we create a shortcut on the fly in Chrome? We were happy to tell her that there was an easy way to view the full configuration in an Excel file. However, configs do get overwritten on import, and we don’t currently have a way to create a shortcut on the fly in Chrome. We recognize these are further areas for improvement.

Since we’ve gotten feedback from her, we were able to work on dictionary import and export options in both Word and Chrome.


## Learnings and future work

By talking to Devva, we were able to learn the importance of alternatives in accessible technology like voice technology. For Devva, who is unable to use voice recognition and has motor control issues that can make it difficult to type, these abbreviation-expansions are really important for her to more easily be able to use the computer.  We also gained more first-hand experience talking to customers to build a customer-specific feature. At work, we generally build features for large groups of people and maybe, if we’re lucky, have the opportunity to talk to a few of them. This was an awesome opportunity to be able to discuss the nitty-gritty details of a project with the person that we were building it for. We learned how important it is to talk to our target audience instead of just guessing about what we think they want. Moreover, we also got good technical experience building a browser extension for Chrome and Edge, as well as building an add-in for Word and learning how to build that. 
