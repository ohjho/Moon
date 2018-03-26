---
layout: post
title:  "Connecting to an AWS Windows virtual machine"
date:   2018-03-26
excerpt: ""
categories: dev
tags: [aws, remote desktop]
comments: true
---

## Already created an AWS account and an instance of Windows?
on Mac you can remote connect to it using `rdesktop`  

Just run `brew install rdesktop`... you might need to `brew install xquartz` first

## Using `rdesktop`
Open `XQuartz` (maybe from Spotlight)

And in the `XQuartz` terminal, run `rdesktop ec123-your-awsaddress.compute.amazonaws.com`
