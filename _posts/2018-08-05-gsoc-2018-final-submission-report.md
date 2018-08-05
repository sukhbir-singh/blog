---
layout: post
title:  "Google Summer of Code 2018 Final Submission Report"
author: "Sukhbir Singh"
---

![Google Summer of Code Image](https://github.com/sukhbir-singh/blog/raw/master/assets/images/gsoc_image.png "Google Summer of Code Image")

Hello, 
I am Sukhbir Singh, an undergraduate from National Institute of Technology Hamirpur. I worked with [Amahi](https://github.com/amahi/) Organization as Google Summer of Code Student over last summer. It was the most exciting summer I ever had. Weekly meetings, Daily challenges, Discussion about Silicon Valley culture, Learning more about Ruby on Rails framework, Making good connections and what else could we imagine.

During this period, I have worked with the core team of Amahi to develop features and functionalities for the latest release of Amahi known as **Amahi 11**, which is the newer version of Linux powered home server. 

## Project Details

- Student: Sukhbir Singh
- Github: [https://github.com/sukhbir-singh](https://github.com/sukhbir-singh)
- GSoC Project Link: [Amahi 11 Improvements](https://summerofcode.withgoogle.com/projects/#6139448354406400)
- Organization: [Amahi](https://github.com/amahi/)

This project requires working knowledge of Ruby on Rails, Javascript, and Web development. Along with other CS fundamentals like caching, ssh, operating system etc. 

Goals Achieved:-
- Improved entire front-end of platform using bootstrap-4.
- Fixed existing bugs of platform and helped in upgrading the project to Rails 5.2 version.
- Provided support to dynamic theme installation.
- Makes apps installation on platform more reliable and user-friendly and also providing caching support to it. 
- Implemented new plugins from scratch and provided support to existing plugins.
- Implemented sharing of folders among the friend servers, also called friending feature. Some parts of this feature are still in progress.

Each plugin adds a new feature to the system. As part of this project, I have developed plugins for detecting hard drive failures using S.M.A.R.T status, and a plugin for creating incremental backups periodically which is based on Rsnapshot tool. 

Lastly, I have collaborated with another GSoC student Chirag, to implement friending feature for Amahi. This feature aims to provide sharing functionality of folders among friends. This feature consists of two parts - implementing REST APIs and developing friending plugin and providing this plugin support in platform. I did the Implementation of friending plugin and platform support part. By using the friending plugin an Amahi user can add friends and can give them access to their folders and can manage friend requests sent. 

## Code Links

### Amahi/Platform

Repository: [https://github.com/amahi/platform](https://github.com/amahi/platform)

Merged Pull Requests: [amahi/platform pull-requests author:sukhbir-singh](https://github.com/amahi/platform/pulls?q=is%3Apr+author%3Asukhbir-singh+is%3Aclosed)

Commits: [amahi/platform commits author=sukhbir-singh](https://github.com/amahi/platform/commits/r52-bs4-app-installs?author=sukhbir-singh)

### RSnapshot Plugin

Repository: [https://github.com/amahi/rsnapshot-backup-plugin](https://github.com/amahi/rsnapshot-backup-plugin)

Commits: [amahi/rsnapshot-backup-plugin commits author=sukhbir-singh](https://github.com/amahi/rsnapshot-backup-plugin/commits?author=sukhbir-singh)

### SMART Status Plugin

Repository: [https://github.com/amahi/smart-status-plugin](https://github.com/amahi/smart-status-plugin)

Commits: [amahi/smart-status-plugin commits author=sukhbir-singh](https://github.com/amahi/smart-status-plugin/commits?author=sukhbir-singh)

### Bug fixes in other plugins

Disk-Wizard Plugin PRs: [amahi/disk-wizard pulls author=sukhbir-singh](https://github.com/amahi/disk-wizard/pulls?q=is%3Apr+author%3Asukhbir-singh)

Greyhole Plugin PRs: [amahi/greyhole pulls author=sukhbir-singh](https://github.com/amahi/greyhole/pulls/sukhbir-singh)

### Friending Plugin (In Progress)

Repository: [https://github.com/sukhbir-singh/friending-plugin](https://github.com/sukhbir-singh/friending-plugin)

Commits: [sukhbir-singh/friending-plugin commits author=sukhbir-singh](https://github.com/sukhbir-singh/friending-plugin/commits?author=sukhbir-singh)

## Implementation

### Amahi/Platform

Platform is the core repository of Amahi. I did the following changes and improvements:- 
- Worked on to make the entire front-end of platform responsive using bootstrap-4. PRs for the same is [here](https://github.com/amahi/platform/pull/196).
- Implemented caching support to apps installation using memcached and made the process reliable for users by preventing multiple installations and showing dynamic progress on the front end. The code is [here](https://github.com/amahi/platform/pull/210).
- Helped in upgrading app to latest Rails version 5.2, particularly solved security issues related to the mass assignment of model attributes by using Rails-5 strong parameters feature. The code for this is [here](https://github.com/amahi/platform/pull/180). 
- Fixed issues from existing themes and implemented beach theme. Code links: [PR#192](https://github.com/amahi/platform/pull/192), [PR#201](https://github.com/amahi/platform/pull/201), [PR#203](https://github.com/amahi/platform/pull/203).
- Added additional login support for the user by adding PIN to user’s model and did corresponding front end changes. Code [here](https://github.com/amahi/platform/pull/195).
- Fixed existing issues in JS files, Rspec tests, and slow loading problem of apps listing. Relevant code links: [PR#188](https://github.com/amahi/platform/pull/188), [PR#191](https://github.com/amahi/platform/pull/191), [PR#194](https://github.com/amahi/platform/pull/194), [PR#207](https://github.com/amahi/platform/pull/207), [PR#209](https://github.com/amahi/platform/pull/209/files), [PR#221](https://github.com/amahi/platform/pull/221).

### SMART Status Plugin and RSnapshot Plugin

- Developed SMART Status Plugin which lists all the hard drives attached to the system along with their [S.M.A.R.T](https://en.wikipedia.org/wiki/S.M.A.R.T.) status. The code for this plugin is [here](https://github.com/amahi/smart-status-plugin/commits?author=sukhbir-singh).
- Implemented RSnapshot based plugin for creating incremental backups. The user can set periodicity of the backups as per his needs. The code is [here](https://github.com/amahi/rsnapshot-backup-plugin/commits?author=sukhbir-singh).
- Resolved routing errors in Greyhole UI Plugin. The code is [here](https://github.com/amahi/greyhole/pulls/sukhbir-singh). Added support for Rails 5.2 in Disk Wizard Plugin, also fixed layouts and Javascripts. The code is [here](https://github.com/amahi/disk-wizard/pulls?q=is%3Apr+author%3Asukhbir-singh).

### Friending Plugin (In Progress)

- Friending plugin is used to implement friending feature in platform. This feature allows one Amahi user to befriend another Amahi user so that friend user can access folders of primary user. Primary user can set levels of access permission for that user corresponding to each folder shared with him.
- The requirements of this feature, API specs, and flow diagram is [here](https://docs.google.com/document/d/14JsH9-aZrE3Z-35Oo38IY1-3Nd5BJiR_G0DshhjKSM4/edit). This doc is prepared by me and chirag for documenting and understanding the requirements of this plugin.
- The development of this plugins is still in progress. The code can be found [here](https://github.com/sukhbir-singh/friending-plugin/commits?author=sukhbir-singh).

## Future Work

 Amahi platform is a large codebase and is a bit complex to understand at first. The project has lots of scope for future improvements. Asset pipeline's implementation can be improved. More plugins can be developed in order to add more functionalities to the system. Front-End parts of other existing plugins can be improved. More REST APIs could be developed as per requirements of the users which can be consumed by Android and iOS apps.

## Conclusion

At last, I want to thanks Google and Amahi for this great opportunity. Google Summer of Code is one of the best programs a student can participate in during his graduation years. Amahi organization is very welcoming and responsive to new contributors. It is because of this friendly community and people only that kept me engaged and motivated for contributions during this period. Also, I want to mention, my mentor [@cpg](https://github.com/cpg), who is one of the best person I ever interacted with. He managed things really well and is always there for help whenever I needed. It is fun overall and I have learned a lot in the process.

Thanks for reading!
