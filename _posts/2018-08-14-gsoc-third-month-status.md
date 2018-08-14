---
layout: post1
title: GSoC 2018 - Third month status
category: draft
--- 

Hi Everyone,

I am working on the GSoC project [Verifying signatures of pdf files](https://summerofcode.withgoogle.com/projects/#6541215701401600) and since the last blog post I have made number of improvements. They are listed below.

**1. Signature Properties Dialog**

This is an improved version with better layout and messages.

![Signature Properties Dialog]({{ "/assets/images/sigpropv2.jpg" | absolute_url }})

**2. Signature Panel**

This is a sidebar widget in okular which will list all digital signatures present in a document. In future, I plan to add a context menu to allow verifying a single signature as well as all signatures at once and viewing the signed revision.

![Signature Panel]({{ "/assets/images/sigpanel.jpg" | absolute_url }})

**3. Revision Viewer**

This is a dialog similar to print preview dialog but instead of previewing what is about to be printed it loads the data covered by a signature in a read-only KPart. In its current state this dialog is pdf specific. This is problematic since okular is a universal document viewer. So I plan to make it a bit more generic.

![Revision Viewer]({{ "/assets/images/sigpreview.jpg" | absolute_url }})

**4. API changes**

Poppler does not provide any details of the signing certificate. So I've filed two bugs ([107055](https://bugs.freedesktop.org/show_bug.cgi?id=107055) and [107056](https://bugs.freedesktop.org/show_bug.cgi?id=107056)) with patches attached for the said task.


**Things I dropped**

* Revision manager

    It turned out to be a mishmash of signature panel and revision viewer. So I dropped it.

* Signature Summary Dialog

    Initially I liked the idea but now I don't.

Finally, the animation below sums up my progress.

![Phase2 GIF]({{ "/assets/images/phase2.gif" | absolute_url }})

Thanks for reading :)
