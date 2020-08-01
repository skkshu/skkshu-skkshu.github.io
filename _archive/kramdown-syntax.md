# KRAMDOWN SYNTAX

## Structural Elements

- Headers
```
# Header 1
### Header 3
###### Header 6
```
- Blockquotes
> use empty line started with `>` to separate paragraphs
>
> you can use `Headers`, `Lists` and nest `Blockquotes`
>
> Line wrapping allows one to be lazy but hinders readability and should
> therefore be avoided, especially with Blockquotes

- lists

- tables

# Text Markup
## Links
- Automatic links
	:  `<https://skkshu.github.io>`
- Inline links
	:  `[alt text](skkshu.github.io "title")`
- Reference links
	:  `The project 1 is [here][github]`
	:  `The project 2 is [also here][github]`
	:  `[github]:<optional one or more spaces>github.com/skkshu`

- Links definitions
	:  `[linkid]: http://skkshu.github.io "Optional Title"`
## Images
`![alt text](/img/shiba.png 'Title text')`
![alt text](/img/shiba.jpg 'a cute shiba')
{: .center-block}
## Emphasis
## Footnotes --From php
uh oh[^1]!  
here[^footnote].

## Abbreviations
This is some text written in HTML but in another language.

*[another language]: It's called Markdown

*[markdown]: HyperTextMarkupLanguage
{:.mega-big}
## Horizontal Rulus
*three or more asterisks, dashes or underscores, optionally separated by spaces or tabs, on an otherwise blank line*
`***`  
`---`  
`- - - - -`  
`-------------`
## Definition lists
*If you insert a blank line before a definition (note: there must only be one blank line between the terms and the first definition), the definition will be wrapped in a paragraph:*
term
: definition
: another definition
## <++>
## Additonal attributes
*code block with line numbers*

{% highlight javascript linenos %}
var foo = function(x) {
  return(x + 5);
}
foo(3)
{% endhighlight %}

---

```bash
sudo pacman -Syyu
pacman -Qdtq
```

The project 1 is [here][github]
The project 2 is [also here][github]

[github]\: github.com/skkshu 'Optional Title'[^note]

[github]:github.com/skkshu 'Optional Title'
[linkid]:http://skkshu.github.io
	"Optional Title"

[^1]:    some what (spaces are stripped away)
[^note]: 
		some other footnote

		some

		or , naturally, simple

[^footnote]:
	some other footnote
