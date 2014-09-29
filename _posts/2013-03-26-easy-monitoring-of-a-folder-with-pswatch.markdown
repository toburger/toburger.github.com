---
layout: post
categories: powershell
title: Easy monitoring of a folder with pswatch
tags: [powershell]
---

[pswatch](https://github.com/jfromaniello/pswatch/) is a easy to use little module for PowerShell to montitor a folder for changes.

You can choose if you want to monitor file additions, changes, renames or deletions. You can also monitor file sin subfolders.

Based on this monitoring you can further add scripting to automatically run other commands (see example on github).

I further customized the output to include the time of the occurrence of the event:

`watch $env:Temp -includeDeleted | % { $_ | Add-Member ScriptProperty Time { Get-Date } -PassThru }`

This adds a dynamic Time property which automatically updates itself when a new file change event is happening.

