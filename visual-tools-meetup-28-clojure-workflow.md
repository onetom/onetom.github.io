# About myself

* 1977 - 0yo
* 1984 - ZX81, 1 KByte RAM, BASIC, ~7yo
* 1986 - ZX Spectrum 48 Kbyte RAM+ROM, Z80 Assembly, 4th Forth, ~9yo

* 1990 - Some PC AT (Intel 80286) 1 MByte RAM
    * Plotting on a Roland DXY-880 with light pen, 4th Forth, DOS

* 1991 - Turbo Pascal 5.5, DOS
    * Font editor of the character generator ROM of Hercules cards,
      so we can show Hungarian characters
       
* 1993 - 386DX40 4MB RAM

    * EPROM burner, 8086 16bit Assembly, DOS
    * PCB CAD file preprocessor to pull out tracks from pin holes,
      Turbo Pascal 5.5, DOS

* 1994 - Microchip PIC16C84 MCU

    8-bit data, 12/14-bit code, 8-level stack
    Assembly, Mary Forth & Flash Forth
         
    * Dog heart stimulator for pharmachological experiments

* 1995 - Turbo Pascal 6.0, mawk (from sunet.se gopher), DOS, ~18yo
    * Hardware debugger in Turbo Vision

* 1996 - Delphi 2.0 under Windows 3.1
    * 2-channel spectro-meter (to measure photosynthesis)

* 1997 - Debian 1.3 Bo, Rex, Slink
    * Chimney cover geometry designer, GNU Forth, geomview
    * Sperm counter, PIC16Cxx Forth
    * "MIDI flute" from keyboard, PIC Forth
    * PIC assembler in gawk
    * PIC pinout visualizer in TCL/Tk

* REBOL
    * iOS app launcher simulation in a few kilobytes
    * Centralized infrastructure configuration server, usable from `bash`

* Ruby (on Rails)
    * Online shop for sed Japanese cars (motorworld.jp)
  
* node.js / Android / Java
    * Digital photo frame

* Clojure / Datomic On-Prem & Cloud
    * Mobile app management for Schneider Electric / Hong Kong government
    * Financial transaction description recognition (from PoS/CC)
    * Xero & QuickBooks -> Google Sheets & Excel "bridge"

# Tooling evolution

* DOS Norton Commander F4, ChiWriter, QBasic, QEdit (`q.exe`)
* Turbo Pascal 5/6 IDE in Turbo Vision with WordStar-like bindings
* 7 years of Linux system administration with `vim` & `screen`
* Ruby in `TextMate` on PPC iBook
* More Ruby & Node.js in `Sublime Text 2` under both Linux & Mac
* Dip toes into JetBrains' `RubyMine`, but went back to `SublimeText`

* Tried every editor under the sun for editing with proportional fonts
  and editing Clojure, without a REPL, using `boot` & its reloading
  capabilities.
    
    * `Sublime Text 3` + `SublimeREPL`
    * `Emacs` + `CIDER` / `inf-clojure`
    * `NetBeans`
    * `Eclipse`
    * `Atom` (now `Pulsar`) + `Chlorine`
    * `jEdit`
    * `LightTable`
    * `VS Code` + `Calva`
    * `vim` + `Fireplace` / `vim-iced`
  
    and all the niche ones, like:
  
    * `Liquid` https://github.com/mogenslund/liquid (https://salza.dk/)
    * `Nightcode` https://github.com/oakes/Nightcode
    * `Nightlight` https://sekao.net/nightlight/
    * `Paravim` https://sekao.net/paravim/
  
* While looking for a `rowanj GitX` alternative, I remembered from
  `RubyMine`, how good its VCS support was, so I spent a week learning
  `IntelliJ CE (Community Edition)` and another week `Cursive` and
  structural editing, then taught my 5 people team in another ~2 weeks,
  by pair-programming with them in rotation.

* In 2020, because of Clojure, started looking into `Emacs` again, but
  more seriously. I had about 2-3 previous failed attempts to learn it
  in the previous decades. No one, who was a proponent of it could use
  it as well, as I could use other editors...

# Cursive

## Pros

* Static analysis, instead of talking to a running program
    * broken program can be navigated intelligently too
* Cross the Clojure / Java / .class-file boundary seamlessly
* Great, *limited* selection of structural editing actions
* Limited evaluation options
* REPL window is a tool window, like an Emacs side-window, which is
  easy to toggle, providing more space for code editing
* REPL shows both the evaluated form & its result
* Evaluations implicitly use the current file's namespace,
  eliminating the need to explicitly switch namespaces
