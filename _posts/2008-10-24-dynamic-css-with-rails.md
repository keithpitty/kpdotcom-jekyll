---
layout: post
title: Dynamic CSS with Rails
date: 2008-10-24
permalink: blog/archives/2008-10-24-dynamic-css-with-rails
---

I’ve sometimes wondered why CSS isn’t more dynamic.

Take, for example, the styles applied to the sub-menu on the
[services](services) page of this site. To achieve the highlighting of
the current service, I combine a Rails view and CSS as follows:

### The Rails View 

```erb
<div id="<%= @current_service.name %>">
  <div id="secondaryNav">
    <ul>
      <% @services.each do |service| %>
        <li class="<%= service.name %>"><%= link_to service.heading, service_path(service) %><li>
      <% end %>
    <ul>
  <div>
<div>
```

### The CSS
```css
#agileweb #secondaryNav .agileweb a,
#java #secondaryNav .java a,
#coaching #secondaryNav .coaching a,
#mentoring #secondaryNav .mentoring a,
#overview #secondaryNav .overview a,
#advice #secondaryNav .advice a { 
  color: #99CC00;
  text-decoration: underline;
}
```

### Handling a new service

That does the trick nicely until I decide to add a new service. Wouldn’t
it be nice to have that CSS regenerated dynamically whenever I create,
update or delete a service?

Enter a new Ruby module:

```ruby
# libdynamic_css.rb  
module DynamicCss  
  def generate_services_nav_links_css  
    return if RAILS_ENV == "test"  
    FileUtils.cd File.expand_path("publicstylesheets", RAILS_ROOT)  
    File.open("servicesnav.css", "w") do |out|  
      service_names = []  
      services = Service.find :all  
      services.each { |s| service_names << s.name }  
      service_names.each_with_index do |name, i|  
        out.print "##{name} #secondaryNav .#{name} a"  
        if i + 1 < service_names.size  
          out.puts ","  
        else  
          out.puts " {"  
        end  
      end  
      out.puts " color: #99CC00;"  
      out.puts " text-decoration: underline;"  
      out.puts "}"  
    end  
  end  
end  
```

Then a small adjustment to invoke the css regeneration via a filter in
my admin services controller:  

```ruby
class Admin::ServicesController < AdminLayoutController  
  include DynamicCss

  after_filter :generate_services_nav_links_css, :only => [:create, :update, :destroy]

# remainder of controller
end  
```

Lastly, to ensure that the servicesnav.css file exists by the time one
of the public services pages is requested:

```ruby
# config/initializers/services_nav_css.rb

include DynamicCss

generate_services_nav_links_css  
```

Admittedly this is a specific case, but this example shows that it is
relatively straightforward to dynamically generate CSS within a Rails
app if required.
