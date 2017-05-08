---
layout: post
title: "Full Stack Guide"
categories:
  - Web Development
  - Full Stack
tags:
  - Mac
  - Web
  - Development
  - Full Stack
---

# Understanding Everything to Launching Your Website from Scratch to Production - Full Stack Guide

![Stack of Start Ups]({{ site.url }}/images/stack-of-start-ups.jpg)

When I started my journey on becoming a Full Stack Web Developer, it was very difficult for me to figure out the whole picture of setting up a site from scratch. In my opinion, I believe everyone should understand what the whole picture means. It'll help us make better decisions about our stack. A backend who's aware of the frontend will know how to design an API for easier development for the frontend. A mobile developer who's aware of the backend will know how to make better API calls or even ask for reasonable tweaks to the backend so they have an easier app API response. Because of this I've decided to create a graph of everything I've learned about Full Stack Development. This isn't the only way to set up a site, but usually the way it's set up I've seen.

## Understanding the Graph

I'll be explaining everything by referring to the graph. This way you understand why something needs to be there, then be able to visually see where it lies in the stack. Blue highlighted boxes represent  the what the user is aware of, white then represents what developers interact with most of their day and the gray represents what developers may interact with but most likely very rarely and should have someone else dedicated to it. Dashed lines represent something that can be there for better performance boost, but not a must if you're starting out. The highlighted yellow circles is a unique identifier associated with each technology to minimize ambiguity.

## Full Tech Stack

There's a really awesome video that explains some of this at a more macroscopic scale from Tree House [here](https://www.youtube.com/watch?v=i5qpS_D8Law). I want to dig a little deeper then that, because once we learn some frontend and backend development we're still kind of left in the dark to figure out on how to get this developed site to actually be hosted and visible to the world to be seen by more then just your friends and families.

### User Interactions

Lets briefly understand what the user's interactions are. Anyone who will interact with your app or website won't really be aware of your stack. In blue you can see that all they really know is that when they go to app they have to download it from the App Store and launch it from their. If they go to your website then they only know that they will have to launch a browser, perhaps Chrome in this case.  Beyond that they don't know or nor do they care.

### A - Frontend UI/UX

This part of the web is what the user usually sees when they go to your site. They see the user interface of your website. This is usually written in HTML/CSS/Javascript or using React + Redux, Angular, etc. When building a site, people usually have two servers. One server holds the frontend that then makes RESTful API calls to another server, which holds the backend API.

### B - NodeJs or NGINX Webserver

For you to be able to host your frontend on a server, you're going to need to have a webserver, which can be NodeJs or NGINX or something else. There's more webservers but you're going to need one to serve your frontend on a server.

### C - Server

The frontend and webserver then sits on a server which you usually get, like Digital Ocean or a more beginner friendly Heroku. These servers have some type of OS on it.

### F - Backend API

The backend is where your API lies, this is where you develop the brains of your website and make sure the data stored is synced across all developed software. For example if you create an user account on your site, you'd like to handle that information on this side and make sure that if they created that account on your mobile app, they can then use that same log in for the website and then expect the same data to be there. The backend is written by a server side language like Rails or NodeJs + Express or etc. This part can actually by hosted on to the server itself since it already acts as a webserver, but you'd optionally be able to put another webserver in between.

### G - SQL Database

Your backend API only handles the flow of information coming and out but it doesn't persists that data anywhere. For your backend to be able to persists the data of someone who created an account so that they can log in the future, it's persisted into a SQL database.

### H - Amazon Web Services (AWS) Load Balancers

What ends up happening is that people will put a webserver between your backend and your server and the reason behind this is so that it's a load balancer. Which means if you get a lot of traffic on your site and want to make sure your site doesn't get slowed down by a lot people going on your site at the same time. Amazon Web Services is a huge software as a service that not only provides load balancing but other services like a back up server if you'd like one.

### I - Redirect Server NGINX

When you load balance you end up splitting the load up for your server, a redirect server is what will help redistribute workloads across multiple computing resources.

### J - Backend Server

The backend, with your webservers are then hosted on a second server, which can again be Digital Ocean, Heroku, Rackspace, CloudatCost, etc.  That pretty much is your entire website from top to bottom.

### D - Mobile App

Your app follows a similar, but much more simple route, since your app doesn't need to be hosted on a server. It's just developed by you then published to the Google Play Store if it's an Android App or App Store if it's an iOS app. Your mobile app can however also make RESTful API calls to your backend so that it stays in sync with the data of your site or any other developed software. Your app can also store some information locally.

### E - Local Database

If they want to be able to automatically logged in their mobile phone, but not the site since they share the computer at home, that's data that they can locally save on their phone.

## Conclusion

That sums up everything there is to know about created your website from scratch. I hope this helps everyone who are trying to figure out how to create their site from scratch and how they will.
