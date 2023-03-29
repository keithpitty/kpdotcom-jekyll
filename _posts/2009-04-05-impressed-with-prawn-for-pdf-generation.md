---
layout: post
title: Impressed with Prawn for PDF Generation
date: 2009-04-05
permalink: /blog/archives/2009-04-05-impressed-with-prawn-for-pdf-generation
---

I’ve been aware of [Prawn](http://github.com/sandal/prawn/tree/master),
the Ruby PDF generation library for some time. Today was the first
occasion I had an opportunity to utilise it and I was delighted with how
easy it was to use.

My Ruby application needed to generate some tabular PDF reports so I
installed the prawn gem and, with a little help from the examples on
[the Prawn home page](http://prawn.majesticseacreature.com/) and the
[core](http://prawn.majesticseacreature.com/docs/prawn-core/) and
[layout](http://prawn.majesticseacreature.com/docs/prawn-layout/)
documentation, I was off and running.

An example of using prawn via a rake task follows:

<code lang='ruby'>  
require ‘rubygems’  
require ‘prawn’  
require ‘prawn/layout’  
namespace :report do  
desc “Generate top 10 points getters report”  
task :top10 =\> :environment do  
Prawn::Document.generate(“reports/top10.pdf”) do  
font “#{Prawn::BASEDIR}/data/fonts/DejaVuSans.ttf”  
font_size 14  
text “Top 10 Points Getters”  
text ” ”  
\# fetch two-dimensional array of data for the table  
data = Player.top10_data  
table data,  
:font_size =\> 9,  
:position =\> :center,  
:headers =\> \[“\#”, “Player”, “Points”\],  
:row_colors =\> \[“ffffff”, “eeeeee”\]  
end  
end  
end  
</code>

Generating the report was then as simple as running:

<code>  
rake report:top10  
</code>

I’m looking forward to using other features of Prawn such as image
embedding and content positioning. At the time of writing prawn itself
is version 0.4.1 and prawn-layout is 0.1.0. Hopefully [James
Healy](http://yob.id.au), an Australian noted as “instrumental to the
forward development of the library”, is coming to [Railscamp
5](http://railscampau.github.com/) next month. Then I can pick his
brains about what other features are in the pipeline.
