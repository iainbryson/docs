## Quiz format

A `.quiz` file is an UTF-8 encoded file written in a text editor. It contains blocks defined by `begin:name_of_block_here`
and `end:name_of_block_here`. The order of the blocks are important, as they determine the order content of the final quiz.
A block can be indented with any number of spaces and tabs. The same goes for the content in the block. Block content in
the following will be called commands.

Blocks and commands are case-insensitive.

An argument for a command must be quoted with either `"` or `'` unless it is a word (from a regex point of view), then it
doesn't need to be quoted.

New lines and comments are allowed inside the block. Comments starts with any number of spaces and tabs followed by `#`.

## Text block

Here is an example.

```
begin:text
Long text over several lines which will be parsed by Markdown.
end:text
```

The content of text blocks are parsed though Kramdown, which is an improved Markdown.

Another example

```
begin:text
## Now comes the hard questions
## These are not comments because they are inside a text block. ## is valid Markdown.

Don't feel bad if you get them wrong.
end:text
```

The lines starting with `#` are not comments, when it is inside a text block.

## Quotes

Here are a few exaples of how quoting works. Notice how a single `'` have an extra quote to protect it.

```
text one_word_doesnt_need_quotes
text "this one needs quotes" 
text 'and this one needs quotes'

text 'DTU''s developers like Ruby'
text "DTU''s developers like Ruby" 
text "PHP used to be ""cool""" 
text 'PHP used to be ""cool""'
text "What is 'the' largest US state?" 
```

## Comments and new lines
Comments and new lines are allowed between the blocks.

## Multiple choice question block

An example

```
begin:multiple_choice
  text "What is the largest US state?"
  right 'Alaska' "You really know your stuff"
  wrong  'Hawaii' "Not big enough."
  wrong  'Texas'  "That's pretty big, but think colder."
  randomize false
end:multiple_choice
```

`text` is required which `text` takes one argument that is parsed though Kramdown. Had the argument been e.g. `Test` then the
command could have been written as `text Test`. Had the argument been `DTU's quiz` then it should have been
written as `text 'DTU''s quiz'`.

`right` and `wrong` are the possible answers for the question. Multiple choice can only have one `right`. The first argument is the text of the answer. The second argument is a teacher feedback which will be displayed in the quiz according to the quiz' fedback level. Both arguments are parsed though Kramdown. As seen here there can be one or more spaces and tabs between commands and arguments and also between arguments. At least one `right` and one `wrong` is required.

`randomize` is optional and takes the boolians `true`, `TRUE`, `false`, or `FALSE`. By default the order of `right` and `wrong` will be randomized, but this can be overwritten per question.

Another example

```
begin:multiple_choice
  text "What distribution is on the graph?"
  # second argument to picture can be left out for don't scale image, y=#value#, x=#value#
  picture images/graph.svg y=400

  right 'Normal'
  wrong  'Binomial'
  wrong  'Poisson'
  randomize false
  hint 'Look at zero' 'Look at the tails'
end:multiple_choice
```

Comments are allowed in blocks.

`picture` is optional and takes a path as the second argument, which is required. The image must be in a directory in the Github repository where the quiz file is. E.g. `images/name_of_image.svg`. A third argument is optional and can either be `x=an_integer_here` or `y=an_integer_here`, which will scale the picture accordinging. If a third argument is not given the picture will be scaled to text width.

`hint` is optional and will make a button appear next to the question. If pressed the student will be asked to confirm that a hint is wanted, and then it will be given and logged. In this example there are two hints and each is parsed through Kramdown. One button click is needed for each of them. 


## Multiple choice "select all that apply" questions

An example

```
begin:all_that_apply
  text "Which are American political parties?"

  right "Democrats"
  right "Republicans"
  right "Greens" "Yes, they're a party!"
  wrong  "Tories" "They're British"
  wrong  "Social Democrats"
end:all_that_apply
```

This type of question uses check boxes instead of radio buttons, which allows for multiple answers needs to be ticked off in order to get the question correct.

## Right and wrong over several lines

So far `right` and `wrong` have all been in single lines, but can over several lines if written like so

```
begin:right
Here you can write whatever you want.

And over as many lines you like.
end:right

begin:wrong
This is the wrong answer.

You can write Latex equations and use Kramdown text styling if you like.
end:wrong
```


## Latex

Latex commands is allowed in `text`, text blocks, `right`, `wrong`, and `hint`. An example

```
begin:multiple_choice

  begin:text
    When $a \ne 0$, there are two solutions to \(ax^2 + bx + c = 0\) and they are
    $$x = {-b \pm \sqrt{b^2-4ac} \over 2a}.$$
 
    Did you knew this?
  end:text

  right "yes" "That was good"
  wrong "no"

end:multiple_choice
```

Leading spaces and tabs inside a text block will be removed before parsing it through Kramdown.

The supported Latex are described at

* http://www.onemathematicalcat.org/MathJaxDocumentation/TeXSyntax.htm
* http://mirrors.ctan.org/macros/latex/required/amslatex/math/amsldoc.pdf
* http://mirrors.ctan.org/info/math/voss/mathmode/Mathmode.pdf


## Draw on picture question

An example

```
begin:draw
  text 'Draw lines with your mouse where the graph have a negative derivative.'
  canvas images/plot.png x=300
end:draw
```

`text` is required.

`canvas` is similar to `picture`, but also allows the student to draw on the picture.


## Randomize questions

An example

```
begin:random
  begin:multiple_choice
    text "Which of the following equations have you seen before?"
    right '$x = {-b \pm \sqrt{b^2-4ac} \over 2a}$'
    wrong  '$x = {-b \pm \sqrt{b^2-4ac} \over 2b}$'
    wrong  '$x = {-b \pm \sqrt{b^2-4ac} \over 2c}$'
  end:multiple_choice

  begin:multiple_choice
    text "Which of the following equations have you seen before?"
    wrong  '$x = {-b \pm \sqrt{b^2-4ac} \over  a}$'
    right '$x = {-b \pm \sqrt{b^2-4ac} \over 2a}$'
    wrong  '$x = {-b \pm \sqrt{b^2-4ac} \over 3a}$'
  end:multiple_choice
end:random
```

The outcome of this is just one question choosen randomly between the blocks inside the random block. The selection of the question block to display happens the first time the student clicks on the quiz. That means, that if the student revisit the quiz at a later time, the quiz will be exactly the same as the first time.

The question type have to be the same inside the `random` block.

## Code

Code blocks start with 3 backticks and ends also with 3 backticks. Example

    begin:multiple_choice
    text "What distribution is on the graph?"
    
    begin:right
    ```ruby
    This
    is
    rendered
    as
    code.
    ```
    end:right
    
    begin:wrong
    
    ```perl
    This
    is
    rendered
    as
    code.
    ```
    end:wrong
    end:multiple_choice

Syntax highlighting is done by writing the name of the language after the 3 backticks. In the first case it is `ruby` and second `perl`, but it should support (all?) languages.

## Fill in the blank

In the below example are there two fields that needs to be filled out. The first have a max character limit of 4 and the second on 7.

```
begin:fill_in_the_blank
  text "Which %4% is %7%?"
end:fill_in_the_blank
```

## Free text

An example

```
begin:free_text
text "Explain what an axel is."
end:free_text
```

`text` is required. A "free text box" is under the text.


## Surveys

An example

```
begin:survey
  text "What did you think about the quiz?"
end:surveys
```

`text` is required. A "free text box" is under the text.