* Evaluation history remembers the form's namespace,
  so it's easy to repeat it
* It's REPL implementation is accidentally very pair-programming friendly

Mostly because of the limitations, I think it's a lot easier to
teach Clojure, but it's also faster to make new-comers effective.

## Cons

* Static analysis, instead of talking to the running program
    * requires extra resources and time to index the whole source tree
    * have to teach it about macros
* Handling of big outputs
* JetBrains platform's heaviness and slow boot up time
* Need expensive machine to run smoothly
* Limited editing and evaluation capabilities (after a decade of use)
* Limited extensibility/customization
* ClojureScript story
* Advanced syntax highlighting (protocols, macros, interop)

# Cursive vs. Emacs

For that reason, I think bbatsov's `inf-clojure` has a great potential
to be a beginner tool, if we could bridge the differences between the
Emacs philosophy and the CUA / IDE land, by either

1. come up with an Emacs syllabus, which is quick and easy to learn.
   
2. port back some of the features into Emacs, if they are
   philosophically compatible

I don't have extensive experience with the following tools, but I saw
them break 1st hand, when I was trying them 1-3 years ago.

If the use of `clojure-lsp` would be as reliable as `Cursive`'s, then
`inf-clojure` would make even more sense.

Nowadays `clojure-lsp` has actually already surpassed `Cursive` in its
refactoring capabilities, but Emacs' built-in `eglot` LSP client seems to be
a bit flaky still and `lsp-mode` is a bit heavy, custom rolled, opinionated
and doesn't _extensively_ leverage Emacs' built-in facilities.

Treesitter integration is not really there yet stability-wise, though it
would be a great way for static-analysis based

1. syntax highlighting
2. structural navigation
3. structural editing, including complex refactorings

# Demo

## Navigation

* `Extend / Shrink selection` actions with `Opt-Up/Down` + `Left/Right`
    In vanilla Emacs 
    * `backward-up-list` (`C-M-<up>/u`)
    * `mark-sexp` (`C-M-SPC`)
    * `exchange-point-and-mark` (`C-x C-x`)
        or `expand-region.el` `C-=` repeatedly

* Navigate by namespaces, not files
    * so you don't have to translate between dashes and underscores

* Navigate with `Recent Files` (`Cmd-E`) action
    * not just to files, but tool windows
    * implicit fuzzy search/narrowing in every popup
    * on 2nd press, it constrains to modified files only

## Editing

* slurp/barf only forwards is largely enough `Cmd-Shift-J/K`

* refactoring (`Ctrl-T`, like refac*T*or)
    * rename symbol
    * rename keyword
    * rename namespace
        * `Cmd-Shift-C` copies full-path, but we need the fully-qualified namespace
            symbol
        * `clojure-lsp rename --from some.name.space --to other.name.space`
          
            https://clojure-lsp.io/
          
            ```shell
            brew remove clojure-lsp
            brew install clojure-lsp/brew/clojure-lsp-native
            ```
  
    * extract variables
    * inline variables
    * extract function
        not built-in, but we can
        1. extract into a `let` block
        2. change it to `letfn` and verify it works
        3. cut&paste the definition in `letfn` to top-level
        4. splice in the `letfn` and just `delete line` it, to clean up

## Evaluation

The following constraints are very useful for beginners IMHO and
take away a lot of mental burden.

* Built-in `Send Top Form to REPL` binding `Cmd-Shift-P` is a bit quirky,
    though it blends in well with other default bindings.
    
    In vanilla Emacs it's `eval-defun` (`C-M-x` like e*X*ecute)
    
    In CIDER it's `cider-eval-defun-at-point` (`C-M-x` too)
    or `cider-pprint-eval-defun-at-point` (`C-c C-f`, like de*F*un?)
    or a handful of other options and bindings.
    
    It's too many options for a beginner and still a lot of mental overhead
    even for a seasoned user, though I'm beginning to feel the need for these
    after about a decade of development :)
  
* Use `Send Form Before Caret` sparsely
    * on remote, PROD envs, it's safer to use, especially if we are on the
      wrong branch, but we lose line number info in exception traces.

* `Re-execute last command`
    * It's a custom Cursive `REPL command`
    * I bound it to `Cmd-Ctrl-Enter` & `^C C`
    * remembers original evaluation namespace
    * automatically saves the current (or all modified files)
    * no need to switch editor focus

* Don't eval individual forms!
    * If you write reloadable code, it's safe to reload any namespace
    * Except `defprotocol`s, because that would invalidate existing usages :(
