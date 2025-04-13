![Metallics by Draneria: Poster. Showcases 10 brushes of faux and real metallic effects](Poster%20Minimalist.png "Metallics Brush Set Poster")

### This is a set of brushes that emulate metallic effects, for [Krita.](https://github.com/KDE/krita)



#### Hello there, this is my first time making brushes! If anyone tries them out, I'd absolutely love to see your art. These can definitely be improved, but I hope you enjoy! (｡•̀ᴗ-)✧

<br>

💜 Download from Ko-Fi!

✨https://ko-fi.com/s/c567fcfd29

<br>
<br>

💜 Download from Github! 

✨https://github.com/Draneria/Metallics-by-Draneria_Krita-Brushes/releases/tag/v1.0

╰── Pick the ".bundle" if you are uncertain :>

<br>
<hr>
<br>

### 🎁 What’s Inside 🎁

<br>

🖌️ ✦ 32 Brushes

╰── Everything from glitter and gold leaf to hammered metal.

📚 ✦ 13 Textures

╰── Such as verdigris grunge and metal foil.

⚜️ ✦ 3 Patterns

╰── Inspired by Art Deco and Ukiyo-e.

🎨 ✦ 1 Palette

╰── Convenient true-to-metal tones.

🛠 ✦ 23 Brushtips

╰── Including unique RGBA tips for custom brush creation.

📜 ✦ 1 PDF Guide

╰── Comes with an install guide, reference sheets and creative inspiration.


<br>
<hr>
<br>

### ✔️ Completely Free ✔️Clean Icons ✔️Descriptive Titles ✔️Everything Tagged ✔️Incredibly Swag ✔️PDF Guide ✔️RGBA ✔️Unrestricted Colours ✔️Pen & Mouse Optimised


<br>
<hr>
<br>

Installation:

    1. Install Krita, if not already done.
    
    2. Go to “Settings” and press “Manage Resources Libraries…”.
    
    3. Press “Import” then select the .bundle file.
    
    4. Restart Krita, and enjoy!
    
<br>
<hr>
<br>
    
License type: CC-BY-SA

<br>

✦ Some brushes use resources made by Memileo, from "Rotating light brushtips WIP" and "Memileo Impasto Brushes". Thank you Memileo!

<br>

🖌 https://krita-artists.org/t/memileo-impasto-brushes/92952/56

<br>

Thank you for reading (ﾉ◕ヮ◕)ﾉ*:・ﾟ

<br>

![Metallics Brush Set Demo GIF](Brush%20Example%20Gif.gif "Metallics Brush Set Demo")

<br>
<hr>
<br>
 
💜 Need help? Check out this post for discussions and info:

<br>

✨ https://krita-artists.org/t/metallics-by-draneria/106425

<br>

Extra Note: for NixOS Users, or anyone having issues getting the brushes to load:

libpng may truncate iTXt Metadata, which isn't great! I think this is a problem with Krita itself, so this fix may apply if you are having problems with other brushes too. (no promises tho)

SOLUTION: Recompile libpng with this patch (Thank you Shiryel 👑): 

```diff
--- a/scripts/pnglibconf.dfa
+++ b/scripts/pnglibconf.dfa
@@ -516,8 +516,8 @@ setting USER_WIDTH_MAX default        1000000
 setting USER_HEIGHT_MAX default       1000000

 # Use 0 for unlimited
-setting USER_CHUNK_CACHE_MAX default     1000
-setting USER_CHUNK_MALLOC_MAX default 8000000
+setting USER_CHUNK_CACHE_MAX default  0
+setting USER_CHUNK_MALLOC_MAX default 0

 # If this option is enabled APIs to set the above limits at run time are added;
 # without this the hardwired (compile time) limits will be used.
```

Also, here is the overlay for NixOS users:

```diff
qt5 = p.qt5.overrideScope (qtf: qtp: {
  qtbase = qtp.qtbase.override {
    libpng = p.libpng.overrideAttrs (old: {
      patches = [ ./libpng.patch ];
    });
  };
});
```
Alternatively, for NixOS users the issue can be fixed without rebuilding, by using 'replacedependency' (with [disclaimers](https://github.com/NixOS/nixpkgs/blob/188297c5163e6d086ce780b25ca7642d30deb96f/pkgs/build-support/replace-dependencies.nix#L9)). Thank you Oido!

```diff
patched-krita = pkgs.replaceDependency {
  drv = pkgs.krita;
  oldDependency = pkgs.libpng;
  newDependency = pkgs.libpng.overrideAttrs (old: {
    patches = old.patches or [ ] ++ [ ./libpng.patch ];
  });
};
```
