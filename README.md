Checks that an XML document is included in another document. It is
handy when testing an application output against a document where
element order is different (GData and Atom specs are examples of
specifications where element order is unimportant). It has a relaxed
notion of containment:

* element order is ignored.
* whitespace is trimmed.
* comments are ignored.
* specific elements can be ignored by passing XPath-like paths on the command line.
* text nodes (element and attribute content) can be ignored by passing '-notext' on the command line. Only document structure is checked.

## Example

You need a working Scala installation to run this program. Then you can run it like this:

```
scala -cp xmldiff.jar com.google.xmldiff.Main feed.xml feed-out.xml -i feed/totalResults feed/startIndex \
    feed/itemsPerPage feed/entry/published //updated /feed/entry/content
```

The above command will compare `feed.xml` and `feed-out.xml`, ignoring
all updated elements, openSearch elements under feed, and content or
published elements inside feed entries.
