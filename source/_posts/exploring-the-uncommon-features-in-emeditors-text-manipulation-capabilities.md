---
title: Exploring the Uncommon Features in EmEditor's Text Manipulation Capabilities
date: 2024-10-08T17:33:44.826Z
updated: 2024-10-11T12:52:07.732Z
tags:
  - product
categories:
  - emeditor
thumbnail: https://thmb.techidaily.com/7b4c05e427ef93175f84d0a703341dbe0517d72f4c6891c8d31a4e5e36657912.jpg
---

## Exploring the Uncommon Features in EmEditor's Text Manipulation Capabilities

Viewing 5 posts - 1 through 5 (of 5 total)

* Author  
Posts
* November 29, 2007 at 10:36 am [#5068](https://tools.techidaily.com/emeditor/products/)  
[![](https://secure.gravatar.com/avatar/a9ad075b6df6272e7d2016a18148314b?s=80&d=identicon&r=g)jugaor](https://www.emeditor.com/forums/users/jugaor666/ "View jugaor's profile")  
Participant  
Hi, I tried several versions (5 up 7beta) and I found the next ‘bugs’, both in manual / script searches (Spanish texts):  
 a por (eeFindReplaceOnlyWord)  
 matches “creería por”, “CAMPAÑA POR”, etc. (i.e., it breaks the words at the accented vowels or “Ñ”/”ñ”)  
 any accented vowel (eeFindReplaceOnlyWord)  
 matches “diseñé”, “ENSEÑÓ”, etc. (i.e., it breaks at the “Ñ”/”ñ” the words with final accented vowels)  
 In manual searches (with an open document), it matches all the accented vowels inside words despite “Search Only Word” (i.e. it matches “cómprale”, “mamá”, “después”, etc.)  
 (?!es |son)esta(s?)(!|?)  
 discards the first negative subexpression (i.e., it matches “esta!” / “esta?” / “estas!” / “estas?”), despite the fact I use ‘eeFindReplaceRegExp Or eeFindReplaceOnlyWord’ options  
 If I simplify the expression  
 (?!es) esta(!|?)  
 (?!es)esta(!|?)  
 or  
 (?!son) estas(!|?)  
 (?!son)estas(!|?)  
 it has the same behavior. However,  
 (¡|¿)esta(s?)(?! es| son)  
 excepts the correct ones.  
 If you need more information, please email-me.  
 TIA.  
 jugaor  
November 29, 2007 at 7:15 pm [#5071](https://tools.techidaily.com/emeditor/products/)  
[![](https://secure.gravatar.com/avatar/a0a6377144ed3636f985d87303f65ed2?s=80&d=identicon&r=g)Yutaka Emura](https://www.emeditor.com/forums/users/yemura/ "View Yutaka Emura's profile")  
Keymaster  
> jugaor wrote:  
> Hi, I tried several versions (5 up 7beta) and I found the next ‘bugs’, both in manual / script searches (Spanish texts):  
>  
> a por (eeFindReplaceOnlyWord)  
> matches “creería por”, “CAMPAÑA POR”, etc. (i.e., it breaks the words at the accented vowels or “Ñ”/”ñ”)  
>  
> any accented vowel (eeFindReplaceOnlyWord)  
> matches “diseñé”, “ENSEÑÓ”, etc. (i.e., it breaks at the “Ñ”/”ñ” the words with final accented vowels)  
>  
> In manual searches (with an open document), it matches all the accented vowels inside words despite “Search Only Word” (i.e. it matches “cómprale”, “mamá”, “después”, etc.)  
>  
> (?!es |son)esta(s?)(!|?)  
> discards the first negative subexpression (i.e., it matches “esta!” / “esta?” / “estas!” / “estas?”), despite the fact I use ‘eeFindReplaceRegExp Or eeFindReplaceOnlyWord’ options  
>  
> If I simplify the expression  
> (?!es) esta(!|?)  
> (?!es)esta(!|?)  
> or  
> (?!son) estas(!|?)  
> (?!son)estas(!|?)  
>  
> it has the same behavior. However,  
> (¡|¿)esta(s?)(?! es| son)  
> excepts the correct ones.  
>  
> If you need more information, please email-me.  
> TIA.  
> jugaor  
 As far as your first question is concerned, EmEditor did not try to check unicode characters (character code > U+0080) in previous versions for the speed. However, I will add a routine to check some Latin character (ch >= 0x00c0 && ch <= 0x02b8) in the next beta version. This addition will not cover all the Unicode characters but still improve "whole word" accuracy in most cases while not sacrificing much speed.  
 I was not sure about your latter question, but there are two unnecessary spaces in your regular expression: (?!es |son)esta(s?)(!|?)  
 One between “s” and “|”, and the other between ‘n’ and ‘)’.  
 Removing these spaces does not solve your issue?  
November 30, 2007 at 5:30 am [#5074](https://tools.techidaily.com/emeditor/products/)  
[![](https://secure.gravatar.com/avatar/a9ad075b6df6272e7d2016a18148314b?s=80&d=identicon&r=g)jugaor](https://www.emeditor.com/forums/users/jugaor666/ "View jugaor's profile")  
Participant  
Hi, thank you very much for your response.  
 1\. In Spanish, the ‘special’ letters are ÁÉÍÓÚÜ, áéíóúü, Ñ, ñ. I presume that these Unicode chars cover them :)  
 2\. The spaces are needed, since they’re two whole words:  
 “esta” = “this” / “estas” = “these”, both feminine.  
 “es” = “is” (singular, verb to be)  
 “son” = “are” (plural, verb to be)  
 The strange thing is that EmEditor rightly works with the same subexpression after, not before (i.e. “(¡|¿)esta(s?)(?! es| son)” is correct).  
 I have been trying to use EmEditor to automatically correct words with bad orthography in subtitles files (Spanish). I wrote some complex VBEE scripts for that, and I found these issues above.  
 Thanks for your attention,  
 jugaor  
 PS: please, write me when the new beta is ready :)  
November 30, 2007 at 8:30 pm [#5077](https://tools.techidaily.com/emeditor/products/)  
[![](https://secure.gravatar.com/avatar/a0a6377144ed3636f985d87303f65ed2?s=80&d=identicon&r=g)Yutaka Emura](https://www.emeditor.com/forums/users/yemura/ "View Yutaka Emura's profile")  
Keymaster  
> jugaor wrote:  
> Hi, thank you very much for your response.  
>  
> 1\. In Spanish, the ‘special’ letters are ÁÉÍÓÚÜ, áéíóúü, Ñ, ñ. I presume that these Unicode chars cover them :)  
>  
> 2\. The spaces are needed, since they’re two whole words:  
> “esta” = “this” / “estas” = “these”, both feminine.  
> “es” = “is” (singular, verb to be)  
> “son” = “are” (plural, verb to be)  
> The strange thing is that EmEditor rightly works with the same subexpression after, not before (i.e. “(¡|¿)esta(s?)(?! es| son)” is correct).  
>  
> I have been trying to use EmEditor to automatically correct words with bad orthography in subtitles files (Spanish). I wrote some complex VBEE scripts for that, and I found these issues above.  
>  
> Thanks for your attention,  
> jugaor  
>  
> PS: please, write me when the new beta is ready :)  
 (?=pattern) (positive lookahead search) and (?!pattern) (negative lookahead search) look ahead from the position where search begins.  
 For example, expression “(?=x)x” always matches, and expression “(?!x)x” never matches.  
 So it doesn’t make sense to place (?=pattern) or (?!pattern) at the beginning of a search term.  
 I will release beta 41 today or tomorrow.  
December 1, 2007 at 8:05 am [#5080](https://tools.techidaily.com/emeditor/products/)  
[![](https://secure.gravatar.com/avatar/a9ad075b6df6272e7d2016a18148314b?s=80&d=identicon&r=g)jugaor](https://www.emeditor.com/forums/users/jugaor666/ "View jugaor's profile")  
Participant  
THANK YOU VERY MUCH! I tried the 41 beta and the ‘special chars’ issue is gone! :D  
 Also, I saw that I misunderstood the “look ahead” expression :-?  
 I needed to use the “look behind” one (?<!pattern). Excuse me!  
 Congratulations for your excellent job!  
 jugaor
* Author  
Posts

Viewing 5 posts - 1 through 5 (of 5 total)

* You must be logged in to reply to this topic.

<ins class="adsbygoogle"
     style="display:block"
     data-ad-format="autorelaxed"
     data-ad-client="ca-pub-7571918770474297"
     data-ad-slot="1223367746"></ins>

<ins class="adsbygoogle"
     style="display:block"
     data-ad-client="ca-pub-7571918770474297"
     data-ad-slot="8358498916"
     data-ad-format="auto"
     data-full-width-responsive="true"></ins>

<span class="atpl-alsoreadstyle">Also read:</span>
<div><ul>
<li><a href="https://facebook-video-footage.techidaily.com/new-comprehensive-directory-of-inexpensive-stock-images-for-2024/"><u>[New] Comprehensive Directory of Inexpensive Stock Images for 2024</u></a></li>
<li><a href="https://facebook-record-videos.techidaily.com/new-in-2024-dominating-the-digital-space-with-trending-content/"><u>[New] In 2024, Dominating the Digital Space with Trending Content</u></a></li>
<li><a href="https://some-techniques.techidaily.com/new-in-pursuit-of-perfection-highest-rated-phones-for-smooth-videos/"><u>[New] In Pursuit of Perfection Highest Rated Phones for Smooth Videos</u></a></li>
<li><a href="https://fox-info.techidaily.com/updated-2024-approved-unleashing-creativity-gif-formats-decoded/"><u>[Updated] 2024 Approved Unleashing Creativity GIF Formats Decoded</u></a></li>
<li><a href="https://extra-guidance.techidaily.com/2024-approved-professional-8-stream-enhancers-for-video-sharpening/"><u>2024 Approved Professional 8 Stream Enhancers for Video Sharpening</u></a></li>
<li><a href="https://video-capture.techidaily.com/budget-game-design-tools-and-software-for-aspiring-developers-for-2024/"><u>Budget Game Design Tools and Software for Aspiring Developers for 2024</u></a></li>
<li><a href="https://win-top.techidaily.com/discover-the-best-web-based-radio-services-for-complimentary-audio-entertainment/"><u>Discover the Best Web-Based Radio Services for Complimentary Audio Entertainment</u></a></li>
<li><a href="https://win-top.techidaily.com/ensure-crystal-clear-audiovideo-in-your-next-gotomeeting-by-following-these-simple-recording-tips/"><u>Ensure Crystal Clear Audio/Video in Your Next GoToMeeting by Following These Simple Recording Tips</u></a></li>
<li><a href="https://win-top.techidaily.com/expert-tutorial-mastering-the-art-of-adjusting-pdf-document-sizes/"><u>Expert Tutorial: Mastering the Art of Adjusting PDF Document Sizes</u></a></li>
<li><a href="https://tech-hub.techidaily.com/how-to-easily-add-codegpt-to-visual-studio-code-an-in-depth-walkthrough/"><u>How to Easily Add CodeGPT to Visual Studio Code: An In-Depth Walkthrough</u></a></li>
<li><a href="https://extra-hints.techidaily.com/in-2024-12plus-ways-to-immerse-in-international-cricket-via-streaming/"><u>In 2024, 12+ Ways to Immerse in International Cricket via Streaming</u></a></li>
<li><a href="https://apple-account.techidaily.com/in-2024-apple-id-is-greyed-out-on-apple-iphone-12-mini-how-to-bypass-by-drfone-ios/"><u>In 2024, Apple ID is Greyed Out On Apple iPhone 12 mini How to Bypass?</u></a></li>
<li><a href="https://ios-unlock.techidaily.com/in-2024-how-to-unlock-apple-iphone-13-pro-without-passcode-by-drfone-ios/"><u>In 2024, How to Unlock Apple iPhone 13 Pro Without Passcode?</u></a></li>
<li><a href="https://win-top.techidaily.com/quick-and-simple-strategies-for-removing-links-from-microsoft-word-documents/"><u>Quick and Simple Strategies for Removing Links From Microsoft Word Documents</u></a></li>
<li><a href="https://win-top.techidaily.com/quick-and-simple-ways-to-edit-down-your-videos/"><u>Quick and Simple Ways to Edit Down Your Videos</u></a></li>
<li><a href="https://win-top.techidaily.com/step-by-step-guide-capturing-remote-sessions-in-windows-and-macos/"><u>Step-by-Step Guide: Capturing Remote Sessions in Windows & macOS</u></a></li>
<li><a href="https://win-top.techidaily.com/step-by-step-guide-changing-your-video-from-mp4-format-to-wma/"><u>Step-by-Step Guide: Changing Your Video From MP4 Format to WMA</u></a></li>
<li><a href="https://win-top.techidaily.com/step-by-step-guide-designing-your-own-unique-instagram-stickers/"><u>Step-by-Step Guide: Designing Your Own Unique Instagram Stickers</u></a></li>
<li><a href="https://win-top.techidaily.com/step-by-step-tutorial-reflect-your-android-phones-content-on-a-tablet/"><u>Step-by-Step Tutorial: Reflect Your Android Phone's Content on a Tablet</u></a></li>
</ul></div>

<!-- affiliate ads begin -->
<a href="https://appsumo.8odi.net/c/5597632/2132162/7443" target="_top" id="2132162">
  <img src="//a.impactradius-go.com/display-ad/7443-2132162" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://appsumo.8odi.net/i/5597632/2132162/7443" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

