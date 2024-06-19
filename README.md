# JSON-LD-SiteNavigationElement-
SiteNavigationElement 

From a couple of schema.org discussions, the SiteNavigationElement can be accessed by the hasPart and isPartof properties. 

My thought here is that the as a menu-item, the SiteNavigationElement references an on-page element (html id attribute) and a related Webpage (url), so I have "typed" them accordingly in JSON-LD.
("@type": ["SiteNavigationElement", "Webpage"],)


~~~
<script type="application/ld+json">
{
    "@context":"https://schema.org",
    "@type": "website",
    "@id": "/#",
    "name": "Title of the website",
    "description" : "The official website for example.com", 
     "url": "/",
     "hasPart": [
      {
        "@type": ["SiteNavigationElement", "Webpage"],
        "@id": "/#navlink1",
        "name": "webpage-1",
        "description" : "Subpage of example.com", 
	"url": "https://example.com/webpage-1"
      },
      {
        "@type": ["SiteNavigationElement", "Webpage"],
        "name": "webpage-2",
        "@id": "/#navlink2",
        "description" : "Subpage of example.com",
	"url": "https://example.com/webpage-2"
      },
      {
        "@type": ["SiteNavigationElement", "Webpage"],
        "name": "webpage-3",
        "@id": "/#navlink3",
        "description" : "Subpage of example.com",
	"url": "https://example.com/webpage-3"
      }
	]
  }
 </script>
~~~

Note that in JSON-LD, the validator (https://validator.schema.org/), expresses the slash character as a path prefix to the current page. So an @id of "/#" would represent the root, https://example.com/#. Likewise an (JSON-LD) @id "/#navlink1" whould be expressed as https://example.com/#navlink1 and points to an on-page element with a matching (and unique) id attribute.  (The forward slash is important so that your menu will work from any page it is placed on.)


The cooresponding html menu would look something like the example below. 
~~~
<nav>
  <ul>
    <li> <a href="/">Home</a></li>
    <li id= "navlink1"> <a href="https://example.com/webpage-1">webpage-1</a></li> <!--id= "navlink1" resolves to "#navlink1" in JSON-LD @id-->
    <li id= "navlink2"> <a href="https://example.com/webpage-2">webpage-2</a></li>
    <li id= "navlink3"> <a href="https://example.com/webpage-3">webpage-3</a></li>
  </ul>
</nav>
~~~


