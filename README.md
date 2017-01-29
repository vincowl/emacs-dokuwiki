# emacs-dokuwik
Edit remote Dokuwiki pages using XML-RPC

# Overview #
Emacs-Dokuwiki is a package that provides a way to edit a remote Dokuwiki wiki through Emacs. The package uses [Dokuwiki's XML-RPC API](https://www.dokuwiki.org/devel:xmlrpc).

Package is still under development. Currently, the package can edit, create, and save pages. Will be adding more convenience functions to make the process easier in the near future.

# Installation #
Download Emacs-Dokuwiki from Github.

``` emacs-lisp
git clone https://github.com/accidentalrebel/emacs-dokuwiki.git
```

Add this to your init:

``` emacs-lisp
require 'emacs-dokuwiki
```

## Dependencies ##
  * The latest version of XML-RPC.el.

# Usage #

## Logging In ##
The first thing to do is to login using the `emacs-dokuwiki-login` function. Once successfully logged in the user can now be able to use the other available functions.

**Note**
To avoid entering the *xml-rpc-url* and the *login-user-name* everytime you login consider setting the `emacs-dokuwiki-xml-rpc-url` and `emacs-dokuwiki-login-user-name` variables on Emacs startup as seen below.

``` emacs-lisp
(setq emacs-dokuwiki-xml-rpc-url "http://www.url-of-wiki.com/lib/exe/xmlrpc.php")
(setq emacs-dokuwiki-login-user-name "username-of-user")
```

## Opening a page ##
The function `emacs-dokuwiki-open-page` will download the contents of the wiki page specified by the user. If the specified page does not exist then the page is created on the remote wiki once the page is saved.

**Note**
To open a page in a particular namespace add the namespace name before the page-name. For example, *namespace:wiki-page* to open the *wiki-page* page inside the *namespace* namespace.

## Saving a page##
The function `emacs-dokuwiki-save-page` will save the contents of the current *.dwiki* buffer to the remote wiki. This function uses the buffer name as the page name to be used when saving. A buffer of *wiki-page.dwiki* is saved as *wikiurl.com/wiki-page*. On the other hand, a buffer of *namespace:wiki-page.dwiki* is saved as *wikiurl.com/namespace:wiki-page*.

**Note**
This function is intended to be called on a buffer created after opening a page. This will still work on any buffer as long as the buffer has a *.dwiki* at the end of it's buffer name.

# Miscellaneous #
  * After opening a page consider using the [emacs-dokuwiki-mode](https://github.com/kai2nenobu/emacs-dokuwiki-mode) or [dokuwiki-mode](https://github.com/kai2nenobu/emacs-dokuwiki-mode) for easy editing of the buffers.
  
# Contributing #
Contributions are always welcome. Feel free to submit a pull request, create an issue, or send suggestions.

# To Do #
  * Use auth-source in storing login credentials
  * Create a function that displays a list of available pages
  * Should be able to open a page even if a full url is entered
