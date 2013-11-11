---
layout: post
title:  'Add a "context" Block to Rails Tests'
date:   2013-11-11 22:00:00
banner: "/images/banner-2.jpg"
---


I've been ranting for awhile now on how hard it is to organize your
tests in [rails][3] using its default test framework. Meaning it doesn't
provide a `context` or `describe` block like [shoulda][1] or [rspec][2]
does.

Although recently I think I found the solution. Randomly looking around
the [devise][4] library code, I found this little snippet that adds "context"
blocks to the default test framework so its easier to organize your tests.

Here's an example:

```ruby
class SampleTest < ActiveSupport::TestCase
  #
  # This method lets us add "context" blocks in our tests
  #
  def self.context(name, &block)
    instance_eval(&block)
  end

  # We can then use the context block...
  context "When saving" do
    test "should validate name" do
      # ...
    end
  end
end
```

So there you go. A quick way of adding `context` blocks to Rails.

[1]: https://github.com/thoughtbot/shoulda
[2]: https://github.com/rspec/rspec
[3]: http://rubyonrails.org
[4]: https://github.com/plataformatec/devise
