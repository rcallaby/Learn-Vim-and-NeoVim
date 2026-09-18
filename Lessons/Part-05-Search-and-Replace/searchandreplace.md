**Mastering Search and Replace in Vim: A Comprehensive Guide**

Vim, a powerful and highly configurable text editor, provides a multitude of features that streamline editing workflows. One of its most essential capabilities is search and replace, which lets you locate specific patterns in text and replace them with the desired content.

### Basic Search and Replace

**Searching for a Pattern**

In Normal mode (press `Esc` if you are not already there), type `/` followed by the pattern and press `Enter` to search forward. Use `?` to search backward.  

Example — search for the word “example”:

```bash
/example
```

Press `n` to jump to the next match and `N` to jump to the previous match.

**Replacing a Pattern**

Use the `:s` (substitute) command. The general syntax is:

```bash
:[range]s/{pattern}/{replacement}/[flags]
```

- `%` as the range applies the command to the entire file.  
- Without a range the command acts only on the current line.  
- The `g` flag replaces every occurrence on each line (not merely the first).

Example — replace every occurrence of “old” with “new” throughout the file:

```bash
:%s/old/new/g
```

### Case-Insensitive Search and Replace

Add the `i` flag to ignore case:

```bash
:%s/old/new/gi
```

### Confirming Replacements

Add the `c` flag to confirm each replacement interactively:

```bash
:%s/old/new/gc
```

At each match you will be prompted (`y` = yes, `n` = no, `a` = all remaining, `q` = quit, etc.).

### Replacing Only Whole Words

Use Vim’s word-boundary atoms `\<` (start of a word) and `\>` (end of a word). (Vim does not use `\b` for word boundaries.)

Example — replace “old” with “new” only when it is a whole word:

```bash
:%s/\<old\>/new/g
```

### Using Regular Expressions

Vim supports a rich set of regular-expression atoms (see `:help pattern`).

Example — replace every digit with “X”:

```bash
:%s/\d/X/g
```

### Using Ranges

Limit the operation to a specific range of lines.

Example — replace “old” with “new” only on lines 5 through 10:

```bash
:5,10s/old/new/g
```

Other useful ranges include `.` (current line), `$` (last line), and `.,$` (current line to the end of the file).

### Saving Changes

Vim does not write changes to disk automatically. After performing substitutions, save the file with:

```bash
:w
```

(or `:wq` to write and quit).

### Using the Global Command for Conditional Replacements

The `:g` (global) command executes an Ex command on every line that matches a given pattern.

Example — on lines that begin with “start”, replace “old” with “new”:

```bash
:g/^start/s/old/new/g
```

### Preserving Case in Replacements

Vim has no single built-in flag that automatically preserves the exact case pattern of the matched text (for example, mapping “dog”/“Dog”/“DOG” to the corresponding forms of “cat”).  

Simple case transformations are available in the replacement string:

- `\u` — make the next character uppercase  
- `\U` — make characters uppercase until `\E`  
- `\l` / `\L` — corresponding lowercase forms  

For true case-preserving substitution you normally use a sub-replace expression (`\=`) or a plugin such as abolish.vim (`:Subvert` / `:S`). A basic expression that handles a simple first-letter difference is:

```bash
:%s/dog/\=submatch(0)[0] ==# 'D' ? 'Cat' : 'cat'/g
```

This approach is limited; it does not fully handle all-uppercase or mixed-case forms. For everyday work, multiple targeted substitutes or a dedicated plugin are usually preferable.

### Conclusion

Mastering search and replace in Vim is a crucial skill for efficient text editing. By understanding ranges, flags (`g`, `c`, `i`), word boundaries (`\<` `\>`), regular expressions, and the global command, you can markedly increase your productivity. Practice the examples on sample text and consult Vim’s built-in help (`:help :s`, `:help pattern`, `:help :g`) for complete details. Happy editing!