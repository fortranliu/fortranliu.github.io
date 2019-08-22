---
layout: post
title:  "matplotlib"
date:   2019-01-12 10:22
categories: 技术文档
tags: matplotlib
---

#matplotlib

Matplotlib has two interface:

- an object-oriented (OO) interface: utilize an instance of `axes.Axes` in order to render visualizations on an instance of `figure.Figure`
- based on MATLAB and uses a state-based interface: encapsulated in the `pyplot` module

Things to remember:

- The Figure is the final image that may contain 1 or more Axes.
- The Axes represent an individual plot (don't confuse this with the word "axis", which refers to the x/y axis of a plot).

[The Lifecycle of a Plot](https://matplotlib.org/tutorials/introductory/lifecycle.html#sphx-glr-tutorials-introductory-lifecycle-py)

[Blog post by Chris Moffitt](http://pbpython.com/effective-matplotlib.html)

##Figure
The figure keeps track of child `Axes` and a figure can have any number of `Axes`

```
fig = plt.figure()  # an empty figure with no axes
fig.suptitle('No axes on this figure')  # Add a title so we know which it is
fig, ax_lst = plt.subplots(2, 2)  # a figure with a 2x2 grid of Axes
```

##Axes

##Axis
- location of ticks is determined by `Locator`
- ticklabel strings are formatted by `Formatter`


#matplotlib.rcParams

##matplotlibrc files
matplotlib uses `matplotlibrc` configuration files to customize all kinds of properties, which we call `rc settings` or `rc parameters`. You can control the defaults of almost every property in matplotlib: figure size and dpi, line width, color and style, axes, axis and grid properties, text and font properties and so on. 

[The matplotlibrc files](https://matplotlib.org/tutorials/introductory/customizing.html#customizing-with-matplotlibrc-files)

##matplotlib.rcParams
You can also dynamically change the default rc settings in a python script or interactively from the python shell. All of the rc settings are stored in a dictionary-like variable called `matplotlib.rcParams`, which is global to the matplotlib package. rcParams can be modified directly, for example:

```
mpl.rcParams['lines.linewidth'] = 2
mpl.rcParams['lines.color'] = 'r'
plt.plot(data)
```

The `matplotlib.rc()` command can be used to modify multiple settings in a single group at once, using keyword arguments:

```
mpl.rc('lines', linewidth=4, color='g')
plt.plot(data)
```

#matplotlib.pyplot

##Working with multiple figures and axes
`pyplot` has the concept of the current figure and the current axes. All plotting commands apply to the current axes. The function `gca()` returns the current axes (a `matplotlib.axes.Axes` instance), and `gcf()` returns the current figure (`matplotlib.figure.Figure` instance). Normally, you don't have to worry about this, because it is all taken care of behind the scenes. 

```
import matplotlib.pyplot as plt
plt.figure(1)                # the first figure
plt.subplot(211)             # the first subplot in the first figure
plt.plot([1, 2, 3])
plt.subplot(212)             # the second subplot in the first figure
plt.plot([4, 5, 6])


plt.figure(2)                # a second figure
plt.plot([4, 5, 6])          # creates a subplot(111) by default

plt.figure(1)                # figure 1 current; subplot(212) still current
plt.subplot(211)             # make subplot(211) in figure1 current
plt.title('Easy as 1, 2, 3') # subplot 211 title
```

##LaTex
There are two ways to use LaTex:

- `mathtex`
- Tex rendering with LaTex

---
[Matplotlib usage guide](https://matplotlib.org/tutorials/introductory/usage.html#sphx-glr-tutorials-introductory-usage-py)