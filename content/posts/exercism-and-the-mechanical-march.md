---
title: "Mechanical March Challenge: Learning Golang with the Help of a Nix Flake"
date: 2023-03-02T15:15:22-03:00
draft: false
tags: [exercism, 12in23, golang, nix, study]
comments: true
---

If you're looking for a way to challenge yourself and improve your programming skills, the Exercism Mechanical March challenge is a great opportunity. This month, I decided to take on the challenge and tackle the Golang track.

To make the process smoother and more efficient, I prepared a Nix flake that would help me in the development of the exercises. If you're not familiar with Nix, it's a package manager that allows for deterministic builds and is particularly helpful when working with multiple dependencies.

With the Nix flake, I was able to quickly and easily set up my development environment for the Golang track, install all the necessary dependencies, and start working on the exercises. This saved me a lot of time and hassle, as I didn't have to worry about managing dependencies manually or dealing with version conflicts.

The tracks on Exercism are a great way to learn a programming language and practice writing idiomatic code. The exercises are challenging but also fun and rewarding, and the feedback from the community is incredibly helpful for improving your skills.

If you're interested in taking on the Mechanical March challenge or learning Golang in general, I highly recommend checking out the Exercism Golang track and using a Nix flake to streamline your development process. Happy coding!


**Feel free to clone my repository and produce code with higher productivity.**

I wrote a post that explain how you can run the nix on your computer. [Read here.]({{< relref path="using-nix-for-productivity.md" lang="en" >}})

1. Clone the repository and enter on shell golang directory
```
git clone https://github.com/douglastofoli/nix-configs.git && cd nix-configs/shells/golang
```

2. On file `flake.nix`, make sure that variable enableExercism to be set to `true`. If you want to use the flake with Golang for development environment, turn this variable value to `false`. Exercism is just for study environment.

3. All done just run the command:
```
direnv allow
```

All packages necessary will be installed locally.

4. Then you need to create your Exercism token, {{< external-link url="https://exercism.org/settings/api_cli" text="here" >}}. _(An account is necessary)_

Create `.env` file with:
```
cp .env.example .env
```

And put your token on variable `EXERCISM_TOKEN=`

5. Finally run the last command to refresh your Nix Flake
```
direnv reload
```
  
{{< break >}}

All ready. If everything went well, you should be able to run go and exercim directly from the golang directory. When leaving the directory all packages will be unloaded from your system, being loaded again when entering the directory again.

Embark on this journey with me and let's learn together more and more.
