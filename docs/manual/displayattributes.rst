.. _display-attributes:

**********************
  Display Attributes  
**********************

Urwid supports a number of common display attributes.

=============================== ================= ===== ============= =====================
Attribute Support by Terminal   xterm, gnome-term rxvt  linux console others
=============================== ================= ===== ============= =====================
16 standard foreground colors   YES               YES   YES           very widely supported
8 standard background colors    YES               YES   YES           very widely supported
default foreground/background   YES               YES   YES           widely supported
bold, underline, standout       YES               YES   standout      widely supported
"bright" background colors      YES               urxvt               some support
256-color foreground/background YES                                   some support
88-color foreground/background  w/palette setting urxvt               limited support
RGB palette setting             YES                                   limited support
=============================== ================= ===== ============= =====================

You are encouraged to provide support for as many of these as you like, while
allowing your interface to degrade gracefully by using display modules' palette
modes and providing command line arguments or other interfaces to switch modes.

When setting up a palette with :class:`~urwid.main_loop.MainLoop` (or directly
on your screen instance), you may specify attributes for 16-color, monochrome
and high color modes. You can then switch between these modes with
:meth:`screen.set_terminal_properties`, where :attr:`screen` is a
:class:`~urwid.main_loop.MainLoop` attribute or your own screen instance.

`register_palette reference <http://excess.org/urwid/reference.html#Screen-register_palette>`_

`set_terminal_properties reference <http://excess.org/urwid/reference.html#Screen-set_terminal_properties>`_

See also: RecommendedPalette.

16 Standard Foreground Colors
=============================

'black', 'dark red', 'dark green', 'brown', 'dark blue', 'dark magenta', 'dark
cyan', 'light gray', 'dark gray', 'light red', 'light green', 'yellow', 'light
blue', 'light magenta', 'light cyan', 'white'

8 Standard Background Colors
============================

'black', 'dark red', 'dark green', 'brown', 'dark blue', 'dark magenta', 'dark
cyan', 'light gray'

Default Foreground/Background
=============================

``'default'`` may be specified as a foreground or background to use a
terminal's default color. For terminals with transparent backgrounds
``'default'`` is the only way to show the transparent background. There is no
way to tell what the default colors are, so it is best to use default
foregrounds and backgrounds together (not with other colors) to ensure good
contrast.

Bold, Underline, Standout
=========================

These settings may be tagged on to foreground colors using commas, eg: ``'light
gray,underline,bold'``

For monochrome mode combinations of these are the only values that may be used.

Many terminals will turn foreground colors into their bright versions when you
use bold, eg: ``'dark blue,bold'`` might look the same as ``'light blue'``.
Some terminals also will display bright colors in a bold font even if you don't
specify bold. To inhibit this you can try setting ``bright_is_bold=False`` with
:func:`set_terminal_properties`, but it is not always supported.

`set_terminal_properties reference <http://excess.org/urwid/reference.html#Screen-set_terminal_properties>`_

Standout is usually displayed as the foreground and background colors reversed.

"Bright" Background Colors
==========================

'dark gray', 'light red', 'light green', 'yellow', 'light blue', 'light
magenta', 'light cyan', 'white'

Terminal support for bright background colors is spotty, and they generally
should be avoided. If you are in a high-color mode you might have better luck
using the high-color versions 'h8', 'h9', 'h10', ..., 'h15'.

.. _high-colors:

256-Color Foreground/Background
===============================

In 256-color mode you have the 16 basic colors, a 6x6x6 color cube and a gray
scale with 24 entries (white and black not included).

The color cube is weighted towards the brighter colors, with RGB points at 0,
0x5f, 0x87, 0xaf, 0xd7 and 0xff. The hex characters '0', '6', '8', 'a', 'd' and
'f' are used as short-forms for these values.

High colors may be specified by their index 'h0', ..., 'h255' or with the
shortcuts for the color cube `'#000'`, `'#006'`, `'#008'`, ..., `'#fff'` or
gray scale entries 'g0', 'g3', 'g7', ... 'g100'.

See also the palette_test.py example program

.. todo: add link

88-Color Foreground/Background
==============================

In 88-color mode you have the 16 basic colors, a 4x4x4 color cube and a gray
scale with 8 entries (white and black not included).

The color cube is weighted towards the brighter colors, with RGB points at 0,
0x8b, 0xcd, and 0xff. The hex characters '0', '8', 'c' and 'f' are used as
short-forms for these values.

High colors may be specified by their index 'h0', ..., 'h87' or with the
shortcuts for the color cube `'#000'`, `'#008'`, `'#00c'`, ..., `'#fff'` or
gray scale entries 'g0', 'g19', 'g35', ... 'g100'.

See also the palette_test.py example program

.. todo: add link

RGB Palette Setting
===================

A few terminals have the ability to customize the terminal palette's RGB
values. There is no automatic way to tell if this is supported by a user's
terminal, so this feature shouldn't be relied on.

It is used (via the reset_default_terminal_palette method) in the
palette_test.py example program when switching modes.

`modify_terminal_palette reference <http://excess.org/urwid/reference.html#Screen-modify_terminal_palette>`_

`reset_default_terminal_palette reference <http://excess.org/urwid/reference.html#Screen-reset_default_terminal_palette>`_