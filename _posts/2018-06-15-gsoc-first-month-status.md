---
layout: post1
title: GSoC 2018 - First month status
category: gsoc kde
---

Hi all, I am Chinmoy and I am working on the GSoC project [Verifying signatures of pdf files](https://summerofcode.withgoogle.com/projects/#6541215701401600). This is my very first post and in this I intend to inform about the progress I have made since May 14.

Now due to some unforeseen problems I had to deviate from my proposed timeline. Initially my plan was to implement all non-graphical components in the first half of coding period and in the later half implement the graphical components. But while coding _RevisionManager_ (this would have enabled to view a signed version of document before an incremental update like Adobe Reader does) I ran into some issues while designing its API. So I postponed my work on _RevisionManager_ and started working on the graphical components. So as a result I was able to add basic GUI support needed to verify signed PDF. The patches are listed in [T8704](https://phabricator.kde.org/T8704). After applying every patch from the dependency stack of any differential the following changes can be observed : 

1. Okular shows a notification telling a signature form field is present.
![Signature Field Notification]({{ "/assets/images/signotif1.jpg" | absolute_url }})

2. "Validate All Signatures" validates all signature and shows signature status.
![Signature Status]({{ "/assets/images/sigstatus.jpg" | absolute_url }})

3. "Show Forms" shows the form widget which is basically a rectangle.
![Signature Widget]({{ "/assets/images/sigwidget.jpg" | absolute_url }})

4. Clicking on widget validates that particular signature and shows signature status.
![Signature Summary]({{ "/assets/images/sigsum.jpg" | absolute_url }})

5. A context menu is also available.
![Signature Menu]({{ "/assets/images/sigmenu.jpg" | absolute_url }})

6. Signature properties will be available only after verifying a signature. It can be  accessed either from signature status dialog or context menu.
![Signature Property]({{ "/assets/images/sigprop.jpg" | absolute_url }})

Putting everything together:
![Signature Gif]({{ "/assets/images/siggif.gif" | absolute_url }})

As you can see the UI is crude and there's LOT to be improved. So I would really appreciate any feedback on what to show and what not to.

You can build my okular [clone](https://github.com/chinmoyrp/okular) and try out the changes on [this PDF]({{ "/assets/downloads/pdf_with_signature.pdf" | absolute_url }}).

Thanks for reading :)

