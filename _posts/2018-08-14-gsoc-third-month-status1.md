---
layout: post1
title: GSoC 2018 - Third month status
category: gsoc kde
--- 

Hi All,

In this post I intend to inform about the final status of my GSoC project [Verifying signatures of pdf files](https://summerofcode.withgoogle.com/projects/#6541215701401600).

<br>

***Things Completed:***

**1. Signature Properties Dialog**

In this version of dialog I got rid of the icon label. The dialog has three sections displaying information about signature validation status, signer, and document revision. 

![Signature Properties Dialog]({{ "/assets/images/phase3/sigprop2.jpeg" | absolute_url }})

**2. Certificate Viewer**

This certificate viewer is similar to that of chromium's. It contains two pages. The "General" page displays sort of summary and the "Details" page has all details. On bottom it provides a push button to export the certificate. This dialog can only be accessed from signature properties dialog.

'General' tab
![Certificate Viewer - General Tab]({{ "/assets/images/phase3/certviewer-general.jpeg" | absolute_url }})

'Details' tab
![Certificate Viewer - Details Tab]({{ "/assets/images/phase3/certviewer-details.jpeg" | absolute_url }})

**3. Revision Viewer**

This is a dialog similar to print preview dialog but instead of previewing what is about to be printed it loads the data covered by a signature in a read-only KPart. On top it shows a message informing the user about the read-only nature of the view and on bottom it provides a "Save As" button so that the signed version can be saved. This dialog can be accessed from signature properties dialog and signature panel's context menu.

![Revision Viewer]({{ "/assets/images/phase3/revisionviewer.jpeg" | absolute_url }})

**4. Signature Panel**

This is a sidebar widget which presents all signatures in a tree structure. A context menu is available for this widget through which signed version of a document and signature properties can be accessed. Also selecting any top-level item will change document's viewport to the page where the signature form field is located. 

![Signature Panel]({{ "/assets/images/sigpanel.jpg" | absolute_url }})

![Signature Panel 2]({{ "/assets/images/phase3/sigpanel2.jpeg" | absolute_url }})

**5. Popup**

Now when a signed document is opened there will be two notifications. The former will (as usual) inform about the (signature) forms present and the latter will tell user that the opened document is signed. A toggle button will be there in the second message widget to access signature panel.

![Signature Popup]({{ "/assets/images/phase3/popup.jpeg" | absolute_url }})

<br>

***Things remaining:***

**Menu actions**

Due to making frequent changes to API and other graphical components I wasn't able to decide on what actions to add and where to put them.

<br>

***Getting the code***

The patches for okular are listed in the [phabricator task](https://phabricator.kde.org/T8704).

The git branch with all patches applied : [gsoc2018_digitalsignature](https://cgit.kde.org/okular.git/log/?h=gsoc2018_digitalsignature)

The patches for poppler : [107055](https://bugs.freedesktop.org/show_bug.cgi?id=107055) and [107056](https://bugs.freedesktop.org/show_bug.cgi?id=107056)

<br>

Finally, the following gif sums up my progress.

![Phase3 GIF]({{ "/assets/images/phase3/phase3.gif" | absolute_url }})

Thanks for reading :)
