# IMPORT NUGET PACKAGES TO F# INTERACTIVE SCRIPTS

Yes, it’s been a long time (exactly one year, but that’s a coincidence) since my last blog post. The main reason was that in the last year I learnt F# and slowly I have the feeling that I have understood the language and especially the paradigm shift that comes with F#.

_I jump over the usual homage of why F# is a wonderful language – that’s material for a plethora of blog posts – and come straight to the motivation of this blog post._

If you are like me and you learn by trying things out you probably love the interactive and iterative nature of F#. Just create a new fsx (F# Interactive) file and start hacking until you have a working prototype. You don’t even have to save the file!
I actually have a folder full of F# scripts with my experimentations in them.

One pain point though is that F# interactive does not have support for NuGet package management. You can reference the library files manually but that’s very cumbersome.

There exists an older [blog post](http://bloggemdano.blogspot.it/2011/08/adding-nuget-support-to-f-interactive.html) from Daniel Mohl where he suggests how to add NuGet support to F# Interactive, but his solution requires the VS Object Model and doesn’t support loose fsx files (without the creation of a F# project).

So I wrote my own “PackageManagement.fsx” file which can be initialized with F# Interactive:

![](http://tobivnext.files.wordpress.com/2014/03/032614_1615_importnuget1.png?w=580)

And here is the script code: https://gist.github.com/toburger/9786275

It depends on the NuGet.Core.dll which you can get from [here](http://nuget.codeplex.com/) and you must define your target NuGet packages directory, where the packages are downloaded and from where they are referenced (you can define the `NugetLibDir` environment variable so you can use the same script on multiple machines). I ignore the versioning of the packages (I always download the latest stable release), but you can enable it by setting the boolean parameter `useSideBySidePaths` on line 11 to true.

## So how to work with this script?

The main command is `ipr` which stands for “install package and references”, which downloads the package with all its dependencies and adds the references to the clipboard, so the only thing you have to do is to paste the references on top of your script file.

Just enter `ipr “package name”;;` in the f# Interactive REPL (don’t forget the two semicolons) and it will try it’s best to download and reference the packages.

![](http://tobivnext.files.wordpress.com/2014/03/032614_1615_importnuget2.png?w=580)

There are also commands to update and uninstall packages or to simply copy the references without trying to download the latest package.

## Limitations:

I try my best to find the best matching references for the framework version in which F# interactive runs, but this matching is not bullet proof and unfortunately the NuGet lib doesn’t provide a way to get the best matching references automatically (at least I didn’t found any practical way).

The script should also work without VS and should work on Mono but I don’t have tested it so please feel free to contact me or edit the file if you have any problems.

***

Actually there is now a suggestion on fslang uservoice with a propose to natively support NuGet packages: http://fslang.uservoice.com/forums/245727-f-language/suggestions/5670137–package-directive-to-import-nuget-packages-in-f