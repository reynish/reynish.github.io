---
layout: post
title:  "D3 data binding, the right way"
date:   2015-02-06 16:32:25
categories: javascript d3
---
```
function applyData(data){
  // Select things from the DOM
  var things = svg.selectAll(‘.thing');
  
  // Attach data
  things.data(data);
  // or if you change the order of data (or things in the DOM) you'll need
  // things.data(data, function(d){ return d.propertyToBeKey });

  // Transition existing elements
  things
    .transition()
    .duration(500)
    .attr({
      something: function(d){ return d.value }
    });

  // Deal with new
  things.enter()
    .append()
    .attr({
      class: 'thing'
    });

  // Remove old
  things.exit()
    .remove();
}
```