+++
title = "VFS for Git"
author = ["Jethro Kuan"]
draft = false
+++

VFS for [Git]({{<relref "git.md" >}}) is a virtualized filesystem used to bypass assumptions
about repository size, allowing Git repositories to scale up to large
repositories.

With GVFS, an initial clone downloads a set of pack-files containing
only commits and trees. These objects are sufficient for generating a
view of the working directory, and examining the commit history with
git log.

GVFS allows dynamically downloading objects as needed.
