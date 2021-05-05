<p align="center"><img src="https://user-images.githubusercontent.com/43980777/109386965-eefed000-7930-11eb-8b83-ef85d70196fa.png"></p>
<p align="center">Portable horizontal ruler for terminal</p>
<p align="center"><a href="https://github.com/NNBnh/hr/blob/main/LICENSE"><img src="https://img.shields.io/github/license/NNBnh/hr?labelColor=073551&color=4EAA25&style=for-the-badge" alt="License: GPL-3.0"></a> <img src="https://img.shields.io/badge/development-completed-%234EAA25.svg?labelColor=073551&style=for-the-badge&logoColor=FFFFFF" alt="Development completed"></p>
<p align="center"><a href="https://github.com/NNBnh/hr/watchers"><img src="https://img.shields.io/github/watchers/NNBnh/hr?labelColor=073551&color=4EAA25&style=flat-square"></a> <a href="https://github.com/NNBnh/hr/stargazers"><img src="https://img.shields.io/github/stars/NNBnh/hr?labelColor=073551&color=4EAA25&style=flat-square"></a> <a href="https://github.com/NNBnh/hr/network/members"><img src="https://img.shields.io/github/forks/NNBnh/hr?labelColor=073551&color=4EAA25&style=flat-square"></a> <a href="https://github.com/NNBnh/hr/issues"><img src="https://img.shields.io/github/issues/NNBnh/hr?labelColor=073551&color=4EAA25&style=flat-square"></a></p>

## 💡 About
![`hr`](https://user-images.githubusercontent.com/43980777/109386947-cd054d80-7930-11eb-90b3-49836d184f25.png) (SuperB HR) is a CLI tool written in [`portable sh`](https://github.com/dylanaraps/pure-sh-bible) to render horizontal ruler/line in the terminal.

### 📔 Story
Recently, i'm obsessed with [`hr`](https://github.com/LuRsT/hr) and i want a portable shell `hr`, the best i found is *"`POSIX`-ish Way"* from the blog [Alternatives to the `hr` library](https://grayson.sh/blogs/some-alternatives-to-hr):

```sh
printf '%*s' "$(tput cols)" | tr ' ' "${*:-#}"
```

but it lacks [Gil Gonçalves's `hr`](https://github.com/LuRsT/hr) key features like output multiple line, custom text or even treats multi-byte symbols properly. So i decided to create ![`hr`](https://user-images.githubusercontent.com/43980777/109386947-cd054d80-7930-11eb-90b3-49836d184f25.png) based on the blog's method with only **6 lines** of [`portable sh`](https://github.com/dylanaraps/pure-sh-bible):

```sh
#!/bin/sh
COLUMNS="${COLUMNS:-$(tput cols)}"
for text in "${@:-${HR_DEFAULT_TEXT:-─}}"; do
	printf '%*s' "$COLUMNS" | sed -e "s/ /$text/g" -e "s/^\(.\{$COLUMNS\}\).*/\1/"
done
exit 0
```

### ✨ Features
- Extremely **minimum** *"only **6 lines** of [`portable sh`](https://github.com/dylanaraps/pure-sh-bible)"*
- Can output **multiple lines** at once
- Can define **custom text**
- Treats **multi-byte symbols** properly
- ![`hr`](https://user-images.githubusercontent.com/43980777/109386947-cd054d80-7930-11eb-90b3-49836d184f25.png)'s default text can be change through [environment variable](#%EF%B8%8F-configuration)

> *![`hr`](https://user-images.githubusercontent.com/43980777/109386947-cd054d80-7930-11eb-90b3-49836d184f25.png) can not be `source` or invoke from [Bash](https://www.gnu.org/software/bash), for that use [Gil Gonçalves's `hr`](https://github.com/LuRsT/hr)*

## 🚀 Setup
### 🧾 Dependencies
- `sh` to process

### 📥 Installation
#### 🔧 Manually
- Option 1: using `curl`

```sh
curl https://raw.githubusercontent.com/NNBnh/hr/main/bin/hr > ~/.local/bin/hr
chmod +x ~/.local/bin/hr
```

- Option 2: using `git`

```sh
git clone https://github.com/NNBnh/hr.git ~/.local/share/hr
ln -s ~/.local/share/hr/bin/hr ~/.local/bin/hr
```

#### 📦 Package manager
For [`bpkg`](https://github.com/bpkg/bpkg) user:

```sh
bpkg install NNBnh/hr
```

For [Basher](https://github.com/bpkg/bpkg) user:

```sh
basher install NNBnh/hr
```

> *If you can and want to port SuperB HR to other package managers, feel free to do so.*

## ⌨️ Usage
Run ![`hr`](https://user-images.githubusercontent.com/43980777/109386947-cd054d80-7930-11eb-90b3-49836d184f25.png) in the terminal:

```sh
hr [TEXTS]
```

Examples:

```sh
hr
```

this will output:

```console
────────────────────────────────────────
```

You can make multiple ![`hr`](https://user-images.githubusercontent.com/43980777/109386947-cd054d80-7930-11eb-90b3-49836d184f25.png) at the same time and with any `TEXT`:

```sh
hr '#' 'hr' 'Hello world! '
```

this will output:

```console
########################################
hrhrhrhrhrhrhrhrhrhrhrhrhrhrhrhrhrhrhrhr
Hello world! Hello world! Hello world! H
```

## ⚙️ Configuration
![`hr`](https://user-images.githubusercontent.com/43980777/109386947-cd054d80-7930-11eb-90b3-49836d184f25.png) is configured through environment variables:

```sh
export HR_DEFAULT_TEXT="<text>"
```

## 💌 Credits
Special thanks to:
- [**hr**](https://github.com/LuRsT/hr) by [Gil Gonçalves](https://github.com/LuRsT)
- [**Alternatives to the 'hr' library**](https://grayson.sh/blogs/some-alternatives-to-hr) by [Grayson Kent](https://grayson.sh)

<br><br><br><br>

---

> <h1 align="center">Made with ❤️ by <a href="https://github.com/NNBnh"><i>NNB</i></a></h1>
>
> <p align="center"><a href="https://www.buymeacoffee.com/nnbnh"><img src="https://img.shields.io/badge/buy_me_a_coffee%20-%23F7CA88.svg?logo=buy-me-a-coffee&logoColor=333333&style=for-the-badge" alt="Buy Me a Coffee"></p>
