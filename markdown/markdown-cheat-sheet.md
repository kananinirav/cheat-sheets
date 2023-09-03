# Markdown cheat sheet

- [Markdown cheat sheet](#markdown-cheat-sheet)
  - [Heading](#heading)
  - [Paragraph](#paragraph)
  - [Emphasized text](#emphasized-text)
  - [Underlining Text](#underlining-text)
  - [Strike through text](#strike-through-text)
  - [Superscript](#superscript)
  - [Strong text](#strong-text)
  - [Strong emphasized text](#strong-emphasized-text)
  - [Text colors and fonts](#text-colors-and-fonts)
  - [Links](#links)
  - [Goto Any heading](#goto-any-heading)
  - [Table](#table)
    - [Adding a pipe `|` in a cell](#adding-a-pipe--in-a-cell)
    - [Left, right and center aligned table](#left-right-and-center-aligned-table)
  - [Quoting code](#quoting-code)
  - [code Block](#code-block)
  - [Bullet list](#bullet-list)
    - [Ordered List](#ordered-list)
  - [Task List](#task-list)
    - [Subtask](#subtask)
  - [Blockquote](#blockquote)
  - [Horizontal line](#horizontal-line)
  - [Image with alt](#image-with-alt)
  - [Foldable text](#foldable-text)
  - [Link to a specific part of the page](#link-to-a-specific-part-of-the-page)
  - [Hotkey](#hotkey)
    - [Hotkey list](#hotkey-list)
  - [Emoji](#emoji)
  - [Footnotes](#footnotes)
  - [Alerts](#alerts)
  - [Hiding content with comments](#hiding-content-with-comments)

- - - -

## Heading

    # Heading 1
    ## Heading 2
    ### Heading 3

## Paragraph

    Paragraph

## Emphasized text

    _Emphasized text_ or *Emphasized text*

**Example:** _Emphasized text_

## Underlining Text

    <u> My Underlined Text</u>

**Example:** <u> My Underlined Text</u>

## Strike through text

    ~~Strikethrough text~~

**Example:** ~~Strikethrough text~~

## Superscript

    This is a <sup>superscript</sup> text

**Example:** This is a <sup>superscript</sup> text

## Strong text

    __Strong text__ or **Strong text**

**Example:** __Strong text__

## Strong emphasized text

    ___Strong emphasized text___ or ***Strong emphasized text***

**Example:**　___Strong emphasized text___

## Text colors and fonts

    In his beard lived three <span style="color:red">cardinals</span>.
    I am in <span style="font-family:Papyrus; font-size:4em;">LOVE!</span>

**Example:**

- In his beard lived three <span style="color:red">cardinals</span>.
- I am in <span style="font-family:Papyrus; font-size:4em;">LOVE!</span>

## Links

    [Sample Link](http://www.example.com/) and <http://example.com/>

**Example:** [Sample Link](http://www.example.com/) and <http://example.com/>

## Goto Any heading

    [heading-1](#heading-1 "Goto heading-1")

**Example:** [Goto Heading](#heading)

## Table

```markdown
| First Header | Second Header |
| ------------ | ------------- |
| Content Cell | Content Cell  |
| Content Cell | Content Cell  |
```

**Example:**

| First Header | Second Header |
| ------------ | ------------- |
| Content Cell | Content Cell  |
| Content Cell | Content Cell  |

### Adding a pipe `|` in a cell

```
| First Header | Second Header |
| ------------ | ------------- |
| Content Cell | Content Cell  |
| Content Cell | \             |
```

**Example:**

| First Header | Second Header |
| ------------ | ------------- |
| Content Cell | Content Cell  |
| Content Cell | \             |

### Left, right and center aligned table

```
| Left aligned Header | Right aligned Header | Center aligned Header |
| :------------------ | -------------------: | :-------------------: |
| Content Cell        |         Content Cell |     Content Cell      |
| Content Cell        |         Content Cell |     Content Cell      |
```

**Example:**

| Left aligned Header | Right aligned Header | Center aligned Header |
| :------------------ | -------------------: | :-------------------: |
| Content Cell        |         Content Cell |     Content Cell      |
| Content Cell        |         Content Cell |     Content Cell      |

## Quoting code

    Use `git status` to list all new or modified files that haven't yet been committed.

**Example:** Use `git status` to list all new or modified files that haven't yet been committed.

## code Block

    ```ruby
    ```

Example

```ruby
def sum(a,b)
  a + b
end
```

## Bullet list

```
* Bullet list
  * Nested bullet
    * Sub-nested bullet etc
* Bullet list item 2

-OR-

- Bullet list
  - Nested bullet
    - Sub-nested bullet etc
- Bullet list item 2
```

**Example:**

- Bullet list
  - Nested bullet
    - Sub-nested bullet etc
- Bullet list item 2

### Ordered List

```
1. A numbered list
  1. A nested numbered list
  2. Which is numbered
2. Which is numbered
```

**Example:**

1. A numbered list
   1. A nested numbered list
   2. Which is numbered
2. Which is numbered

## Task List

```
- [ ] An uncompleted task
- [x] A completed task
```

**Example:**

- [ ] An uncompleted task
- [x] A completed task

### Subtask

```
- [ ] Project 1
  - [ ] Subtask 1
```

**Example:**

- [ ] Project 1
  - [ ] Subtask 1

## Blockquote

    > Blockquote
    >> Nested Blockquote

**Example:**

> Blockquote
>> Nested blockquote

## Horizontal line

    - - - -

**Example:**

- - - -

## Image with alt

    ![picture alt](http://example.com/200x150)

**Example:** ![picture alt](http://example.com/200x150)

## Foldable text

    <details>
      <summary>Title 1</summary>
      <p>Title 1 Title 1 Title 1</p>
    </details>

**Example:**

<details>
  <summary>Title 1</summary>
  <p>Title 1 Title 1 Title 1</p>
</details>
<details>
  <summary>Title 2</summary>
  <p>Title 2 Title 2 Title 2</p>
</details>

## Link to a specific part of the page

    [text goes here](#section_name)

**Example:** [Go To TOP](#TOP)

## Hotkey

    <kbd>⌘F</kbd>

**Example:**

<kbd>⌘F</kbd> <kbd>⇧⌘F</kbd>

### Hotkey list

| Key       | Symbol |
| --------- | ------ |
| Option    | ⌥      |
| Control   | ⌃      |
| Command   | ⌘      |
| Shift     | ⇧      |
| Caps Lock | ⇪      |
| Tab       | ⇥      |
| Esc       | ⎋      |
| Power     | ⌽      |
| Return    | ↩      |
| Delete    | ⌫      |
| Up        | ↑      |
| Down      | ↓      |
| Left      | ←      |
| Right     | →      |

## Emoji

:exclamation: Use emoji icons to enhance text. :+1:  Look up emoji codes at [emoji-cheat-sheet.com](http://emoji-cheat-sheet.com/)

    Code appears between colons :EMOJICODE:

## Footnotes

    Here is a simple footnote[^1].

    A footnote can also have multiple lines[^2].

    [^1]: My reference.
    [^2]: To add line breaks within a footnote, prefix new lines with 2 spaces.
      This is a second line.

**Example:**

Here is a simple footnote[^1].

A footnote can also have multiple lines[^2].

[^1]: My reference.
[^2]: To add line breaks within a footnote, prefix new lines with 2 spaces.
  This is a second line.

## Alerts

    > [!NOTE]
    > Highlights information that users should take into account, even when skimming.

    > [!IMPORTANT]
    > Crucial information necessary for users to succeed.

    > [!WARNING]
    > Critical content demanding immediate user attention due to potential risks.

**Example:**

> [!NOTE]
> Highlights information that users should take into account, even when skimming.

> [!IMPORTANT]
> Crucial information necessary for users to succeed.

> [!WARNING]
> Critical content demanding immediate user attention due to potential risks.

## Hiding content with comments

    <!-- This content will not appear in the rendered Markdown -->
