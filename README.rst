==============================================
 Jedi.el - a Python auto-completion for Emacs
==============================================

.. warning:: Work in progress!


Jedi.el is a Python auto-completion package for Emacs.  It uses jedi_
library to compute completion and EPC_ (an RPC stack for Emacs Lisp)
and its `Python binding`_ to commentate with Python process.  It also
uses excellent Emacs auto-complete_ module to start completion
automatically.

.. _jedi: https://github.com/davidhalter/jedi
.. _EPC: https://github.com/kiwanami/emacs-epc
.. _Python binding: python-epc_
.. _python-epc: https://github.com/tkf/python-epc
.. _auto-complete: https://github.com/auto-complete/auto-complete


Install
=======

el-get
------

The easiest way to install Jedi.el is to use el-get_:
just do ``M-x el-get-install jedi``.
You need to have `virtualenv` to automatically install Python module
dependencies.  If your el-get does not have the recipes for Jedi.el
yet, get them from `this pull request`_.

.. _el-get: https://github.com/dimitri/el-get
.. _this pull request: https://github.com/dimitri/el-get/pull/927

Manual install
--------------

1. Install EPC_ and auto-complete_.
2. Install Jedi.el.  Download this repository and add it to
   `load-path`.
3. Install Jedi_ and python-epc_ by ``make requirements`` or ``pip
   install jedi epc`` if you want to determine where to install them.
   If you don't use the make command, you need to set
   `jedi:server-command` appropriately.
4. Add ``(require 'jedi)`` in your Emacs configuration.


Setup
=====

All you need to do is to call `jedi:ac-setup` in python buffer.
To do that, add the following in your Emacs configuration::

   (add-hook 'python-mode-hook 'jedi:ac-setup)

If you want to manually invoke completion, use something like this::

   (define-key python-mode-map (kbd "<C-tab>") 'jedi:complete)