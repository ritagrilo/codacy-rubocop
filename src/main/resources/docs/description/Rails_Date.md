
This cop checks for the correct use of Date methods,
such as Date.today, Date.current etc.

Using `Date.today` is dangerous, because it doesn't know anything about
Rails time zone. You must use `Time.zone.today` instead.

The cop also reports warnings when you are using `to_time` method,
because it doesn't know about Rails time zone either.

Two styles are supported for this cop. When EnforcedStyle is 'strict'
then the Date methods `today`, `current`, `yesterday`, and `tomorrow`
are prohibited and the usage of both `to_time`
and 'to_time_in_current_zone' are reported as warning.

When EnforcedStyle is 'flexible' then only `Date.today` is prohibited
and only `to_time` is reported as warning.

# Examples

```ruby
# bad
Date.current
Date.yesterday
Date.today
date.to_time
date.to_time_in_current_zone

# good
Time.zone.today
Time.zone.today - 1.day# bad
Date.today
date.to_time

# good
Time.zone.today
Time.zone.today - 1.day
Date.current
Date.yesterday
date.to_time_in_current_zone
```

[Source](http://www.rubydoc.info/gems/rubocop/RuboCop/Cop/Rails/Date)