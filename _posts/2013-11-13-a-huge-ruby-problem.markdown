---
layout: post
title:  'A Huge Ruby Problem'
date:   2013-11-13 03:00:00
banner: "/images/banner-3.png"
---


Oh my beloved ruby! How I thought you were perfect... This was the
case until I realized it had a huge problem resolving classes.

Given this class:

```ruby
class MyModule::File 
end
```

When I try to use `MyModule::File` it would always resolve to the
standard `File` class, which is not what I want and gives me a warning:

```sh
> MyModule::File
(irb):4: warning: toplevel constant File referenced by ContentItem::File
=> File
```

I was wondering what I was doing wrong, it took me awhile to figure out,
but then [this][0] stack overflow answer beautifully explained it.

It seems that naming classes under modules that have the same name in
the global space is a bad idea because of how ruby resolves classes.
So as a workaround, just to be safe, I always try to name my classes
diffrently from any of the gem/lib classes that I use. So for this use case,
I can use `MyModule::FileItem`.


[0]: http://stackoverflow.com/questions/17695557/rails-organizing-models-in-subfolders-having-warning-toplevel-constant-a-refer
