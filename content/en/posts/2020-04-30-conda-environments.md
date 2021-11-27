---
title: "Conda Environments"
date: 2020-04-30T09:42:49-03:00
type: "post"
draft: false
featured-img: "https://cdn-images-1.medium.com/max/2560/0*EP6R4_j7cHRQnx8z"
topics:
  - Data Science
tags:
  - "Best Practices"
  - "Python"
  - "Conda"
categories:
  - "Best Practices"
  - "Python"
  - "Conda"
description: "Best practices for Conda Environments with Python"
---

No more tears!
If you are a user of conda packages, more precisely [Jupyter Notebook](), as I am, you should worry - a lot! - with your programming environment and your OS. Your _environment_ is one of the barriers that prevent you from cloging your system with all sorts of packages and their - conflicting - versions. Lets be honest, you don't want a crucial package being overwritten on your system do you?

So let's go!

<!--!more-->

## Creating an environment from ground up

```bash
$ conda create --name myenv
```

It is recommended to create your _environment_ already with the packages you want to install, so there is no conflict issues with dependencies. This way

```bash
$ conda create --name myenv python scipy=0.15.0 astroid babel
```

Or

```bash
$ conda create --name myenv
$ conda install -n myenv python scipy=0.15.0 astroid babel
```

Note that:

- Use of package_name=**version** to identify which specific version you want;
- Creating _environments_ this way loads default packages and if you want a **clean** environment you should use:

```bash
$ conda create --no-default-packages -n myenv _packages you want to install_
```

## Creating an environment from an Yaml file

To create an environment from an `.yml|yaml` file, it has to have a specific structure, since the routines from the CLI will look for particular attributes to **name** and install **dependencies** through **channels**.

```yaml
name: myenv
channels:
  - channel_name
dependencies:
  - python
  - scipy=0.15.0
  - astroid
  - babel
```

Awesome, now we do have a starting point: our `env.yml`. Lets go back to the terminal and:

```bash
$ conda env create -f env.yml
```

Respecting the `env.yml` path.

## Updating an environment

There will be a moment when you will miss some dependency or another, versions are not up-to-date or even, there are better packages to work with. This time you will remember how ease `pip` is or even `npm|yarn`.

The best, documentation recomended, way is making a _manual_ update on your `env.yml` file and execute the following:

```bash
$ conda env update --prefix ./env --file env.yml --prune
```

If you are a hasty person, and you cannot be without `pip` there is a way. But before that you need to config conda to use the python package manager.

```bash
$ conda config --set pip_interop_enabled True
```

**Atention!**

Only use `pip` to install new dependencies with your **environment** enabled!

```bash
$ pip install --upgrade-strategy only-if-needed package
$ pip freeze > requirements.txt
```

Or

```bash
$ conda list --explicit > requirements.txt
```

## When its time to work

Like work had never came before eveything, doesn't it?

```bash
$ conda activate
```

And to deactivate

```bash
$ conda deactivate
```

## Useful Commands

```bash
# List Environment
$ conda env list

# Info
$ conda info --envs

# Map dependencies to a text file
$ conda list --explicit > requirements.txt
```

## References

[Conda Documentation](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html)
