---
layout: post
title:  "Read Large XML Files"
date:   2014-03-19 14:38:00
<!-- categries: -->
tags: [XML, C#, large files]
share: true
<!-- comments: true -->
---

This is a note to myself if ever in the future I need to read a large xml file. I know I know, reading xml is so 90's but it does happen.

Standard approach is it Google the answer. As it is not one of those things you use on a regular basis. Which is what I was about to do like any other developer. Then thought to myself that the .NET framework has been around for at least 10 years. They must have provided a way to accomplish this.

So here is an extension method to read large xml files.

{% highlight c# %}
public static class Extension
{
    public static IEnumerable<XElement> ReadElements(this XmlReader reader, XName elementName)
    {
        if (reader.Name.Equals(elementName.LocalName, StringComparison.OrdinalIgnoreCase) 
            && reader.NamespaceURI.Equals(elementName.NamespaceName, StringComparison.OrdinalIgnoreCase))
        {
            yield return (XElement)XNode.ReadFrom(reader);
        }

        while (reader.ReadToNextSibling(elementName.LocalName, elementName.NamespaceName))
        {
            yield return (XElement)XNode.ReadFrom(reader);
        }
    }
}
{% endhighlight %}

Here is example of how to use the extension method:

{% highlight c# %}
using (XmlReader reader = XmlReader.Create(path))
{
    foreach (XElement etext in reader.ReadElements("product"))
    {
    	// extract data from xml element...
    }
}
{% endhighlight %}

The path is the location of the xml file. In this example the xml contains collection of products. Hence passing the elemnt name "product".

The trick here is the XNode which makes a copy of the elements at the current position of xml reader. This allows the reader to move onto next element in the file.

That is all.