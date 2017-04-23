<!-- TITLE: Blockquotes -->
<!-- SUBTITLE: How to use blockquotes -->

# What is blockquote
A blockquote is originally used to define a section that is quoted from another source. However, Wiki.js offers many additional options to the blockquote.

# How to define a blockquote
Simply begin your line of text with a **>**

For example, the following markdown text:

```
> A line of text

> A blockquote with
> 
> multiple lines  
> of text!

> You can even include **styling** in your text, or **icons** :apple:
```

would result in:

> A line of text

> A blockquote with
> 
> multiple lines  
> of text!

> You can even include **styling** *in your text*, or **icons** :apple:

# Available stylings
Various styling options are available:

> Default

> Info
{.is-info}

> Success
{.is-success}

> Warning
{.is-warning}

> Danger
{.is-danger}

Simply add the desired styling class below your blockquote:

```
> Default

> Info
{.is-info}

> Success
{.is-success}

> Warning
{.is-warning}

> Danger
{.is-danger}
```