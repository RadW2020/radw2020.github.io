---
layout: post
title: Components library with Angular
image: Angular_SubModules.png
---

Let's say our project is growing and we want to keep things separated. Sometimes we can split our angular project in two or three different projects but then, we realize it will be repeated code from styles, components or any other resource.

As a first resume of what we want to do here, we have:
- Create a couple of Angular projects that will use same custom library
- Create the custom components library (with Angular)
- Host that custom library in our base projects like a GIT submodule
- Build and access the library from our base projects like a normal angular package
- Profit :)

You can find nice posts and with generic information tha can help you to accomplish this task. Like this amazing [summary](https://gist.github.com/gitaarik/8735255) about GIT submodules. Or the official documentation of [ng-packagr](https://github.com/ng-packagr/ng-packagr) about transpile a library to Angular Package Format.

But for this post, what a I want to do is a __practical example with Angular__ (I need to practice to feel like I really understand, I'm sure some of you too!).

### Create the example projects

Create three minimal Angular projects:
```bash
ng new HelloFoo --minimal
ng new HelloBar --minimal
ng generate library ComponentsLibrary
```

After a few tweaks, __to help us differentiate both Hello projects__, we could have something like this.

![](https://i.imgur.com/gSeLcW1.png)

### Prepare the custom library project

Pay attention to the shape of our __components library__. We have generate it as a library. Doing so, we don't need to  delete non useful Angular configuration files as we only need to export components/modules there.

For this occasion, lets create a footer module in our new components library project. 


![](https://i.imgur.com/Zbt4xYl.png)


We want to use this resource in both Hello projects and we want to be sure that it is going to __keep consistency while avoiding DRY__. (This is one of the main reasons of having a common submodule)

Pay attention to ```public-api.ts``` file. It describes the access points that we will need to import in the Hello Projects later on.


For the purposes of this tutorial, we can have these two projects in local, but we need to put the components library in a shared repository. 
We use Github in this case, so we push out this new components library into his repository. https://github.com/RadW2020/components_library_tutorial

### Add the submodule to the projects

At this point, we want our two base projects stay aware of this new library. In order to do that we execute this command in the root folder of our Hello project:

```
git submodule add git@github.com:RadW2020/components_library_tutorial.git custom_lib
```
Execute this in our two Hello projects. This will add it as a submodule in the given folder. Please notice the new file GIT has created for us named ```.gitmodules```

![](https://i.imgur.com/sS3Sgku.png)


> From now on, this shared library, that is a project on itself, is tied in our Hello projects as a submodule hosted in his own folder _custom_lib_. 

### Maintain the submodule updated

What happens if a change is pushed to the components library repository? We need to be aware and check it to keep our library updated.
This will be noticeable any time we use ```git status``` in our Hello projects.
Something like this should be shown:

![](https://i.imgur.com/2VpHWu0.png)

GIT is warning us about commits in lib's origin. We want to tell to our Hello project to point to the last commit of the components library repository. For that, we don something like this:

```
git add .
git commit -m "update custom_lib to last reference" 
```

This will update the submodule from the point of view of our Hello project. What we really are doing here is maintaining in our Hello project custom_lib folder. This is done by holding a reference that points to a commit of the custom_lib GIT history, if it is not the last, the message __(new commits)__ shows up.


### Components library evolution
To finnish this mutation, we have to prepare our library to behave like that. A new configuration file has to be created, so **ng-packagr** will know how to handle it:

![](https://i.imgur.com/erY446B.png)

In ```ng-package.json``` file it is specified where will be located the build (dest), and how it will accesible (entryFile).

### Next steps

Now we need to **tell to our Hello projects** that this _custom_lib_ is more than just a sub-folder synced with GIT. We have to specify a few things:
 > - How to compile _custom_lib_ so it can be used like a regular **dependency**.
 > - Where is located the library dependency. (We will leave it in dist folder next to the other installed dependencies)
 > - The **compiled** library needs to be listed in package.json like a regular dependency.
 

#### Dev Dependencies
In ```devDependencies```, it is declared the ng-packagr and other dependencies needed to transpile the library to an Angular package format.

![](https://i.imgur.com/1h7aFIH.png)

Time to execute ```npm install``` to get those new dependencies.

#### Build lib
In ```scripts```, it is declared how to build the library.
![](https://i.imgur.com/gXfYvOp.png)

This will build the project that we have to define in ```angular.json```
![](https://i.imgur.com/RiUdWFJ.png)

Then execute ```npm run build-lib```. The console will show some information.
![](https://i.imgur.com/C62YS2z.png)

In ```dependencies```, must be declared where to find the build.
![](https://i.imgur.com/Sn1yyRt.png)

The last step is to execute ```npm install```. With this final step we are installing the package as a regular dependency. In fact, you can find it inside _node_modules_ folder.

### Back to work

It is time to come back to our regular Angular workflow. This is, to import the FooterModule 

![](https://i.imgur.com/RTmGa4N.png)


and then use Footer component in the template.

![](https://i.imgur.com/F1btI20.png)

Both Hello projects should look like this: 
![](https://i.imgur.com/t4Q1ymi.png)

yai!
We got it :D

### Test it
1. Custom lib: Edit footer background. 
2. Custom lib: Commit and push changes.
3. Hello projects: ```git pull --recurse-submodules``` 
4. Hello projects: Serve and enjoy.

![](https://i.imgur.com/B26uGhJ.png)

Salute!!