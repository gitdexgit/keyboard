```markdown
# Custom Real Programmer Dvorak XKB Layout for Linux from the primegen in xkb

This repository contains the XKB symbol file for the "Real Programmer Dvorak" keyboard layout, configured for Linux systems running X11. 

the keyboard can be found int https://github.com/ThePrimeagen/keyboards

here is a picture of the keyboard withiout shift:

https://i.imgur.com/fsE7SUR.png

with shift:

https://i.imgur.com/IqESbIw.png



The primary goal is to have a single, self-contained file that can be easily deployed on a new system without modifying complex system XML rules, making it a robust and portable solution.

---

## The Layout File: `us_rpd`

The entire layout is defined in this single file. To back it up, just save this file. To restore, place it in the correct system directory as described in the installation instructions below.

```xkb
// Real Programmer Dvorak layout
// Based on the layout by Roland Kaufmann

default partial alphanumeric_keys
xkb_symbols "rpd" {

    name[Group1]= "English (US, Real Programmer Dvorak)";

    // Inherit from the base US layout to get modifier keys, etc.
    include "us(basic)";

    key <TLDE> { [      dollar,   asciitilde ] };
    key <AE01> { [        plus,            1 ] };
    key <AE02> { [  bracketleft,          2 ] };
    key <AE03> { [    braceleft,          3 ] };
    key <AE04> { [    parenleft,          4 ] };
    key <AE05> { [    ampersand,          5 ] };
    key <AE06> { [        equal,          6 ] };
    key <AE07> { [   parenright,          7 ] };
    key <AE08> { [   braceright,          8 ] };
    key <AE09> { [ bracketright,          9 ] };
    key <AE10> { [     asterisk,          0 ] };
    key <AE11> { [       exclam,    percent ] };
    key <AE12> { [          bar,      grave ] };

    key <AD01> { [    semicolon,      colon ] };
    key <AD02> { [        comma,       less ] };
    key <AD03> { [       period,    greater ] };
    key <AD04> { [            p,          P ] };
    key <AD05> { [            y,          Y ] };
    key <AD06> { [            f,          F ] };
    key <AD07> { [            g,          G ] };
    key <AD08> { [            c,          C ] };
    key <AD09> { [            r,          R ] };
    key <AD10> { [            l,          L ] };
    key <AD11> { [        slash,   question ] };
    key <AD12> { [           at, asciicircum] };

    key <AC01> { [            a,          A ] };
    key <AC02> { [            o,          O ] };
    key <AC03> { [            e,          E ] };
    key <AC04> { [            u,          U ] };
    key <AC05> { [            i,          I ] };
    key <AC06> { [            d,          D ] };
    key <AC07> { [            h,          H ] };
    key <AC08> { [            t,          T ] };
    key <AC09> { [            n,          N ] };
    key <AC10> { [            s,          S ] };
    key <AC11> { [        minus, underscore ] };

    key <LSGT> { [    backslash, numbersign ] };
    key <AB01> { [   apostrophe,   quotedbl ] };
    key <AB02> { [            q,          Q ] };
    key <AB03> { [            j,          J ] };
    key <AB04> { [            k,          K ] };
    key <AB05> { [            x,          X ] };
    key <AB06> { [            b,          B ] };
    key <AB07> { [            m,          M ] };
    key <AB08> { [            w,          W ] };
    key <AB09> { [            v,          V ] };
    key <AB10> { [            z,          Z ] };

};
```

---

## Installation

1.  **Copy the Layout File**

    Copy the `us_rpd` file from this repository to the system's XKB symbols directory.

    ```bash
    sudo cp us_rpd /usr/share/X11/xkb/symbols/
    ```

2.  **Activate the Layout**

    Apply the layout using `setxkbmap`. Your keyboard should immediately change.

    ```bash
    setxkbmap us_rpd
    ```

    To switch back to the standard US QWERTY layout, run:
    ```bash
    setxkbmap us
    ```

## Usage: Creating Aliases for Quick Switching

To make switching between layouts fast and easy, you can create aliases in your shell's configuration file.

1.  Open your shell's config file (e.g., `~/.zshrc` for Zsh or `~/.bashrc` for Bash).
    ```bash
    # For Zsh:
    nano ~/.zshrc

    # For Bash:
    nano ~/.bashrc
    ```

2.  Add the following lines to the end of the file:
    ```bash
    # My custom keyboard layout aliases
    alias dvp='setxkbmap us_rpd'
    alias qwerty='setxkbmap us'
    alias fr='setxkbmap fr'
    alias ara='setxkbmap ara'
    ```

3.  Apply the changes to your current terminal session:
    ```bash
    # For Zsh:
    source ~/.zshrc

    # For Bash:
    source ~/.bashrc
    ```
4.  Now you can switch layouts instantly from the command line:
    -   `dvp` - Activates Real Programmer Dvorak
    -   `qwerty` - Activates standard US QWERTY
    -   `fr` - Activates the French layout
    -   `ara` - Activates the Arabic layout

```

