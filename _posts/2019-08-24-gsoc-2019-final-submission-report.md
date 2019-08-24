---
layout: post
title:  "Google Summer of Code 2019 Final Project Report"
author: "Sukhbir Singh"
---

![Google Summer of Code Image](https://github.com/sukhbir-singh/blog/raw/master/assets/images/gsoc_image.png "Google Summer of Code Image")

Hi there, 
I am Sukhbir Singh, a final year student of National Institute of Technology Hamirpur. For last 3 months, I have worked with "Amahi" organization as a Google Summer of Code student developer. Amahi is one the best open source media server software available right now. Platform is the core sofware of Amahi and it is in development from last 7 years. Amahi 11 officially released last year in 2018 and provides support for fedora 27. In this report, I would like to mention everything i have worked on during this period.

## Project Details
Student: Sukhbir Singh ([sukhbir-singh](https://github.com/sukhbir-singh))

Mentor: Carlos Puchol ([cpg](https://github.com/cpg))

Organization: [Amahi](https://github.com/amahi)

GSoC Proposal Link: [Amahi 12 Improvements](https://summerofcode.withgoogle.com/projects/#4847686564446208)


## Introduction
The aim of my proposal for this year's GSoC is to implement new features for Amahi 12. Also implementing new plugins and maintaining existing plugins for Amahi system.


### Objectives Achieved:-
1. Developed various new features and improvements for Amahi platform.
2. Implemented friending feature for Amahi 12 using which Amahi users can share their Shares with other Amahi users.
3. Improved and maintained disk wizard and web apps plugin for Amahi 12.
4. Implemented most of the parts of lets encrypt feature. This feature will help to provide support for certificate generation required for establishing secure connection with subdomains of yourhda.com for Amahi.


## Implementations

### 1. Platform
- Improved search results page front-end of platform using bootstrap 4. PR: [#234](https://github.com/amahi/platform/pull/234)
- Fixed and improved pagination of search results page. PR: [#236](https://github.com/amahi/platform/pull/236)
- Updated Dockerfile with required configurations for Amahi 12 such as using Fedora 29 as base operating system, Rails 5.2.0, etc. and using this updated Dockerfile I have built new "amahi_platform" image with tag "latest" and uploaded it on Docker Hub. PRs: [#237](https://github.com/amahi/platform/pull/237), [#239](https://github.com/amahi/platform/pull/239)
* Amahi 12 Docker Image: [https://hub.docker.com/r/sukhbir947/amahi_platform](https://hub.docker.com/r/sukhbir947/amahi_platform)
- Added .dockerignore file. This helps in excluding files not relevant to build. And so reduces overall image size and prevents adding unnecessary files to build the image. PR: [#238](https://github.com/amahi/platform/pull/238)
- Fixed App instructions box sliding-off-screen problem in platform. PR: [#240](https://github.com/amahi/platform/pull/240)
- Made app description consistent and single line across themes. PR: [#241](https://github.com/amahi/platform/pull/241)
- Added component to Apps Tab for showing app installation status on reload. PR: [#242](https://github.com/amahi/platform/pull/242)

### 2. Friending
  **2.1 Friending Plugin**
  - Fixed UI and implemented changes to the plugin as per requirements. 
  - Now after making request to Amahi.org backend server for creating friend request, a copy of friend request is also maintained on local HDA which will later be used for creating friend user when its related friend request got accepted.
  - Implemented short polling for updating friend users asynchronously with Amahi.org friending server. Wrote rake task for running it as cron job.
  - Repo link: [https://github.com/amahi/friending-plugin](https://github.com/amahi/friending-plugin)

  **2.2 Friending Rails Backend**
  - Implemented all the APIs for this friending feature from scratch. This backend server needs to be hosted on Amahi.org server with some modifications.
  - Discussed all the corner cases with mentors and implemented solutions for handling each of them.
  - Synced this backend with the requirements of plugin and Amahi android, ios clients.
  - Repo link: [https://github.com/sukhbir-singh/amahi-friending-backend](https://github.com/sukhbir-singh/amahi-friending-backend)

### 3. Disk Wizard Plugin
- Initially disk wizard plugin had lot of problems due to various crashes and bugs for Amahi 12. I have fixed all these bugs and crashes related to this disk wizard plugin. Also improved front end of the entire plugin. PR: [#23](https://github.com/amahi/disk-wizard/pull/23), [#24](https://github.com/amahi/disk-wizard/pull/24), [#25](https://github.com/amahi/disk-wizard/pull/25), [#26](https://github.com/amahi/disk-wizard/pull/26)

### 4. Web Apps Plugin
- Solved issue with web apps submit button - UI got stuck when someone click on submit button for creating new web app using this plugin. PR: [#1](https://github.com/amahi/web-apps/pull/1)

### 5. Let's Encrypt
 - Maintained all three repos of lets encrypt. Particularly implemented plugin and backend server part.

  **5.1 Let's Encrypt Plugin**
  - Lets encrypt plugin will show status of last successful certificate generated and also provides an interface for performing actions like deleting certificate, regenerating new certificate, etc. For performing any actions or checking statuses related to certificates, plugin will request Let's encrypt backend server which will further request cert factory server whenever required.
  - This plugin will also be responsible for configuring existing web apps on platform. 
  - Repo link: [https://github.com/sukhbir-singh/lets-encrypt-plugin](https://github.com/sukhbir-singh/lets-encrypt-plugin)

  **5.2 Let's Encrypt Backend Server**
  - This server will be hosted on Amahi.org and will interact with plugin and cert factory for performing various actions.
  - A dashboard is also provided to admin in this backend server using which he can generate new certificate, delete certificate, etc for existing users and can also view statuses of last certificate generations.
  - This server will make API calls to cert factory server for performing various certificate related actions and also maintain last certificate statues in a database table for dashboard and loggin purpose.
  - Repo link: [https://github.com/sukhbir-singh/lets-encrypt-backend-server](https://github.com/sukhbir-singh/lets-encrypt-backend-server)

  **5.3 Let's Encrypt Cert Factory**
  - Cert factory server is maintained isolated for lets encrypt backend server for security reasons and to serve only the purpose of dealing with certificates. 
  - This will internally uses lets encrypt APIs for requesting new certificates, deleting old certificates etc.
  - Repo link: [https://github.com/sukhbir-singh/amahi-cert-factory](https://github.com/sukhbir-singh/amahi-cert-factory)


## Code Links

### Platform

Repository Link: [https://github.com/amahi/platform](https://github.com/amahi/platform)

Merged Pull Requests: [amahi/platform/pulls-closed](https://github.com/amahi/platform/pulls?q=author%3Asukhbir-singh+created%3A%3E2019-05-27+is%3Aclosed)

Opened Pull Requests: [amahi/platform/pulls-opened](https://github.com/amahi/platform/pulls?q=author%3Asukhbir-singh+created%3A%3E2019-05-27+is%3Aopen)

### DockerHub Repo

Docker Repository Link: [sukhbir947/amahi_platform](https://hub.docker.com/r/sukhbir947/amahi_platform)

### Friending Plugin

Repository Link: [https://github.com/amahi/friending-plugin](https://github.com/amahi/friending-plugin)

All Commits: [amahi/friending-plugin/commits](https://github.com/amahi/friending-plugin/commits?author=sukhbir-singh&since=2019-05-27&until=2019-08-20)

### Friending Rails Backend

Repository Link: [https://github.com/sukhbir-singh/amahi-friending-backend](https://github.com/sukhbir-singh/amahi-friending-backend)

All Commits: [sukhbir-singh/amahi-friending-backend/commits](https://github.com/sukhbir-singh/amahi-friending-backend/commits?author=sukhbir-singh&since=2019-05-27&until=2019-08-20)

### Disk Wizard Plugin

Repository Link: [https://github.com/amahi/disk-wizard](https://github.com/amahi/disk-wizard)

All Commits: [amahi/disk-wizard/commits](https://github.com/amahi/disk-wizard/commits?author=sukhbir-singh&since=2019-05-27&until=2019-08-20)

Pull Requests: [amahi/disk-wizard/pulls](https://github.com/amahi/disk-wizard/pulls?utf8=%E2%9C%93&q=author%3Asukhbir-singh+is%3Aclosed+created%3A%3E2019-05-27)

### Web Apps Plugin

Pull Request: [amahi/web-apps/pulls](https://github.com/amahi/web-apps/pull/1)

### Let's Encrypt Plugin

Repository Link: [https://github.com/sukhbir-singh/lets-encrypt-plugin](https://github.com/sukhbir-singh/lets-encrypt-plugin)

All Commits: [sukhbir-singh/lets-encrypt-plugin/commits](https://github.com/sukhbir-singh/lets-encrypt-plugin/commits?author=sukhbir-singh&since=2019-05-27&until=2019-08-20)

### Let's Encrypt Backend Server

Repository Link: [https://github.com/sukhbir-singh/lets-encrypt-backend-server](https://github.com/sukhbir-singh/lets-encrypt-backend-server)

All Commits: [sukhbir-singh/lets-encrypt-backend-server/commits](https://github.com/sukhbir-singh/lets-encrypt-backend-server/commits?author=sukhbir-singh&since=2019-05-27&until=2019-08-20)

### Let's Encrypt Cert Factory

Repository Link: [https://github.com/sukhbir-singh/amahi-cert-factory](https://github.com/sukhbir-singh/amahi-cert-factory)

All Commits: [sukhbir-singh/amahi-cert-factory/commits](https://github.com/sukhbir-singh/amahi-cert-factory/commits?author=sukhbir-singh&since=2019-05-27&until=2019-08-20)


## Future Work

There is always a scope of improvements. Softwares need maintainence to keep working fine in new changing environments. With newer versions of Amahi got released in order to support latest fedora versions, plugins for the same needs maintainance. Friending feature needs to be adapted for Amahi.org. Most of the work in Let's encrypt feature is complete but still needs some development.


## Conclusion

I really enjoyed contributing to Amahi and learned lots of new things in the way. This was my second time doing Google Summer of Code with Amahi. Thanks to this awesome program, I can say that i have become a better software developer overall and now i am not afraid to contribute to big codebase projects. I would also like to thanks [@cpg](https://github.com/cpg) for mentoring me so well during this program. During this period, I have gained lots of new skills related to coding, software maintainance, system design, etc that will always help me in my career ahead. 


