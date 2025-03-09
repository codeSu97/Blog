---
title: "{{ replace .Name "-" " " | title }}"
description:
date: "{{ .Date }}"
url: "/post/{{ replace .Name "-" " " | title }}/"
image: ""
math: true
license: false
hidden: false
comments: false
draft: true
tags:
categories:
---