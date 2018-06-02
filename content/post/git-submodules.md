---
title: "Introduction to git submodules"
date: 2018-06-02T13:30:00+02:00
draft: false
---

# What is a submodule?

When cloning a git repository it will sometimes be that the superproject repository uses *submodules*.

A *submodule* is a commit reference to another projects repository that the superproject depends on.

You can identify this by the superproject containing a `.gitmodules` file in the root directory of the superproject repository.

# How do I correctly clone the superproject?

There are a few steps that are required on your part before you can utilise the superproject repository as desired:

Clone the repository to your local machine and change into the directory.

``` bash
git clone https://github.com/user/superproject.git
cd superproject
```

Initialize your local git configuration file to be aware of the submodules.

``` bash
git submodule init
```

Pull the submodule projects at the referenced commit in the `.gitmodules` file to your local machine.

``` bash
git submodule update
```

# There is an even simpler way!

A quicker, simpler way to achieve this state is to use a special flag when cloning the project.

``` bash
git clone --recurse-submodules https://github.com/user/superproject.git
```

This will initialize and pull the superproject repository along with all submodule projects.

# How do I get the submodules upstream changes?

When you need to get the upstream changes for your submodule, you will have to update your submodules referenced commit in the `.gitsubmodule` file.

We do this by changing into the submodule directory and performing a *fetch* and *merge* into the local code.

``` bash
cd superproject/submoduleproject
git fetch
git merge
```

# All the updates... one command?

We may have multiple submodules and want to update all of them together. Using the method of changing into the submodule and doing a fetch and merge can lead to missing one of the submodules and can be repetitive if you have many submodules.

We can use this command to do them all at once.

``` bash
git submodule update --remote
```

# Where can I learn more?

Submodules are an awesome way to share code between projects allowing you to avoid repeating the code and also avoiding the need to package the code for consumption by the other projects.

If you want to learn more about how to use the submodules feature of git you can read the [official documentation](https://git-scm.com/book/en/v2/Git-Tools-Submodules)