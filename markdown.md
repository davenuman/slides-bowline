name: default
layout: true
class: middle

---
name: title
class: center

#Introduction to [Bowline](https://github.com/davenuman/bowline)

## Dockerizing Drupal Projects

![knot](images/320px-Palstek_innen.jpg)
---
class: center
# Developer Experience
### UX for DevOps

???
Ask what might be involved in a positive DX

---
# Developer Experience

 - **Ramp up time**
   - time it takes to start working on a project
 - Context switching
 - Intuitive Tools
 - Consistent patterns

???
 - Autonomy - Mastery - Purpose

---
###  Our Goals

 - Faster developer sandbox set up to get started on projects sooner.

 - Consistent software stack across developers, testing infrastructure, and production.

 - Ideally, a basic tool set that would work for both our new projects as well as our maintenance sites.

---
## Motivation
  - rapid, portable sandbox set up ...even on old maintenance sites
  - consistent stack and tools across team and on ci testing server
- requirements
  - fig changed to docker compose

---

- Use case: start a new Drupal 7 project

### Improving the dev experience...

---
class: center

| Vagrant | Docker |
|:--------|:-------|
| Virtual Machine | Virtual Environment  |

???


---
`. bin/activate`

```bash
[ "$(alias | grep deactivate)" ] && deactivate  # In case already activated.
GIT_ROOT=$(git rev-parse --show-toplevel)
alias deactivate="export PATH=$PATH; export PS1=\"$PS1\"; unset BOWLINE"
export PATH=$GIT_ROOT/bin:$PATH
export BOWLINE=${GIT_ROOT##*/}

if [ "$SHELL_TYPE" = "bash" ];then
  export PS1="${PS1}\[\033[01;31m\](${BOWLINE})\[\033[00m\] \$ "
else
  export PS1="${PS1} (${BOWLINE}) \$ "
fi
```

???
This is really important... when activated, new commands are available in your current shell environment. Some of those override commands you may already have such as drush, composer

---
## Bowline activated

```
Available commands:
activate  bowline  composer  fix-perms	invoke_proxy  settings_init
backup	  build    drush     import	run

Containers:
db   ~  172.17.0.61
web  ~  172.17.0.62  http://172.17.0.62/
Proxy:
	http://bowline.localtest.me/
```

---
class: center
![D8](images/drupal8.png)

???
Yes, it works with D8.

---
## Issues

- Performance in boot2docker
- Incomplete set of tools

---
# Questions?
.footnote[Slideshow created using [remark](http://github.com/gnab/remark).]
