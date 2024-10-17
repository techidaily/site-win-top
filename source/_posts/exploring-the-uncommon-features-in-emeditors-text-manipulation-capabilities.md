---
title: Exploring the Uncommon Features in EmEditor's Text Manipulation Capabilities
date: 2024-10-15T16:28:58.243Z
updated: 2024-10-17T16:43:24.058Z
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
<li><a href="https://youtube-blog.techidaily.com/ed-expertly-slice-your-videos-macs-finest-mp4-applications-for-2024/"><u>[Updated] Expertly Slice Your Videos Mac's Finest MP4 Applications for 2024</u></a></li>
<li><a href="https://win-top.techidaily.com/ultimate-guide-windows-103/"><u>「Ultimate Guide: Windows 10における3種類のゴースト画像化手法」</u></a></li>
<li><a href="https://screen-sharing-recording.techidaily.com/2024-approved-leading-tools-to-record-your-desktop/"><u>2024 Approved Leading Tools to Record Your Desktop</u></a></li>
<li><a href="https://win-top.techidaily.com/win1011/"><u>修復Win10/11硬盤碎片化分區的刪除資料回收方法</u></a></li>
<li><a href="https://win-top.techidaily.com/ultra-3d-ssd/"><u>最高のクローニング方法：サンディスクUltra 3D SSDのためのベストプラクティス</u></a></li>
<li><a href="https://win-top.techidaily.com/comprehensive-freeundelete-software-analysis-the-ultimate-guide/"><u>Comprehensive FreeUndelete Software Analysis - The Ultimate Guide</u></a></li>
<li><a href="https://extra-resources.techidaily.com/echo-emporium-a-selection-of-top-sites-for-skype-audio/"><u>Echo Emporium A Selection of Top Sites for Skype Audio</u></a></li>
<li><a href="https://youtube-video-recordings.techidaily.com/in-2024-7-insider-tips-to-make-money-quickly-on-youtube-shorts/"><u>In 2024, 7 Insider Tips to Make Money Quickly on YouTube Shorts</u></a></li>
<li><a href="https://screen-capture.techidaily.com/in-2024-step-by-step-guide-to-flawless-zoom-screen-sharing/"><u>In 2024, Step-by-Step Guide to Flawless Zoom Screen Sharing</u></a></li>
<li><a href="https://fox-direct.techidaily.com/step-by-step-strategies-for-successful-youtube-srt-downloads/"><u>Step-by-Step Strategies for Successful YouTube SRT Downloads</u></a></li>
<li><a href="https://win-top.techidaily.com/switching-sql-database-models-transition-from-simple-to-full-a-comprehensive-guide/"><u>Switching SQL Database Models: Transition From Simple to Full - A Comprehensive Guide</u></a></li>
</ul></div>

<!-- affiliate ads begin -->
<a href="https://aligracehair.sjv.io/c/5597632/2135402/19272" target="_top" id="2135402">
  <img src="//a.impactradius-go.com/display-ad/19272-2135402" border="0" alt="https://techidaily.com" width="336" height="90"/>
</a>
<img height="0" width="0" src="https://aligracehair.sjv.io/i/5597632/2135402/19272" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

