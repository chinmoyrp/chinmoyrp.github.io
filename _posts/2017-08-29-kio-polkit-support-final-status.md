---
layout: post
title: Polkit Support in KIO - Final Status
category: gsoc kde
---

In this post I intend report the final status of my GSoC project (obviously).
My goal for this summer was to add Polkit support in KIO and integrate the upgraded library in dolphin. And well, I have accomplished most (not all :| ) of my goals.

So here goes the list of file operations that can now be performed with elevated privileges 

**1. File Cut/Copy/Paste**

**2. File/Folder Delete**
 
**3. File Rename**
 
**4. Create New Folder/File/Link**
 
**5. Undo**
 
**6. Drag and Drop**
 
 
Now the things that are not working.

**1. Mass Rename**
   
To accomplish mass rename Dolphin creates `CopyJob` in a loop. My approach assumes a single top-level job and multiple child jobs but it is not the case with mass rename. Moreover, there are already couple of bugs owing to the way mass rename is done. That's why I have disabled the action in dolphin's context menu inside a read-only folder.

**2. Trashing Files**

This requires changes in the *trash* protocol. Internally it uses `CopyJob` to move file to/from trash. But the job doesn't have `JobUiDelegateExtension`. The problem seems simple but I haven't had any luck so far maybe because there is something else that's required apart from creating  a `JobUiDelegateExtension`. Currently it shows an error when trying to trash file from a root owned location.

**3. Copying Locked Folder(s)**

Currently folder without search permission cannot be copied. Technically it is possible but the code will be very convoluted and hard to maintain.

**4. Listing Contents of Locked Folder**

Reason stated above.

Revisions for all these changes are listed in  the phabricator task phabricator.kde.org/T6561. All these changes will be merged soon. Till then you can clone my scratch repo https://cgit.kde.org/scratch/chinmoyr/kio-polkit-support.git/ and try out these changes.

Thanks for reading.

