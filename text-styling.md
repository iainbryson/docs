### Paragraphs
Paragraphs in Markdown are just one or more lines of consecutive text followed by one or more blank lines.

On July 2, an alien mothership entered Earth's orbit and deployed several dozen saucer-shaped "destroyer" spacecraft, each 15 miles (24 km) wide.

On July 3, the Black Knights, a squadron of Marine Corps F/A-18 Hornets, participated in an assault on a destroyer near the city of Los Angeles.

### Newlines
The biggest difference with writing on GitHub is the way we handle linebreaks. With Markdown, you can hard wrap paragraphs of text to have them combine into a single paragraph. We find this causes a huge number of unintentional formatting errors. In comments, GitHub treats newlines in paragraph-like content as real line breaks, which is usually what you intended.

The next paragraph contains two phrases separated by a single newline character and two spaces at the first line:

Roses are red  
Violets are blue

### Headings
You can create a heading by adding one or more # symbols before your heading text. The number of `#` you use will determine the size of the heading.

# Largest which have underline
## Second largest which have underline
### Third largest
#### Third smallest
##### Second smallest
###### Smallest

### Blockquotes
You can indicate blockquotes with a `>`.

> In the words of Abraham Lincoln:
>
> Pardon my french

### Styling text
You can make text bold or italic.

*This text will be italic*  
**This text will be bold**

Both bold and italic can use either a `*` or an `_` around the text for styling. This allows you to combine both bold and italic if needed.

**Everyone _must_ attend the meeting at 5 o'clock today.**

### Multiple underscores in words
Where Markdown transforms underscores `_` into italics, GFM ignores underscores in words, like this:

wow_great_stuff  
do_this_and_do_that_and_another_thing.

This allows code and names with multiple underscores to render properly. To emphasize a portion of a word, use asterisks `*`.

### Strikethrough
GFM adds syntax to create strikethrough text, which is missing from standard Markdown.

~~Mistaken text.~~

### Unordered lists
You can make an unordered list by preceding list items with either a `*` or a `-`.

* Item
* Item
* Item

- Item
- Item
- Item

### Ordered lists
You can make an ordered list by preceding list items with a number.

1. Item 1
2. Item 2
3. Item 3

### Nested lists
You can create nested lists by indenting list items by two spaces.

1. Item 1
  1. A corollary to the above item.
  2. Yet another point to consider.
2. Item 2
  * A corollary that does not need to be ordered.
    * This is indented four spaces, because it's two spaces further than the item above.
    * You might want to consider making a new list.
3. Item 3

### Task lists
Lists can be turned into task lists by prefacing list items with `[ ]` or `[x]` (incomplete or complete, respectively).

- [x] @mentions, #refs, [links](), **formatting**, and <del>tags</del> are supported
- [x] list syntax is required (any unordered or ordered list supported)
- [x] this is a complete item
- [ ] this is an incomplete item

Task lists render with checkboxes in all comments and Markdown files. Select or unselect these checkboxes to mark them as complete or incomplete across GitHub.

Task lists can be nested to better structure your tasks:

- [ ] a bigger project
  - [ ] first subtask #1234
  - [ ] follow up subtask #4321
  - [ ] final subtask cc @mention
- [ ] a separate task

Task lists can be nested to arbitrary depths, though we recommend nesting at most once or twice; more complicated tasks should be broken out into separate lists.

### Inline code formats
Use single backticks <code>`</code> to format text in a special monospace format. Everything within the backticks appear as-is, with no other special formatting.

Here's an idea: why don't we take `SuperiorProject` and turn it into `**Reasonable**Project`.

### Multiple code lines
You can use triple backticks <code>```</code> to format text as its own distinct block.
```
Check out this neat program I wrote:

x = 2 + y
y = 2 + x
what is x?
```

### Multiple code lines syntax highlighting
Code blocks can be taken a step further by adding syntax highlighting. In your fenced block, add an optional language identifier and we'll run it through syntax highlighting. For example, to syntax highlight R code:

```R
# save as a PDF file
pdf("myPlot.pdf")
x <- 1:50
plot(x, log(x))
graphics.off()
```

### Links
You can create an inline link by wrapping link text in brackets `[ ]`, and then wrapping the link in parentheses `( )`.

For example, to create a hyperlink to www.github.com, with a link text that says, Visit GitHub!, you'd write this in Markdown: [Visit GitHub!](www.github.com).

GFM will autolink standard URLs, so if you want to link to a URL (instead of setting link text), you can simply enter the URL and it will be turned into a link to that URL.

http://example.com

### Tables
You can create tables by assembling a list of words and dividing them with hyphens `-` (for the first row), and then separating each column with a pipe `|`:

First Header  | Second Header
------------- | -------------
Content Cell  | Content Cell
Content Cell  | Content Cell

For aesthetic purposes, you can also add extra pipes on the ends:

| First Header  | Second Header |
| ------------- | ------------- |
| Content Cell  | Content Cell  |
| Content Cell  | Content Cell  |

Note that the dashes at the top don't need to match the length of the header text exactly:

| Name | Description          |
| ------------- | ----------- |
| Help      | Display the help window.|
| Close     | Closes a window     |

You can also include inline Markdown such as links, bold, italics, or strikethrough:

| Name | Description          |
| ------------- | ----------- |
| Help      | ~~Display the~~ help window.|
| Close     | _Closes_ a window     |

Finally, by including colons `:` within the header row, you can define text to be left-aligned, right-aligned, or center-aligned:

| Left-Aligned  | Center Aligned  | Right Aligned |
| :------------ |:---------------:| -----:|
| col 3 is      | some wordy text | $1600 |
| col 2 is      | centered        |   $12 |
| zebra stripes | are neat        |    $1 |

A colon on the left-most side indicates a left-aligned column; a colon on the right-most side indicates a right-aligned column; a colon on both sides indicates a center-aligned column.

### Images
![GitHub Logo](https://avatars0.githubusercontent.com/u/2102028)
