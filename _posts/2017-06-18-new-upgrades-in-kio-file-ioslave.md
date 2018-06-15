---
layout: post
title: New updates in KIO file ioslave
category: gsoc
---
KIO Slaves are out-of-process worker applications that perform protocol-specific communications. To provide local file handling file managers use the file ioslave(file:/). Up until now file management with root access was forbidden in file ioslave. But with this week's work situation might just change for good. 

During the past week and a half, I worked on getting polkit support to delete, copy, rename, symlink and mkdir function. My attempts at getting these file operations working correctly inside a read-only folder were almost successful. I was able to add polkit support to all but the copy file operation. To get the copy function working I needed to be able to open a file with elevated privilege in the KAuth helper and send back the file descriptor to file ioslave for further processing. It was the latter part that proved to be the major obstacle. Since file descriptors are non-negative integers it may be instinctive to embed them in QVariant and send them back to ioslave over D-Bus. However, they have more to them than just being an integer. Owing to this fact the integer value is pretty much meaningless outside its host process. Therefore, even though I was able to retrieve the file descriptor in ioslave, doing any kind of file processing ended in failure. Although unix local domain socket is apt for this task, due to my unfamiliarity with network programming and the unavailability of any equivalents in Qt, I had to postpone my work on the copy function for a while. 

Coming back to changes. I had added polkit support to the delete function prior to sending my GSOC proposal as a proof of concept. So, during this time I mostly made it a bit modular and separated, what seemed to be, the boilerplate code. Getting polkit support to rest of the lot was simple as the code was similar to that of delete. After these successive changes, a KIO client can now perform the following tasks as a privileged user without having to start itself as root.
1. Delete files and folders.
2. Rename files and folders.
3. Create folders.
3. Create symbolic links.

You can view all of my changes in [cgit.kde.org](https://cgit.kde.org/scratch/chinmoyr/kio-polkit-support.git). To avoid any convolution in future I went for creating a separate branch for every file management function instead of a single, difficult-to-manage branch. Testing the upgraded ioslave needs some changes in dolphin as well. Since the changes are trivial and cloning dolphin seemed futile, I have hosted my patches for dolphin on [github](https://github.com/chinmoyrp/dolphin-patches). Apart from the clone, I have some patches on phabricator as well, precisely [D6197](https://phabricator.kde.org/D6197), [D6198](https://phabricator.kde.org/D6198) and [D6199](https://phabricator.kde.org/D6199). Apply them in order to test polkit support in delete file operation. So, if you are getting bored and looking forward to doing some unpaid labor you can review my patches, alternatively, you can also fork my kio [clone](https://cgit.kde.org/scratch/chinmoyr/kio-polkit-support.git) and see the changes yourself. (:

Here's a demo for the curious minds.
<div class="video_container">
<iframe src="https://www.youtube.com/embed/TqfyUN1kVl4" frameborder="0" allowfullscreen class="video"></iframe>
</div>


That's all for this week folks.
