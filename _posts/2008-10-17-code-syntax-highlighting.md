---
layout: post
title: Code Syntax Highlighting
date: 2008-10-17
permalink: /blog/archives/2008-10-17-code-syntax-highlighting
---

Having just implemented code syntax highlighting in this blog in
addition to Textile formatting, I thought I’d share how I did it.

After a little research, I decided that Arya Asemanfar’s
[tm_syntax_highlighting
plugin](http://github.com/arya/tm_syntax_highlighting/tree/master)
looked the most promising. Arya’s [blog
post](http://unboundimagination.com/Rails-Plugin:-TextMate-Syntax-Highlighting)
about it was particularly helpful.

### Prerequisites

Install the oniguruma system library (see link in the plugin README).

Install the [ultraviolet](http://ultraviolet.rubyforge.org/) gem, which
will also install the textpow and oniguruma gems.

`sudo gem install ultraviolet`

### 1. Install the Plugin

`./script/plugin install git://github.com/arya/tm_syntax_highlighting`

### 2. Copy all themes from ultraviolet:

`./script/generate syntax_css`

### 3. Create defaults initializer

```ruby
# config/initializers/tm_syntax.rb  
TmSyntaxHighlighting.defaults = {:theme => "mac_classic", :line_numbers => false, :lang => "ruby"}  
```

### 4. Create an application helper method to parse the Textile and code:

Note: I have used “c0de” instead of “code” here just to enable this code
to be parsed!

```ruby
# app/helpers/application_helper.rb  
def parse_textile_and_code_syntax(text)  
  text_pieces = text.split((<c0de>|<c0de lang="[A-Za-z0-9_-]+">|<c0de lang='[A-Za-z0-9_-]+'>|<\/c0de>)/)  
  in_pre = false  
  language = nil  
  text_pieces.collect do |piece|  
    if piece =~ /^<c0de( lang=(["’\])?(.*)\2)?>$/  
      language = $3  
      in_pre = true  
      nil  
    elsif piece == "</c0de>"  
      in_pre = false  
      language = nil  
      nil  
    elsif in_pre  
      code(piece.strip, :lang => language, :theme => "mac_classic")  
    else  
      RedCloth.new(piece.strip).to_html  
    end  
  end  
end  
```  

### 5. Use the helper in the views

```erb
parse_textile_and_code_syntax(@blog_post.post) %>
```

### 6. Add CSS for horizontal scrolling

```css
pre {  
  margin: 10px 10px;  
  padding: 10px 10px;  
  line-height: 15px;  
  overflow: auto;  
  font-family: "Monaco", "Courier New", courier;  
  font-size: 12px;  
}  
```
