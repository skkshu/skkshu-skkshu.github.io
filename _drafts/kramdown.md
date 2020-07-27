> some
> 
> some
> 
> some
> > some
> 
> 
> > > > some
> 
> 
> some hello thing

> A sample blockquote.
>
> >Nested blockquotes are
> >also possible.
>
> ## Headers work too
> This is the outer quote again.


> This is a blockquote
continued on this
and this line.
---
But this is a separate paragraph.
** ** **
-----------------------------------
- - - -- -- - --- - -- 
- some
- ---------  - - - - -- 

stigma
: some the most

term
: definition
: another definition  
some the most

another term
and another term
: and a definition for the term


| word      | definition                                                                       |
|-----------|----------------------------------------------------------------------------------|
| `emblem`  | a design representing a country or org                                           |
| `stigma`  | a mark of disgrace associated with a particular circumstance, quality, or person |
| `prevail` | to exist or be very common at a particular time or in a particular place         |
| `<++>`    | <++>                                                                             |



| Header1 | Header2 | Header3 |
|:--------|:-------:|--------:|
| cell1   | cell2   | cell3   |
| cell4   | cell5   | cell6   |
|----
| cell1   | cell2   | cell3   |
| cell4   | cell5   | cell6   |
|=====
| Foot1   | Foot2   | Foot3
{: rules="groups"}



> A nice blockquote[^2]
{: title="Blockquote title"}

Use `Kramdown::Document.new(text).to_html`
to convert the `text` in kramdown
syntax to HTML.

Use backticks to markup code,
e.g. `` `code` ``.  
`` `code` ``

This is a text with a
footnote[^1].

[^1]: And here is the definition.
[^2]:
		blockquote is a block which quotes sth.
some
here
is
the
place.

This is an <span style="color: purple">HTML</span>.
example.

*[HTML]: Hyper Text Markup Language  

a game which name is CS:GO

*[CS:GO]: cross fire and go


*   This is just text.
    * this is a sub list item
      * this is a sub sub list item
* This is just text,
    spanning two lines
  * this is a nested list item.
