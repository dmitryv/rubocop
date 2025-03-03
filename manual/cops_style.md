# Style

## Style/AccessModifierDeclarations

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | No | 0.57 | -

Access modifiers should be declared to apply to a group of methods
or inline before each method, depending on configuration.

### Examples

#### EnforcedStyle: group (default)

```ruby
# bad

class Foo

  private def bar; end
  private def baz; end

end

# good

class Foo

  private

  def bar; end
  def baz; end

end
```
#### EnforcedStyle: inline

```ruby
# bad

class Foo

  private

  def bar; end
  def baz; end

end

# good

class Foo

  private def bar; end
  private def baz; end

end
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
EnforcedStyle | `group` | `inline`, `group`

## Style/Alias

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.9 | 0.36

This cop enforces the use of either `#alias` or `#alias_method`
depending on configuration.
It also flags uses of `alias :symbol` rather than `alias bareword`.

### Examples

#### EnforcedStyle: prefer_alias (default)

```ruby
# bad
alias_method :bar, :foo
alias :bar :foo

# good
alias bar foo
```
#### EnforcedStyle: prefer_alias_method

```ruby
# bad
alias :bar :foo
alias bar foo

# good
alias_method :bar, :foo
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
EnforcedStyle | `prefer_alias` | `prefer_alias`, `prefer_alias_method`

### References

* [https://rubystyle.guide#alias-method-lexically](https://rubystyle.guide#alias-method-lexically)

## Style/AndOr

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.9 | 0.25

This cop checks for uses of `and` and `or`, and suggests using `&&` and
`||` instead. It can be configured to check only in conditions or in
all contexts.

### Examples

#### EnforcedStyle: always (default)

```ruby
# bad
foo.save and return

# bad
if foo and bar
end

# good
foo.save && return

# good
if foo && bar
end
```
#### EnforcedStyle: conditionals

```ruby
# bad
if foo and bar
end

# good
foo.save && return

# good
foo.save and return

# good
if foo && bar
end
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
EnforcedStyle | `always` | `always`, `conditionals`

### References

* [https://rubystyle.guide#no-and-or-or](https://rubystyle.guide#no-and-or-or)

## Style/ArrayJoin

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.20 | 0.31

This cop checks for uses of "*" as a substitute for *join*.

Not all cases can reliably checked, due to Ruby's dynamic
types, so we consider only cases when the first argument is an
array literal or the second is a string literal.

### Examples

```ruby
# bad
%w(foo bar baz) * ","

# good
%w(foo bar baz).join(",")
```

### References

* [https://rubystyle.guide#array-join](https://rubystyle.guide#array-join)

## Style/AsciiComments

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | No | 0.9 | 0.52

This cop checks for non-ascii (non-English) characters
in comments. You could set an array of allowed non-ascii chars in
AllowedChars attribute (empty by default).

### Examples

```ruby
# bad
# Translates from English to 日本語。

# good
# Translates from English to Japanese
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
AllowedChars | `[]` | Array

### References

* [https://rubystyle.guide#english-comments](https://rubystyle.guide#english-comments)

## Style/Attr

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.9 | 0.12

This cop checks for uses of Module#attr.

### Examples

```ruby
# bad - creates a single attribute accessor (deprecated in Ruby 1.9)
attr :something, true
attr :one, :two, :three # behaves as attr_reader

# good
attr_accessor :something
attr_reader :one, :two, :three
```

### References

* [https://rubystyle.guide#attr](https://rubystyle.guide#attr)

## Style/AutoResourceCleanup

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Disabled | Yes | No | 0.30 | -

This cop checks for cases when you could use a block
accepting version of a method that does automatic
resource cleanup.

### Examples

```ruby
# bad
f = File.open('file')

# good
File.open('file') do |f|
  # ...
end
```

## Style/BarePercentLiterals

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.25 | -

This cop checks if usage of %() or %Q() matches configuration.

### Examples

#### EnforcedStyle: bare_percent (default)

```ruby
# bad
%Q(He said: "#{greeting}")
%q{She said: 'Hi'}

# good
%(He said: "#{greeting}")
%{She said: 'Hi'}
```
#### EnforcedStyle: percent_q

```ruby
# bad
%|He said: "#{greeting}"|
%/She said: 'Hi'/

# good
%Q|He said: "#{greeting}"|
%q/She said: 'Hi'/
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
EnforcedStyle | `bare_percent` | `percent_q`, `bare_percent`

### References

* [https://rubystyle.guide#percent-q-shorthand](https://rubystyle.guide#percent-q-shorthand)

## Style/BeginBlock

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | No | 0.9 | -

This cop checks for BEGIN blocks.

### Examples

```ruby
# bad
BEGIN { test }
```

### References

* [https://rubystyle.guide#no-BEGIN-blocks](https://rubystyle.guide#no-BEGIN-blocks)

## Style/BlockComments

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.9 | 0.23

This cop looks for uses of block comments (=begin...=end).

### Examples

```ruby
# bad
=begin
Multiple lines
of comments...
=end

# good
# Multiple lines
# of comments...
```

### References

* [https://rubystyle.guide#no-block-comments](https://rubystyle.guide#no-block-comments)

## Style/BlockDelimiters

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.30 | 0.35

Check for uses of braces or do/end around single line or
multi-line blocks.

### Examples

#### EnforcedStyle: line_count_based (default)

```ruby
# bad - single line block
items.each do |item| item / 5 end

# good - single line block
items.each { |item| item / 5 }

# bad - multi-line block
things.map { |thing|
  something = thing.some_method
  process(something)
}

# good - multi-line block
things.map do |thing|
  something = thing.some_method
  process(something)
end
```
#### EnforcedStyle: semantic

```ruby
# Prefer `do...end` over `{...}` for procedural blocks.

# return value is used/assigned
# bad
foo = map do |x|
  x
end
puts (map do |x|
  x
end)

# return value is not used out of scope
# good
map do |x|
  x
end

# Prefer `{...}` over `do...end` for functional blocks.

# return value is not used out of scope
# bad
each { |x|
  x
}

# return value is used/assigned
# good
foo = map { |x|
  x
}
map { |x|
  x
}.inspect

# The AllowBracesOnProceduralOneLiners option is ignored unless the
# EnforcedStyle is set to `semantic`. If so:

# If the AllowBracesOnProceduralOneLiners option is unspecified, or
# set to `false` or any other falsey value, then semantic purity is
# maintained, so one-line procedural blocks must use do-end, not
# braces.

# bad
collection.each { |element| puts element }

# good
collection.each do |element| puts element end

# If the AllowBracesOnProceduralOneLiners option is set to `true`, or
# any other truthy value, then one-line procedural blocks may use
# either style. (There is no setting for requiring braces on them.)

# good
collection.each { |element| puts element }

# also good
collection.each do |element| puts element end
```
#### EnforcedStyle: braces_for_chaining

```ruby
# bad
words.each do |word|
  word.flip.flop
end.join("-")

# good
words.each { |word|
  word.flip.flop
}.join("-")
```
#### EnforcedStyle: always_braces

```ruby
# bad
words.each do |word|
  word.flip.flop
end

# good
words.each { |word|
  word.flip.flop
}
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
EnforcedStyle | `line_count_based` | `line_count_based`, `semantic`, `braces_for_chaining`, `always_braces`
ProceduralMethods | `benchmark`, `bm`, `bmbm`, `create`, `each_with_object`, `measure`, `new`, `realtime`, `tap`, `with_object` | Array
FunctionalMethods | `let`, `let!`, `subject`, `watch` | Array
IgnoredMethods | `lambda`, `proc`, `it` | Array
AllowBracesOnProceduralOneLiners | `false` | Boolean

### References

* [https://rubystyle.guide#single-line-blocks](https://rubystyle.guide#single-line-blocks)

## Style/BracesAroundHashParameters

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.14.1 | 0.28

This cop checks for braces around the last parameter in a method call
if the last parameter is a hash.
It supports `braces`, `no_braces` and `context_dependent` styles.

### Examples

#### EnforcedStyle: braces

```ruby
# The `braces` style enforces braces around all method
# parameters that are hashes.

# bad
some_method(x, y, a: 1, b: 2)

# good
some_method(x, y, {a: 1, b: 2})
```
#### EnforcedStyle: no_braces (default)

```ruby
# The `no_braces` style checks that the last parameter doesn't
# have braces around it.

# bad
some_method(x, y, {a: 1, b: 2})

# good
some_method(x, y, a: 1, b: 2)
```
#### EnforcedStyle: context_dependent

```ruby
# The `context_dependent` style checks that the last parameter
# doesn't have braces around it, but requires braces if the
# second to last parameter is also a hash literal.

# bad
some_method(x, y, {a: 1, b: 2})
some_method(x, y, {a: 1, b: 2}, a: 1, b: 2)

# good
some_method(x, y, a: 1, b: 2)
some_method(x, y, {a: 1, b: 2}, {a: 1, b: 2})
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
EnforcedStyle | `no_braces` | `braces`, `no_braces`, `context_dependent`

## Style/CaseEquality

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | No | 0.9 | -

This cop checks for uses of the case equality operator(===).

### Examples

```ruby
# bad
Array === something
(1..100) === 7
/something/ === some_string

# good
something.is_a?(Array)
(1..100).include?(7)
some_string =~ /something/
```

### References

* [https://rubystyle.guide#no-case-equality](https://rubystyle.guide#no-case-equality)

## Style/CharacterLiteral

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.9 | -

Checks for uses of the character literal ?x.

### Examples

```ruby
# bad
?x

# good
'x'

# good
?\C-\M-d
```

### References

* [https://rubystyle.guide#no-character-literals](https://rubystyle.guide#no-character-literals)

## Style/ClassAndModuleChildren

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes (Unsafe) | 0.19 | -

This cop checks the style of children definitions at classes and
modules. Basically there are two different styles:

The compact style is only forced for classes/modules with one child.

### Examples

#### EnforcedStyle: nested (default)

```ruby
# good
# have each child on its own line
class Foo
  class Bar
  end
end
```
#### EnforcedStyle: compact

```ruby
# good
# combine definitions as much as possible
class Foo::Bar
end
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
AutoCorrect | `false` | Boolean
EnforcedStyle | `nested` | `nested`, `compact`

### References

* [https://rubystyle.guide#namespace-definition](https://rubystyle.guide#namespace-definition)

## Style/ClassCheck

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.24 | -

This cop enforces consistent use of `Object#is_a?` or `Object#kind_of?`.

### Examples

#### EnforcedStyle: is_a? (default)

```ruby
# bad
var.kind_of?(Date)
var.kind_of?(Integer)

# good
var.is_a?(Date)
var.is_a?(Integer)
```
#### EnforcedStyle: kind_of?

```ruby
# bad
var.is_a?(Time)
var.is_a?(String)

# good
var.kind_of?(Time)
var.kind_of?(String)
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
EnforcedStyle | `is_a?` | `is_a?`, `kind_of?`

## Style/ClassMethods

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.9 | 0.20

This cop checks for uses of the class/module name instead of
self, when defining class/module methods.

### Examples

```ruby
# bad
class SomeClass
  def SomeClass.class_method
    # ...
  end
end

# good
class SomeClass
  def self.class_method
    # ...
  end
end
```

### References

* [https://rubystyle.guide#def-self-class-methods](https://rubystyle.guide#def-self-class-methods)

## Style/ClassVars

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | No | 0.13 | -

This cop checks for uses of class variables. Offenses
are signaled only on assignment to class variables to
reduce the number of offenses that would be reported.

You have to be careful when setting a value for a class
variable; if a class has been inherited, changing the
value of a class variable also affects the inheriting
classes. This means that it's almost always better to
use a class instance variable instead.

### Examples

```ruby
# bad
class A
  @@test = 10
end

# good
class A
  @test = 10
end

class A
  def test
    @@test # you can access class variable without offense
  end
end
```

### References

* [https://rubystyle.guide#no-class-vars](https://rubystyle.guide#no-class-vars)

## Style/CollectionMethods

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Disabled | No | Yes  | 0.9 | 0.27

This cop enforces the use of consistent method names
from the Enumerable module.

Unfortunately we cannot actually know if a method is from
Enumerable or not (static analysis limitation), so this cop
can yield some false positives.

You can customize the mapping from undesired method to desired method.

e.g. to use `detect` over `find`:

  Style/CollectionMethods:
    PreferredMethods:
      find: detect

The default mapping for `PreferredMethods` behaves as follows.

### Examples

```ruby
# bad
items.collect
items.collect!
items.inject
items.detect
items.find_all

# good
items.map
items.map!
items.reduce
items.find
items.select
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
PreferredMethods | `{"collect"=>"map", "collect!"=>"map!", "inject"=>"reduce", "detect"=>"find", "find_all"=>"select"}` | 

### References

* [https://rubystyle.guide#map-find-select-reduce-size](https://rubystyle.guide#map-find-select-reduce-size)

## Style/ColonMethodCall

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.9 | -

This cop checks for methods invoked via the :: operator instead
of the . operator (like FileUtils::rmdir instead of FileUtils.rmdir).

### Examples

```ruby
# bad
Timeout::timeout(500) { do_something }
FileUtils::rmdir(dir)
Marshal::dump(obj)

# good
Timeout.timeout(500) { do_something }
FileUtils.rmdir(dir)
Marshal.dump(obj)
```

### References

* [https://rubystyle.guide#double-colons](https://rubystyle.guide#double-colons)

## Style/ColonMethodDefinition

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.52 | -

This cop checks for class methods that are defined using the `::`
operator instead of the `.` operator.

### Examples

```ruby
# bad
class Foo
  def self::bar
  end
end

# good
class Foo
  def self.bar
  end
end
```

### References

* [https://rubystyle.guide#colon-method-definition](https://rubystyle.guide#colon-method-definition)

## Style/CommandLiteral

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.30 | -

This cop enforces using `` or %x around command literals.

### Examples

#### EnforcedStyle: backticks (default)

```ruby
# bad
folders = %x(find . -type d).split

# bad
%x(
  ln -s foo.example.yml foo.example
  ln -s bar.example.yml bar.example
)

# good
folders = `find . -type d`.split

# good
`
  ln -s foo.example.yml foo.example
  ln -s bar.example.yml bar.example
`
```
#### EnforcedStyle: mixed

```ruby
# bad
folders = %x(find . -type d).split

# bad
`
  ln -s foo.example.yml foo.example
  ln -s bar.example.yml bar.example
`

# good
folders = `find . -type d`.split

# good
%x(
  ln -s foo.example.yml foo.example
  ln -s bar.example.yml bar.example
)
```
#### EnforcedStyle: percent_x

```ruby
# bad
folders = `find . -type d`.split

# bad
`
  ln -s foo.example.yml foo.example
  ln -s bar.example.yml bar.example
`

# good
folders = %x(find . -type d).split

# good
%x(
  ln -s foo.example.yml foo.example
  ln -s bar.example.yml bar.example
)
```
#### AllowInnerBackticks: false (default)

```ruby
# If `false`, the cop will always recommend using `%x` if one or more
# backticks are found in the command string.

# bad
`echo \`ls\``

# good
%x(echo `ls`)
```
#### AllowInnerBackticks: true

```ruby
# good
`echo \`ls\``
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
EnforcedStyle | `backticks` | `backticks`, `percent_x`, `mixed`
AllowInnerBackticks | `false` | Boolean

### References

* [https://rubystyle.guide#percent-x](https://rubystyle.guide#percent-x)

## Style/CommentAnnotation

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.10 | 0.31

This cop checks that comment annotation keywords are written according
to guidelines.

### Examples

```ruby
# bad
# TODO make better

# good
# TODO: make better

# bad
# TODO:make better

# good
# TODO: make better

# bad
# fixme: does not work

# good
# FIXME: does not work

# bad
# Optimize does not work

# good
# OPTIMIZE: does not work
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
Keywords | `TODO`, `FIXME`, `OPTIMIZE`, `HACK`, `REVIEW` | Array

### References

* [https://rubystyle.guide#annotate-keywords](https://rubystyle.guide#annotate-keywords)

## Style/CommentedKeyword

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | No | 0.51 | -

This cop checks for comments put on the same line as some keywords.
These keywords are: `begin`, `class`, `def`, `end`, `module`.

Note that some comments
(`:nodoc:`, `:yields:`, `rubocop:disable` and `rubocop:todo`)
are allowed.

### Examples

```ruby
# bad
if condition
  statement
end # end if

# bad
class X # comment
  statement
end

# bad
def x; end # comment

# good
if condition
  statement
end

# good
class X # :nodoc:
  y
end
```

## Style/ConditionalAssignment

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.36 | 0.47

Check for `if` and `case` statements where each branch is used for
assignment to the same variable when using the return of the
condition can be used instead.

### Examples

#### EnforcedStyle: assign_to_condition (default)

```ruby
# bad
if foo
  bar = 1
else
  bar = 2
end

case foo
when 'a'
  bar += 1
else
  bar += 2
end

if foo
  some_method
  bar = 1
else
  some_other_method
  bar = 2
end

# good
bar = if foo
        1
      else
        2
      end

bar += case foo
       when 'a'
         1
       else
         2
       end

bar << if foo
         some_method
         1
       else
         some_other_method
         2
       end
```
#### EnforcedStyle: assign_inside_condition

```ruby
# bad
bar = if foo
        1
      else
        2
      end

bar += case foo
       when 'a'
         1
       else
         2
       end

bar << if foo
         some_method
         1
       else
         some_other_method
         2
       end

# good
if foo
  bar = 1
else
  bar = 2
end

case foo
when 'a'
  bar += 1
else
  bar += 2
end

if foo
  some_method
  bar = 1
else
  some_other_method
  bar = 2
end
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
EnforcedStyle | `assign_to_condition` | `assign_to_condition`, `assign_inside_condition`
SingleLineConditionsOnly | `true` | Boolean
IncludeTernaryExpressions | `true` | Boolean

## Style/ConstantVisibility

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Disabled | Yes | No | 0.66 | -

This cop checks that constants defined in classes and modules have
an explicit visibility declaration. By default, Ruby makes all class-
and module constants public, which litters the public API of the
class or module. Explicitly declaring a visibility makes intent more
clear, and prevents outside actors from touching private state.

### Examples

```ruby
# bad
class Foo
  BAR = 42
  BAZ = 43
end

# good
class Foo
  BAR = 42
  private_constant :BAR

  BAZ = 43
  public_constant :BAZ
end
```

## Style/Copyright

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Disabled | Yes | Yes  | 0.30 | -

Check that a copyright notice was given in each source file.

The default regexp for an acceptable copyright notice can be found in
config/default.yml. The default can be changed as follows:

    Style/Copyright:
      Notice: '^Copyright (\(c\) )?2\d{3} Acme Inc'

This regex string is treated as an unanchored regex. For each file
that RuboCop scans, a comment that matches this regex must be found or
an offense is reported.

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
Notice | `^Copyright (\(c\) )?2[0-9]{3} .+` | String
AutocorrectNotice | `` | String

## Style/DateTime

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Disabled | Yes | No | 0.51 | 0.59

This cop checks for consistent usage of the `DateTime` class over the
`Time` class. This cop is disabled by default since these classes,
although highly overlapping, have particularities that make them not
replaceable in certain situations when dealing with multiple timezones
and/or DST.

### Examples

```ruby
# bad - uses `DateTime` for current time
DateTime.now

# good - uses `Time` for current time
Time.now

# bad - uses `DateTime` for modern date
DateTime.iso8601('2016-06-29')

# good - uses `Time` for modern date
Time.iso8601('2016-06-29')

# good - uses `DateTime` with start argument for historical date
DateTime.iso8601('1751-04-23', Date::ENGLAND)
```
#### AllowCoercion: false (default)

```ruby
# bad - coerces to `DateTime`
something.to_datetime

# good - coerces to `Time`
something.to_time
```
#### AllowCoercion: true

```ruby
# good
something.to_datetime

# good
something.to_time
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
AllowCoercion | `false` | Boolean

### References

* [https://rubystyle.guide#date--time](https://rubystyle.guide#date--time)

## Style/DefWithParentheses

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.9 | 0.12

This cop checks for parentheses in the definition of a method,
that does not take any arguments. Both instance and
class/singleton methods are checked.

### Examples

```ruby
# bad
def foo()
  # does a thing
end

# good
def foo
  # does a thing
end

# also good
def foo() does_a_thing end
```
```ruby
# bad
def Baz.foo()
  # does a thing
end

# good
def Baz.foo
  # does a thing
end
```

### References

* [https://rubystyle.guide#method-parens](https://rubystyle.guide#method-parens)

## Style/Dir

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.50 | -

This cop checks for places where the `#__dir__` method can replace more
complex constructs to retrieve a canonicalized absolute path to the
current file.

### Examples

```ruby
# bad
path = File.expand_path(File.dirname(__FILE__))

# bad
path = File.dirname(File.realpath(__FILE__))

# good
path = __dir__
```

## Style/Documentation

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | No | 0.9 | -

This cop checks for missing top-level documentation of
classes and modules. Classes with no body are exempt from the
check and so are namespace modules - modules that have nothing in
their bodies except classes, other modules, or constant definitions.

The documentation requirement is annulled if the class or module has
a "#:nodoc:" comment next to it. Likewise, "#:nodoc: all" does the
same for all its children.

### Examples

```ruby
# bad
class Person
  # ...
end

# good
# Description/Explanation of Person class
class Person
  # ...
end
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
Exclude | `spec/**/*`, `test/**/*` | Array

## Style/DocumentationMethod

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Disabled | Yes | No | 0.43 | -

This cop checks for missing documentation comment for public methods.
It can optionally be configured to also require documentation for
non-public methods.

### Examples

```ruby
# bad

class Foo
  def bar
    puts baz
  end
end

module Foo
  def bar
    puts baz
  end
end

def foo.bar
  puts baz
end

# good

class Foo
  # Documentation
  def bar
    puts baz
  end
end

module Foo
  # Documentation
  def bar
    puts baz
  end
end

# Documentation
def foo.bar
  puts baz
end
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
Exclude | `spec/**/*`, `test/**/*` | Array
RequireForNonPublicMethods | `false` | Boolean

## Style/DoubleCopDisableDirective

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.73 | -

Detects double disable comments on one line. This is mostly to catch
automatically generated comments that need to be regenerated.

### Examples

```ruby
# bad
def f # rubocop:disable Style/For # rubocop:disable Metrics/AbcSize
end

# good
# rubocop:disable Metrics/AbcSize
def f # rubocop:disable Style/For
end
# rubocop:enable Metrics/AbcSize

# if both fit on one line
def f # rubocop:disable Style/For, Metrics/AbcSize
end
```

## Style/DoubleNegation

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | No | 0.19 | -

This cop checks for uses of double negation (!!) to convert something
to a boolean value. As this is both cryptic and usually redundant, it
should be avoided.

Please, note that when something is a boolean value
!!something and !something.nil? are not the same thing.
As you're unlikely to write code that can accept values of any type
this is rarely a problem in practice.

### Examples

```ruby
# bad
!!something

# good
!something.nil?
```

### References

* [https://rubystyle.guide#no-bang-bang](https://rubystyle.guide#no-bang-bang)

## Style/EachForSimpleLoop

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.41 | -

This cop checks for loops which iterate a constant number of times,
using a Range literal and `#each`. This can be done more readably using
`Integer#times`.

This check only applies if the block takes no parameters.

### Examples

```ruby
# bad
(1..5).each { }

# good
5.times { }
```
```ruby
# bad
(0...10).each {}

# good
10.times {}
```

## Style/EachWithObject

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.22 | 0.42

This cop looks for inject / reduce calls where the passed in object is
returned at the end and so could be replaced by each_with_object without
the need to return the object at the end.

However, we can't replace with each_with_object if the accumulator
parameter is assigned to within the block.

### Examples

```ruby
# bad
[1, 2].inject({}) { |a, e| a[e] = e; a }

# good
[1, 2].each_with_object({}) { |e, a| a[e] = e }
```

## Style/EmptyBlockParameter

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.52 | -

This cop checks for pipes for empty block parameters. Pipes for empty
block parameters do not cause syntax errors, but they are redundant.

### Examples

```ruby
# bad
a do ||
  do_something
end

# bad
a { || do_something }

# good
a do
end

# good
a { do_something }
```

## Style/EmptyCaseCondition

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.40 | -

This cop checks for case statements with an empty condition.

### Examples

```ruby
# bad:
case
when x == 0
  puts 'x is 0'
when y == 0
  puts 'y is 0'
else
  puts 'neither is 0'
end

# good:
if x == 0
  puts 'x is 0'
elsif y == 0
  puts 'y is 0'
else
  puts 'neither is 0'
end

# good: (the case condition node is not empty)
case n
when 0
  puts 'zero'
when 1
  puts 'one'
else
  puts 'more'
end
```

## Style/EmptyElse

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.28 | 0.32

Checks for empty else-clauses, possibly including comments and/or an
explicit `nil` depending on the EnforcedStyle.

### Examples

#### EnforcedStyle: empty

```ruby
# warn only on empty else

# bad
if condition
  statement
else
end

# good
if condition
  statement
else
  nil
end

# good
if condition
  statement
else
  statement
end

# good
if condition
  statement
end
```
#### EnforcedStyle: nil

```ruby
# warn on else with nil in it

# bad
if condition
  statement
else
  nil
end

# good
if condition
  statement
else
end

# good
if condition
  statement
else
  statement
end

# good
if condition
  statement
end
```
#### EnforcedStyle: both (default)

```ruby
# warn on empty else and else with nil in it

# bad
if condition
  statement
else
  nil
end

# bad
if condition
  statement
else
end

# good
if condition
  statement
else
  statement
end

# good
if condition
  statement
end
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
EnforcedStyle | `both` | `empty`, `nil`, `both`

## Style/EmptyLambdaParameter

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.52 | -

This cop checks for parentheses for empty lambda parameters. Parentheses
for empty lambda parameters do not cause syntax errors, but they are
redundant.

### Examples

```ruby
# bad
-> () { do_something }

# good
-> { do_something }

# good
-> (arg) { do_something(arg) }
```

## Style/EmptyLiteral

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.9 | 0.12

This cop checks for the use of a method, the result of which
would be a literal, like an empty array, hash, or string.

### Examples

```ruby
# bad
a = Array.new
h = Hash.new
s = String.new

# good
a = []
h = {}
s = ''
```

### References

* [https://rubystyle.guide#literal-array-hash](https://rubystyle.guide#literal-array-hash)

## Style/EmptyMethod

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.46 | -

This cop checks for the formatting of empty method definitions.
By default it enforces empty method definitions to go on a single
line (compact style), but it can be configured to enforce the `end`
to go on its own line (expanded style).

Note: A method definition is not considered empty if it contains
      comments.

### Examples

#### EnforcedStyle: compact (default)

```ruby
# bad
def foo(bar)
end

def self.foo(bar)
end

# good
def foo(bar); end

def foo(bar)
  # baz
end

def self.foo(bar); end
```
#### EnforcedStyle: expanded

```ruby
# bad
def foo(bar); end

def self.foo(bar); end

# good
def foo(bar)
end

def self.foo(bar)
end
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
EnforcedStyle | `compact` | `compact`, `expanded`

### References

* [https://rubystyle.guide#no-single-line-methods](https://rubystyle.guide#no-single-line-methods)

## Style/Encoding

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.9 | 0.50

This cop checks ensures source files have no utf-8 encoding comments.

### Examples

```ruby
# bad
# encoding: UTF-8
# coding: UTF-8
# -*- coding: UTF-8 -*-
```

### References

* [https://rubystyle.guide#utf-8](https://rubystyle.guide#utf-8)

## Style/EndBlock

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | No | 0.9 | -

This cop checks for END blocks.

### Examples

```ruby
# bad
END { puts 'Goodbye!' }

# good
at_exit { puts 'Goodbye!' }
```

### References

* [https://rubystyle.guide#no-END-blocks](https://rubystyle.guide#no-END-blocks)

## Style/EvalWithLocation

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | No | 0.52 | -

This cop checks `eval` method usage. `eval` can receive source location
metadata, that are filename and line number. The metadata is used by
backtraces. This cop recommends to pass the metadata to `eval` method.

### Examples

```ruby
# bad
eval <<-RUBY
  def do_something
  end
RUBY

# bad
C.class_eval <<-RUBY
  def do_something
  end
RUBY

# good
eval <<-RUBY, binding, __FILE__, __LINE__ + 1
  def do_something
  end
RUBY

# good
C.class_eval <<-RUBY, __FILE__, __LINE__ + 1
  def do_something
  end
RUBY
```

## Style/EvenOdd

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.12 | 0.29

This cop checks for places where `Integer#even?` or `Integer#odd?`
can be used.

### Examples

```ruby
# bad
if x % 2 == 0
end

# good
if x.even?
end
```

### References

* [https://rubystyle.guide#predicate-methods](https://rubystyle.guide#predicate-methods)

## Style/ExpandPathArguments

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.53 | -

This cop checks for use of the `File.expand_path` arguments.
Likewise, it also checks for the `Pathname.new` argument.

Contrastive bad case and good case are alternately shown in
the following examples.

### Examples

```ruby
# bad
File.expand_path('..', __FILE__)

# good
File.expand_path(__dir__)

# bad
File.expand_path('../..', __FILE__)

# good
File.expand_path('..', __dir__)

# bad
File.expand_path('.', __FILE__)

# good
File.expand_path(__FILE__)

# bad
Pathname(__FILE__).parent.expand_path

# good
Pathname(__dir__).expand_path

# bad
Pathname.new(__FILE__).parent.expand_path

# good
Pathname.new(__dir__).expand_path
```

## Style/FloatDivision

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | No | 0.72 | -

This cop checks for division with integers coerced to floats.
It is recommended to either always use `fdiv` or coerce one side only.
This cop also provides other options for code consistency.

### Examples

#### EnforcedStyle: single_coerce (default)

```ruby
# bad
a.to_f / b.to_f

# good
a.to_f / b
a / b.to_f
```
#### EnforcedStyle: left_coerce

```ruby
# bad
a / b.to_f
a.to_f / b.to_f

# good
a.to_f / b
```
#### EnforcedStyle: right_coerce

```ruby
# bad
a.to_f / b
a.to_f / b.to_f

# good
a / b.to_f
```
#### EnforcedStyle: fdiv

```ruby
# bad
a / b.to_f
a.to_f / b
a.to_f / b.to_f

# good
a.fdiv(b)
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
EnforcedStyle | `single_coerce` | `left_coerce`, `right_coerce`, `single_coerce`, `fdiv`

### References

* [https://rubystyle.guide#float-division](https://rubystyle.guide#float-division)
* [https://github.com/rubocop-hq/ruby-style-guide/issues/628](https://github.com/rubocop-hq/ruby-style-guide/issues/628)

## Style/For

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.13 | 0.59

This cop looks for uses of the `for` keyword or `each` method. The
preferred alternative is set in the EnforcedStyle configuration
parameter. An `each` call with a block on a single line is always
allowed.

### Examples

#### EnforcedStyle: each (default)

```ruby
# bad
def foo
  for n in [1, 2, 3] do
    puts n
  end
end

# good
def foo
  [1, 2, 3].each do |n|
    puts n
  end
end
```
#### EnforcedStyle: for

```ruby
# bad
def foo
  [1, 2, 3].each do |n|
    puts n
  end
end

# good
def foo
  for n in [1, 2, 3] do
    puts n
  end
end
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
EnforcedStyle | `each` | `each`, `for`

### References

* [https://rubystyle.guide#no-for-loops](https://rubystyle.guide#no-for-loops)

## Style/FormatString

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.19 | 0.49

This cop enforces the use of a single string formatting utility.
Valid options include Kernel#format, Kernel#sprintf and String#%.

The detection of String#% cannot be implemented in a reliable
manner for all cases, so only two scenarios are considered -
if the first argument is a string literal and if the second
argument is an array literal.

### Examples

#### EnforcedStyle: format (default)

```ruby
# bad
puts sprintf('%10s', 'hoge')
puts '%10s' % 'hoge'

# good
puts format('%10s', 'hoge')
```
#### EnforcedStyle: sprintf

```ruby
# bad
puts format('%10s', 'hoge')
puts '%10s' % 'hoge'

# good
puts sprintf('%10s', 'hoge')
```
#### EnforcedStyle: percent

```ruby
# bad
puts format('%10s', 'hoge')
puts sprintf('%10s', 'hoge')

# good
puts '%10s' % 'hoge'
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
EnforcedStyle | `format` | `format`, `sprintf`, `percent`

### References

* [https://rubystyle.guide#sprintf](https://rubystyle.guide#sprintf)

## Style/FormatStringToken

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | No | 0.49 | 0.75

Use a consistent style for named format string tokens.

**Note:**
`unannotated` style cop only works for strings
which are passed as arguments to those methods:
`sprintf`, `format`, `%`.
The reason is that *unannotated* format is very similar
to encoded URLs or Date/Time formatting strings.

### Examples

#### EnforcedStyle: annotated (default)

```ruby
# bad
format('%{greeting}', greeting: 'Hello')
format('%s', 'Hello')

# good
format('%<greeting>s', greeting: 'Hello')
```
#### EnforcedStyle: template

```ruby
# bad
format('%<greeting>s', greeting: 'Hello')
format('%s', 'Hello')

# good
format('%{greeting}', greeting: 'Hello')
```
#### EnforcedStyle: unannotated

```ruby
# bad
format('%<greeting>s', greeting: 'Hello')
format('%{greeting}', 'Hello')

# good
format('%s', 'Hello')
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
EnforcedStyle | `annotated` | `annotated`, `template`, `unannotated`

## Style/FrozenStringLiteralComment

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.36 | 0.69

This cop is designed to help you transition from mutable string literals
to frozen string literals.
It will add the comment `# frozen_string_literal: true` to the top of
files to enable frozen string literals. Frozen string literals may be
default in future Ruby. The comment will be added below a shebang and
encoding comment. The frozen string literal comment is only valid in
Ruby 2.3+.

### Examples

#### EnforcedStyle: always (default)

```ruby
# The `always` style will always add the frozen string literal comment
# to a file, regardless of the Ruby version or if `freeze` or `<<` are
# called on a string literal.
# bad
module Bar
  # ...
end

# good
# frozen_string_literal: true

module Bar
  # ...
end
```
#### EnforcedStyle: never

```ruby
# The `never` will enforce that the frozen string literal comment does
# not exist in a file.
# bad
# frozen_string_literal: true

module Baz
  # ...
end

# good
module Baz
  # ...
end
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
EnforcedStyle | `always` | `always`, `never`

## Style/GlobalVars

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | No | 0.13 | -

This cop looks for uses of global variables.
It does not report offenses for built-in global variables.
Built-in global variables are allowed by default. Additionally
users can allow additional variables via the AllowedVariables option.

Note that backreferences like $1, $2, etc are not global variables.

### Examples

```ruby
# bad
$foo = 2
bar = $foo + 5

# good
FOO = 2
foo = 2
$stdin.read
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
AllowedVariables | `[]` | Array

### References

* [https://rubystyle.guide#instance-vars](https://rubystyle.guide#instance-vars)
* [https://www.zenspider.com/ruby/quickref.html](https://www.zenspider.com/ruby/quickref.html)

## Style/GuardClause

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | No | 0.20 | 0.22

Use a guard clause instead of wrapping the code inside a conditional
expression

### Examples

```ruby
# bad
def test
  if something
    work
  end
end

# good
def test
  return unless something
  work
end

# also good
def test
  work if something
end

# bad
if something
  raise 'exception'
else
  ok
end

# good
raise 'exception' if something
ok
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
MinBodyLength | `1` | Integer

### References

* [https://rubystyle.guide#no-nested-conditionals](https://rubystyle.guide#no-nested-conditionals)

## Style/HashSyntax

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.9 | 0.43

This cop checks hash literal syntax.

It can enforce either the use of the class hash rocket syntax or
the use of the newer Ruby 1.9 syntax (when applicable).

A separate offense is registered for each problematic pair.

The supported styles are:

* ruby19 - forces use of the 1.9 syntax (e.g. `{a: 1}`) when hashes have
  all symbols for keys
* hash_rockets - forces use of hash rockets for all hashes
* no_mixed_keys - simply checks for hashes with mixed syntaxes
* ruby19_no_mixed_keys - forces use of ruby 1.9 syntax and forbids mixed
  syntax hashes

### Examples

#### EnforcedStyle: ruby19 (default)

```ruby
# bad
{:a => 2}
{b: 1, :c => 2}

# good
{a: 2, b: 1}
{:c => 2, 'd' => 2} # acceptable since 'd' isn't a symbol
{d: 1, 'e' => 2} # technically not forbidden
```
#### EnforcedStyle: hash_rockets

```ruby
# bad
{a: 1, b: 2}
{c: 1, 'd' => 5}

# good
{:a => 1, :b => 2}
```
#### EnforcedStyle: no_mixed_keys

```ruby
# bad
{:a => 1, b: 2}
{c: 1, 'd' => 2}

# good
{:a => 1, :b => 2}
{c: 1, d: 2}
```
#### EnforcedStyle: ruby19_no_mixed_keys

```ruby
# bad
{:a => 1, :b => 2}
{c: 2, 'd' => 3} # should just use hash rockets

# good
{a: 1, b: 2}
{:c => 3, 'd' => 4}
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
EnforcedStyle | `ruby19` | `ruby19`, `hash_rockets`, `no_mixed_keys`, `ruby19_no_mixed_keys`
UseHashRocketsWithSymbolValues | `false` | Boolean
PreferHashRocketsForNonAlnumEndingSymbols | `false` | Boolean

### References

* [https://rubystyle.guide#hash-literals](https://rubystyle.guide#hash-literals)

## Style/IdenticalConditionalBranches

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | No | 0.36 | -

This cop checks for identical lines at the beginning or end of
each branch of a conditional statement.

### Examples

```ruby
# bad
if condition
  do_x
  do_z
else
  do_y
  do_z
end

# good
if condition
  do_x
else
  do_y
end
do_z

# bad
if condition
  do_z
  do_x
else
  do_z
  do_y
end

# good
do_z
if condition
  do_x
else
  do_y
end

# bad
case foo
when 1
  do_x
when 2
  do_x
else
  do_x
end

# good
case foo
when 1
  do_x
  do_y
when 2
  # nothing
else
  do_x
  do_z
end
```

## Style/IfInsideElse

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | No | 0.36 | -

If the `else` branch of a conditional consists solely of an `if` node,
it can be combined with the `else` to become an `elsif`.
This helps to keep the nesting level from getting too deep.

### Examples

```ruby
# bad
if condition_a
  action_a
else
  if condition_b
    action_b
  else
    action_c
  end
end

# good
if condition_a
  action_a
elsif condition_b
  action_b
else
  action_c
end
```
#### AllowIfModifier: false (default)

```ruby
# bad
if condition_a
  action_a
else
  action_b if condition_b
end

# good
if condition_a
  action_a
elsif condition_b
  action_b
end
```
#### AllowIfModifier: true

```ruby
# good
if condition_a
  action_a
else
  action_b if condition_b
end

# good
if condition_a
  action_a
elsif condition_b
  action_b
end
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
AllowIfModifier | `false` | Boolean

## Style/IfUnlessModifier

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.9 | 0.30

Checks for `if` and `unless` statements that would fit on one line if
written as modifier `if`/`unless`. The cop also checks for modifier
`if`/`unless` lines that exceed the maximum line length.

The maximum line length is configured in the `Metrics/LineLength`
cop. The tab size is configured in the `IndentationWidth` of the
`Layout/Tab` cop.

### Examples

```ruby
# bad
if condition
  do_stuff(bar)
end

unless qux.empty?
  Foo.do_something
end

do_something_in_a_method_with_a_long_name(arg) if long_condition

# good
do_stuff(bar) if condition
Foo.do_something unless qux.empty?

if long_condition
  do_something_in_a_method_with_a_long_name(arg)
end
```

### References

* [https://rubystyle.guide#if-as-a-modifier](https://rubystyle.guide#if-as-a-modifier)

## Style/IfUnlessModifierOfIfUnless

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | No | 0.39 | -

Checks for if and unless statements used as modifiers of other if or
unless statements.

### Examples

```ruby
# bad
tired? ? 'stop' : 'go faster' if running?

# bad
if tired?
  "please stop"
else
  "keep going"
end if running?

# good
if running?
  tired? ? 'stop' : 'go faster'
end
```

## Style/IfWithSemicolon

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | No | 0.9 | -

Checks for uses of semicolon in if statements.

### Examples

```ruby
# bad
result = if some_condition; something else another_thing end

# good
result = some_condition ? something : another_thing
```

### References

* [https://rubystyle.guide#no-semicolon-ifs](https://rubystyle.guide#no-semicolon-ifs)

## Style/ImplicitRuntimeError

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Disabled | Yes | No | 0.41 | -

This cop checks for `raise` or `fail` statements which do not specify an
explicit exception class. (This raises a `RuntimeError`. Some projects
might prefer to use exception classes which more precisely identify the
nature of the error.)

### Examples

```ruby
# bad
raise 'Error message here'

# good
raise ArgumentError, 'Error message here'
```

## Style/InfiniteLoop

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.26 | 0.61

Use `Kernel#loop` for infinite loops.

### Examples

```ruby
# bad
while true
  work
end

# good
loop do
  work
end
```

### References

* [https://rubystyle.guide#infinite-loop](https://rubystyle.guide#infinite-loop)

## Style/InlineComment

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Disabled | Yes | No | 0.23 | -

This cop checks for trailing inline comments.

### Examples

```ruby
# good
foo.each do |f|
  # Standalone comment
  f.bar
end

# bad
foo.each do |f|
  f.bar # Trailing inline comment
end
```

## Style/InverseMethods

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | No | Yes  | 0.48 | -

This cop check for usages of not (`not` or `!`) called on a method
when an inverse of that method can be used instead.
Methods that can be inverted by a not (`not` or `!`) should be defined
in `InverseMethods`
Methods that are inverted by inverting the return
of the block that is passed to the method should be defined in
`InverseBlocks`

### Examples

```ruby
# bad
!foo.none?
!foo.any? { |f| f.even? }
!foo.blank?
!(foo == bar)
foo.select { |f| !f.even? }
foo.reject { |f| f != 7 }

# good
foo.none?
foo.blank?
foo.any? { |f| f.even? }
foo != bar
foo == bar
!!('foo' =~ /^\w+$/)
!(foo.class < Numeric) # Checking class hierarchy is allowed
# Blocks with guard clauses are ignored:
foo.select do |f|
  next if f.zero?
  f != 1
end
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
InverseMethods | `{:any?=>:none?, :even?=>:odd?, :===>:!=, :=~=>:!~, :<=>:>=, :>=>:<=}` | 
InverseBlocks | `{:select=>:reject, :select!=>:reject!}` | 

## Style/IpAddresses

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Disabled | Yes | No | 0.58 | -

This cop checks for hardcoded IP addresses, which can make code
brittle. IP addresses are likely to need to be changed when code
is deployed to a different server or environment, which may break
a deployment if forgotten. Prefer setting IP addresses in ENV or
other configuration.

### Examples

```ruby
# bad
ip_address = '127.59.241.29'

# good
ip_address = ENV['DEPLOYMENT_IP_ADDRESS']
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
Whitelist | `::` | Array

## Style/Lambda

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.9 | 0.40

This cop (by default) checks for uses of the lambda literal syntax for
single line lambdas, and the method call syntax for multiline lambdas.
It is configurable to enforce one of the styles for both single line
and multiline lambdas as well.

### Examples

#### EnforcedStyle: line_count_dependent (default)

```ruby
# bad
f = lambda { |x| x }
f = ->(x) do
      x
    end

# good
f = ->(x) { x }
f = lambda do |x|
      x
    end
```
#### EnforcedStyle: lambda

```ruby
# bad
f = ->(x) { x }
f = ->(x) do
      x
    end

# good
f = lambda { |x| x }
f = lambda do |x|
      x
    end
```
#### EnforcedStyle: literal

```ruby
# bad
f = lambda { |x| x }
f = lambda do |x|
      x
    end

# good
f = ->(x) { x }
f = ->(x) do
      x
    end
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
EnforcedStyle | `line_count_dependent` | `line_count_dependent`, `lambda`, `literal`

### References

* [https://rubystyle.guide#lambda-multi-line](https://rubystyle.guide#lambda-multi-line)

## Style/LambdaCall

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.13.1 | 0.14

This cop checks for use of the lambda.(args) syntax.

### Examples

#### EnforcedStyle: call (default)

```ruby
# bad
lambda.(x, y)

# good
lambda.call(x, y)
```
#### EnforcedStyle: braces

```ruby
# bad
lambda.call(x, y)

# good
lambda.(x, y)
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
EnforcedStyle | `call` | `call`, `braces`

### References

* [https://rubystyle.guide#proc-call](https://rubystyle.guide#proc-call)

## Style/LineEndConcatenation

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes (Unsafe) | 0.18 | 0.64

This cop checks for string literal concatenation at
the end of a line.

### Examples

```ruby
# bad
some_str = 'ala' +
           'bala'

some_str = 'ala' <<
           'bala'

# good
some_str = 'ala' \
           'bala'
```

## Style/MethodCallWithArgsParentheses

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Disabled | Yes | Yes  | 0.47 | 0.61

This cop enforces the presence (default) or absence of parentheses in
method calls containing parameters.

In the default style (require_parentheses), macro methods are ignored.
Additional methods can be added to the `IgnoredMethods`
or `IgnoredPatterns` list. These options are
valid only in the default style. Macros can be included by
either setting `IgnoreMacros` to false or adding specific macros to
the `IncludedMacros` list.

Precedence of options is all follows:

1. `IgnoredMethods`
2. `IgnoredPatterns`
3. `IncludedMacros`

eg. If a method is listed in both
`IncludedMacros` and `IgnoredMethods`, then the latter takes
precedence (that is, the method is ignored).

In the alternative style (omit_parentheses), there are three additional
options.

1. `AllowParenthesesInChaining` is `false` by default. Setting it to
   `true` allows the presence of parentheses in the last call during
   method chaining.

2. `AllowParenthesesInMultilineCall` is `false` by default. Setting it
    to `true` allows the presence of parentheses in multi-line method
    calls.

3. `AllowParenthesesInCamelCaseMethod` is `false` by default. This
    allows the presence of parentheses when calling a method whose name
    begins with a capital letter and which has no arguments. Setting it
    to `true` allows the presence of parentheses in such a method call
    even with arguments.

### Examples

#### EnforcedStyle: require_parentheses (default)

```ruby
# bad
array.delete e

# good
array.delete(e)

# good
# Operators don't need parens
foo == bar

# good
# Setter methods don't need parens
foo.bar = baz

# okay with `puts` listed in `IgnoredMethods`
puts 'test'

# okay with `^assert` listed in `IgnoredPatterns`
assert_equal 'test', x

# IgnoreMacros: true (default)

# good
class Foo
  bar :baz
end

# IgnoreMacros: false

# bad
class Foo
  bar :baz
end
```
#### EnforcedStyle: omit_parentheses

```ruby
# bad
array.delete(e)

# good
array.delete e

# bad
foo.enforce(strict: true)

# good
foo.enforce strict: true

# AllowParenthesesInMultilineCall: false (default)

# bad
foo.enforce(
  strict: true
)

# good
foo.enforce \
  strict: true

# AllowParenthesesInMultilineCall: true

# good
foo.enforce(
  strict: true
)

# good
foo.enforce \
  strict: true

# AllowParenthesesInChaining: false (default)

# bad
foo().bar(1)

# good
foo().bar 1

# AllowParenthesesInChaining: true

# good
foo().bar(1)

# good
foo().bar 1

# AllowParenthesesInCamelCaseMethod: false (default)

# bad
Array(1)

# good
Array 1

# AllowParenthesesInCamelCaseMethod: true

# good
Array(1)

# good
Array 1
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
IgnoreMacros | `true` | Boolean
IgnoredMethods | `[]` | Array
IgnoredPatterns | `[]` | Array
IncludedMacros | `[]` | Array
AllowParenthesesInMultilineCall | `false` | Boolean
AllowParenthesesInChaining | `false` | Boolean
AllowParenthesesInCamelCaseMethod | `false` | Boolean
EnforcedStyle | `require_parentheses` | `require_parentheses`, `omit_parentheses`

### References

* [https://rubystyle.guide#method-invocation-parens](https://rubystyle.guide#method-invocation-parens)

## Style/MethodCallWithoutArgsParentheses

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.47 | 0.55

This cop checks for unwanted parentheses in parameterless method calls.

### Examples

```ruby
# bad
object.some_method()

# good
object.some_method
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
IgnoredMethods | `[]` | Array

### References

* [https://rubystyle.guide#method-invocation-parens](https://rubystyle.guide#method-invocation-parens)

## Style/MethodCalledOnDoEndBlock

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Disabled | Yes | No | 0.14 | -

This cop checks for methods called on a do...end block. The point of
this check is that it's easy to miss the call tacked on to the block
when reading code.

### Examples

```ruby
a do
  b
end.c
```

### References

* [https://rubystyle.guide#single-line-blocks](https://rubystyle.guide#single-line-blocks)

## Style/MethodDefParentheses

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.16 | 0.35

This cop checks for parentheses around the arguments in method
definitions. Both instance and class/singleton methods are checked.

### Examples

#### EnforcedStyle: require_parentheses (default)

```ruby
# The `require_parentheses` style requires method definitions
# to always use parentheses

# bad
def bar num1, num2
  num1 + num2
end

def foo descriptive_var_name,
        another_descriptive_var_name,
        last_descriptive_var_name
  do_something
end

# good
def bar(num1, num2)
  num1 + num2
end

def foo(descriptive_var_name,
        another_descriptive_var_name,
        last_descriptive_var_name)
  do_something
end
```
#### EnforcedStyle: require_no_parentheses

```ruby
# The `require_no_parentheses` style requires method definitions
# to never use parentheses

# bad
def bar(num1, num2)
  num1 + num2
end

def foo(descriptive_var_name,
        another_descriptive_var_name,
        last_descriptive_var_name)
  do_something
end

# good
def bar num1, num2
  num1 + num2
end

def foo descriptive_var_name,
        another_descriptive_var_name,
        last_descriptive_var_name
  do_something
end
```
#### EnforcedStyle: require_no_parentheses_except_multiline

```ruby
# The `require_no_parentheses_except_multiline` style prefers no
# parentheses when method definition arguments fit on single line,
# but prefers parentheses when arguments span multiple lines.

# bad
def bar(num1, num2)
  num1 + num2
end

def foo descriptive_var_name,
        another_descriptive_var_name,
        last_descriptive_var_name
  do_something
end

# good
def bar num1, num2
  num1 + num2
end

def foo(descriptive_var_name,
        another_descriptive_var_name,
        last_descriptive_var_name)
  do_something
end
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
EnforcedStyle | `require_parentheses` | `require_parentheses`, `require_no_parentheses`, `require_no_parentheses_except_multiline`

### References

* [https://rubystyle.guide#method-parens](https://rubystyle.guide#method-parens)

## Style/MethodMissingSuper

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | No | 0.56 | -

This cop checks for the presence of `method_missing` without
falling back on `super`.

### Examples

```ruby
#bad
def method_missing(name, *args)
  # ...
end

#good

def method_missing(name, *args)
  # ...
  super
end
```

### References

* [https://rubystyle.guide#no-method-missing](https://rubystyle.guide#no-method-missing)

## Style/MinMax

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.50 | -

This cop checks for potential uses of `Enumerable#minmax`.

### Examples

```ruby
# bad
bar = [foo.min, foo.max]
return foo.min, foo.max

# good
bar = foo.minmax
return foo.minmax
```

## Style/MissingElse

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Disabled | Yes | No | 0.30 | 0.38

Checks for `if` expressions that do not have an `else` branch.

Supported styles are: if, case, both.

### Examples

#### EnforcedStyle: if

```ruby
# warn when an `if` expression is missing an `else` branch.

# bad
if condition
  statement
end

# good
if condition
  statement
else
  # the content of `else` branch will be determined by Style/EmptyElse
end

# good
case var
when condition
  statement
end

# good
case var
when condition
  statement
else
  # the content of `else` branch will be determined by Style/EmptyElse
end
```
#### EnforcedStyle: case

```ruby
# warn when a `case` expression is missing an `else` branch.

# bad
case var
when condition
  statement
end

# good
case var
when condition
  statement
else
  # the content of `else` branch will be determined by Style/EmptyElse
end

# good
if condition
  statement
end

# good
if condition
  statement
else
  # the content of `else` branch will be determined by Style/EmptyElse
end
```
#### EnforcedStyle: both (default)

```ruby
# warn when an `if` or `case` expression is missing an `else` branch.

# bad
if condition
  statement
end

# bad
case var
when condition
  statement
end

# good
if condition
  statement
else
  # the content of `else` branch will be determined by Style/EmptyElse
end

# good
case var
when condition
  statement
else
  # the content of `else` branch will be determined by Style/EmptyElse
end
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
EnforcedStyle | `both` | `if`, `case`, `both`

## Style/MissingRespondToMissing

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | No | 0.56 | -

This cop checks for the presence of `method_missing` without also
defining `respond_to_missing?`.

### Examples

```ruby
#bad
def method_missing(name, *args)
  # ...
end

#good
def respond_to_missing?(name, include_private)
  # ...
end

def method_missing(name, *args)
  # ...
end
```

### References

* [https://rubystyle.guide#no-method-missing](https://rubystyle.guide#no-method-missing)

## Style/MixinGrouping

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.48 | 0.49

This cop checks for grouping of mixins in `class` and `module` bodies.
By default it enforces mixins to be placed in separate declarations,
but it can be configured to enforce grouping them in one declaration.

### Examples

#### EnforcedStyle: separated (default)

```ruby
# bad
class Foo
  include Bar, Qox
end

# good
class Foo
  include Qox
  include Bar
end
```
#### EnforcedStyle: grouped

```ruby
# bad
class Foo
  extend Bar
  extend Qox
end

# good
class Foo
  extend Qox, Bar
end
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
EnforcedStyle | `separated` | `separated`, `grouped`

### References

* [https://rubystyle.guide#mixin-grouping](https://rubystyle.guide#mixin-grouping)

## Style/MixinUsage

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | No | 0.51 | -

This cop checks that `include`, `extend` and `prepend` statements appear
inside classes and modules, not at the top level, so as to not affect
the behavior of `Object`.

### Examples

```ruby
# bad
include M

class C
end

# bad
extend M

class C
end

# bad
prepend M

class C
end

# good
class C
  include M
end

# good
class C
  extend M
end

# good
class C
  prepend M
end
```

## Style/ModuleFunction

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes (Unsafe) | 0.11 | 0.65

This cop checks for use of `extend self` or `module_function` in a
module.

Supported styles are: module_function, extend_self.

In case there are private methods, the cop won't be activated.
Otherwise, it forces to change the flow of the default code.

These offenses are not safe to auto-correct since there are different
implications to each approach.

### Examples

#### EnforcedStyle: module_function (default)

```ruby
# bad
module Test
  extend self
  # ...
end

# good
module Test
  module_function
  # ...
end
```
#### EnforcedStyle: module_function (default)

```ruby
# good
module Test
  extend self
  # ...
  private
  # ...
end
```
#### EnforcedStyle: extend_self

```ruby
# bad
module Test
  module_function
  # ...
end

# good
module Test
  extend self
  # ...
end
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
EnforcedStyle | `module_function` | `module_function`, `extend_self`
Autocorrect | `false` | Boolean

### References

* [https://rubystyle.guide#module-function](https://rubystyle.guide#module-function)

## Style/MultilineBlockChain

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | No | 0.13 | -

This cop checks for chaining of a block after another block that spans
multiple lines.

### Examples

```ruby
Thread.list.find_all do |t|
  t.alive?
end.map do |t|
  t.object_id
end
```

### References

* [https://rubystyle.guide#single-line-blocks](https://rubystyle.guide#single-line-blocks)

## Style/MultilineIfModifier

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.45 | -

Checks for uses of if/unless modifiers with multiple-lines bodies.

### Examples

```ruby
# bad
{
  result: 'this should not happen'
} unless cond

# good
{ result: 'ok' } if cond
```

### References

* [https://rubystyle.guide#no-multiline-if-modifiers](https://rubystyle.guide#no-multiline-if-modifiers)

## Style/MultilineIfThen

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.9 | 0.26

Checks for uses of the `then` keyword in multi-line if statements.

### Examples

```ruby
# bad
# This is considered bad practice.
if cond then
end

# good
# If statements can contain `then` on the same line.
if cond then a
elsif cond then b
end
```

### References

* [https://rubystyle.guide#no-then](https://rubystyle.guide#no-then)

## Style/MultilineMemoization

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.44 | 0.48

This cop checks expressions wrapping styles for multiline memoization.

### Examples

#### EnforcedStyle: keyword (default)

```ruby
# bad
foo ||= (
  bar
  baz
)

# good
foo ||= begin
  bar
  baz
end
```
#### EnforcedStyle: braces

```ruby
# bad
foo ||= begin
  bar
  baz
end

# good
foo ||= (
  bar
  baz
)
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
EnforcedStyle | `keyword` | `keyword`, `braces`

## Style/MultilineMethodSignature

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Disabled | Yes | No | 0.59 | -

This cop checks for method signatures that span multiple lines.

### Examples

```ruby
# good

def foo(bar, baz)
end

# bad

def foo(bar,
        baz)
end
```

## Style/MultilineTernaryOperator

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | No | 0.9 | -

This cop checks for multi-line ternary op expressions.

### Examples

```ruby
# bad
a = cond ?
  b : c
a = cond ? b :
    c
a = cond ?
    b :
    c

# good
a = cond ? b : c
a =
  if cond
    b
  else
    c
  end
```

### References

* [https://rubystyle.guide#no-multiline-ternary](https://rubystyle.guide#no-multiline-ternary)

## Style/MultilineWhenThen

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.73 | -

This cop checks uses of the `then` keyword
in multi-line when statements.

### Examples

```ruby
# bad
case foo
when bar then
end

# good
case foo
when bar
end

# good
case foo
when bar then do_something
end
```

### References

* [https://rubystyle.guide#no-then](https://rubystyle.guide#no-then)

## Style/MultipleComparison

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | No | 0.49 | -

This cop checks against comparing a variable with multiple items, where
`Array#include?` could be used instead to avoid code repetition.

### Examples

```ruby
# bad
a = 'a'
foo if a == 'a' || a == 'b' || a == 'c'

# good
a = 'a'
foo if ['a', 'b', 'c'].include?(a)
```

## Style/MutableConstant

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.34 | 0.65

This cop checks whether some constant value isn't a
mutable literal (e.g. array or hash).

Strict mode can be used to freeze all constants, rather than
just literals.
Strict mode is considered an experimental feature. It has not been
updated with an exhaustive list of all methods that will produce
frozen objects so there is a decent chance of getting some false
positives. Luckily, there is no harm in freezing an already
frozen object.

### Examples

#### EnforcedStyle: literals (default)

```ruby
# bad
CONST = [1, 2, 3]

# good
CONST = [1, 2, 3].freeze

# good
CONST = <<~TESTING.freeze
  This is a heredoc
TESTING

# good
CONST = Something.new
```
#### EnforcedStyle: strict

```ruby
# bad
CONST = Something.new

# bad
CONST = Struct.new do
  def foo
    puts 1
  end
end

# good
CONST = Something.new.freeze

# good
CONST = Struct.new do
  def foo
    puts 1
  end
end.freeze
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
EnforcedStyle | `literals` | `literals`, `strict`

## Style/NegatedIf

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.20 | 0.48

Checks for uses of if with a negated condition. Only ifs
without else are considered. There are three different styles:

  - both
  - prefix
  - postfix

### Examples

#### EnforcedStyle: both (default)

```ruby
# enforces `unless` for `prefix` and `postfix` conditionals

# bad

if !foo
  bar
end

# good

unless foo
  bar
end

# bad

bar if !foo

# good

bar unless foo
```
#### EnforcedStyle: prefix

```ruby
# enforces `unless` for just `prefix` conditionals

# bad

if !foo
  bar
end

# good

unless foo
  bar
end

# good

bar if !foo
```
#### EnforcedStyle: postfix

```ruby
# enforces `unless` for just `postfix` conditionals

# bad

bar if !foo

# good

bar unless foo

# good

if !foo
  bar
end
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
EnforcedStyle | `both` | `both`, `prefix`, `postfix`

### References

* [https://rubystyle.guide#unless-for-negatives](https://rubystyle.guide#unless-for-negatives)

## Style/NegatedUnless

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.69 | -

Checks for uses of unless with a negated condition. Only unless
without else are considered. There are three different styles:

  - both
  - prefix
  - postfix

### Examples

#### EnforcedStyle: both (default)

```ruby
# enforces `if` for `prefix` and `postfix` conditionals

# bad
unless !foo
  bar
end

# good
if foo
  bar
end

# bad
bar unless !foo

# good
bar if foo
```
#### EnforcedStyle: prefix

```ruby
# enforces `if` for just `prefix` conditionals

# bad
unless !foo
  bar
end

# good
if foo
  bar
end

# good
bar unless !foo
```
#### EnforcedStyle: postfix

```ruby
# enforces `if` for just `postfix` conditionals

# bad
bar unless !foo

# good
bar if foo

# good
unless !foo
  bar
end
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
EnforcedStyle | `both` | `both`, `prefix`, `postfix`

### References

* [https://rubystyle.guide#if-for-negatives](https://rubystyle.guide#if-for-negatives)

## Style/NegatedWhile

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.20 | -

Checks for uses of while with a negated condition.

### Examples

```ruby
# bad
while !foo
  bar
end

# good
until foo
  bar
end

# bad
bar until !foo

# good
bar while foo
bar while !foo && baz
```

### References

* [https://rubystyle.guide#until-for-negatives](https://rubystyle.guide#until-for-negatives)

## Style/NestedModifier

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.35 | -

This cop checks for nested use of if, unless, while and until in their
modifier form.

### Examples

```ruby
# bad
something if a if b

# good
something if b && a
```

### References

* [https://rubystyle.guide#no-nested-modifiers](https://rubystyle.guide#no-nested-modifiers)

## Style/NestedParenthesizedCalls

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.36 | 0.50

This cop checks for unparenthesized method calls in the argument list
of a parenthesized method call.

### Examples

```ruby
# good
method1(method2(arg), method3(arg))

# bad
method1(method2 arg, method3, arg)
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
Whitelist | `be`, `be_a`, `be_an`, `be_between`, `be_falsey`, `be_kind_of`, `be_instance_of`, `be_truthy`, `be_within`, `eq`, `eql`, `end_with`, `include`, `match`, `raise_error`, `respond_to`, `start_with` | Array

## Style/NestedTernaryOperator

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | No | 0.9 | -

This cop checks for nested ternary op expressions.

### Examples

```ruby
# bad
a ? (b ? b1 : b2) : a2

# good
if a
  b ? b1 : b2
else
  a2
end
```

### References

* [https://rubystyle.guide#no-nested-ternary](https://rubystyle.guide#no-nested-ternary)

## Style/Next

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.22 | 0.35

Use `next` to skip iteration instead of a condition at the end.

### Examples

#### EnforcedStyle: skip_modifier_ifs (default)

```ruby
# bad
[1, 2].each do |a|
  if a == 1
    puts a
  end
end

# good
[1, 2].each do |a|
  next unless a == 1
  puts a
end

# good
[1, 2].each do |o|
  puts o unless o == 1
end
```
#### EnforcedStyle: always

```ruby
# With `always` all conditions at the end of an iteration needs to be
# replaced by next - with `skip_modifier_ifs` the modifier if like
# this one are ignored: `[1, 2].each { |a| return 'yes' if a == 1 }`

# bad
[1, 2].each do |o|
  puts o unless o == 1
end

# bad
[1, 2].each do |a|
  if a == 1
    puts a
  end
end

# good
[1, 2].each do |a|
  next unless a == 1
  puts a
end
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
EnforcedStyle | `skip_modifier_ifs` | `skip_modifier_ifs`, `always`
MinBodyLength | `3` | Integer

### References

* [https://rubystyle.guide#no-nested-conditionals](https://rubystyle.guide#no-nested-conditionals)

## Style/NilComparison

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.12 | 0.59

This cop checks for comparison of something with nil using `==` and
`nil?`.

Supported styles are: predicate, comparison.

### Examples

#### EnforcedStyle: predicate (default)

```ruby
# bad
if x == nil
end

# good
if x.nil?
end
```
#### EnforcedStyle: comparison

```ruby
# bad
if x.nil?
end

# good
if x == nil
end
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
EnforcedStyle | `predicate` | `predicate`, `comparison`

### References

* [https://rubystyle.guide#predicate-methods](https://rubystyle.guide#predicate-methods)

## Style/NonNilCheck

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.20 | 0.22

This cop checks for non-nil checks, which are usually redundant.

Non-nil checks are allowed if they are the final nodes of predicate.

  # good
  def signed_in?
    !current_user.nil?
  end

### Examples

```ruby
# bad
if x != nil
end

# good (when not allowing semantic changes)
# bad (when allowing semantic changes)
if !x.nil?
end

# good (when allowing semantic changes)
if x
end
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
IncludeSemanticChanges | `false` | Boolean

### References

* [https://rubystyle.guide#no-non-nil-checks](https://rubystyle.guide#no-non-nil-checks)

## Style/Not

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.9 | 0.20

This cop checks for uses of the keyword `not` instead of `!`.

### Examples

```ruby
# bad - parentheses are required because of op precedence
x = (not something)

# good
x = !something
```

### References

* [https://rubystyle.guide#bang-not-not](https://rubystyle.guide#bang-not-not)

## Style/NumericLiteralPrefix

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.41 | -

This cop checks for octal, hex, binary, and decimal literals using
uppercase prefixes and corrects them to lowercase prefix
or no prefix (in case of decimals).

### Examples

#### EnforcedOctalStyle: zero_with_o (default)

```ruby
# bad - missing octal prefix
num = 01234

# bad - uppercase prefix
num = 0O1234
num = 0X12AB
num = 0B10101

# bad - redundant decimal prefix
num = 0D1234
num = 0d1234

# good
num = 0o1234
num = 0x12AB
num = 0b10101
num = 1234
```
#### EnforcedOctalStyle: zero_only

```ruby
# bad
num = 0o1234
num = 0O1234

# good
num = 01234
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
EnforcedOctalStyle | `zero_with_o` | `zero_with_o`, `zero_only`

### References

* [https://rubystyle.guide#numeric-literal-prefixes](https://rubystyle.guide#numeric-literal-prefixes)

## Style/NumericLiterals

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.9 | 0.48

This cop checks for big numeric literals without _ between groups
of digits in them.

### Examples

```ruby
# bad

1000000
1_00_000
1_0000

# good

1_000_000
1000

# good unless Strict is set

10_000_00 # typical representation of $10,000 in cents
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
MinDigits | `5` | Integer
Strict | `false` | Boolean

### References

* [https://rubystyle.guide#underscores-in-numerics](https://rubystyle.guide#underscores-in-numerics)

## Style/NumericPredicate

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | No | Yes (Unsafe) | 0.42 | 0.59

This cop checks for usage of comparison operators (`==`,
`>`, `<`) to test numbers as zero, positive, or negative.
These can be replaced by their respective predicate methods.
The cop can also be configured to do the reverse.

The cop disregards `#nonzero?` as it its value is truthy or falsey,
but not `true` and `false`, and thus not always interchangeable with
`!= 0`.

The cop ignores comparisons to global variables, since they are often
populated with objects which can be compared with integers, but are
not themselves `Integer` polymorphic.

### Examples

#### EnforcedStyle: predicate (default)

```ruby
# bad

foo == 0
0 > foo
bar.baz > 0

# good

foo.zero?
foo.negative?
bar.baz.positive?
```
#### EnforcedStyle: comparison

```ruby
# bad

foo.zero?
foo.negative?
bar.baz.positive?

# good

foo == 0
0 > foo
bar.baz > 0
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
AutoCorrect | `false` | Boolean
EnforcedStyle | `predicate` | `predicate`, `comparison`
IgnoredMethods | `[]` | Array
Exclude | `spec/**/*` | Array

### References

* [https://rubystyle.guide#predicate-methods](https://rubystyle.guide#predicate-methods)

## Style/OneLineConditional

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.9 | 0.38

TODO: Make configurable.
Checks for uses of if/then/else/end on a single line.

### Examples

```ruby
# bad
if foo then boo else doo end
unless foo then boo else goo end

# good
foo ? boo : doo
boo if foo
if foo then boo end

# good
if foo
  boo
else
  doo
end
```

### References

* [https://rubystyle.guide#ternary-operator](https://rubystyle.guide#ternary-operator)

## Style/OptionHash

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Disabled | Yes | No | 0.33 | 0.34

This cop checks for options hashes and discourages them if the
current Ruby version supports keyword arguments.

### Examples

```ruby
# bad
def fry(options = {})
  temperature = options.fetch(:temperature, 300)
  # ...
end

# good
def fry(temperature: 300)
  # ...
end
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
SuspiciousParamNames | `options`, `opts`, `args`, `params`, `parameters` | Array

## Style/OptionalArguments

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | No | 0.33 | -

This cop checks for optional arguments to methods
that do not come at the end of the argument list

### Examples

```ruby
# bad
def foo(a = 1, b, c)
end

# good
def baz(a, b, c = 1)
end

def foobar(a = 1, b = 2, c = 3)
end
```

### References

* [https://rubystyle.guide#optional-arguments](https://rubystyle.guide#optional-arguments)

## Style/OrAssignment

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.50 | -

This cop checks for potential usage of the `||=` operator.

### Examples

```ruby
# bad
name = name ? name : 'Bozhidar'

# bad
name = if name
         name
       else
         'Bozhidar'
       end

# bad
unless name
  name = 'Bozhidar'
end

# bad
name = 'Bozhidar' unless name

# good - set name to 'Bozhidar', only if it's nil or false
name ||= 'Bozhidar'
```

### References

* [https://rubystyle.guide#double-pipe-for-uninit](https://rubystyle.guide#double-pipe-for-uninit)

## Style/ParallelAssignment

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.32 | -

Checks for simple usages of parallel assignment.
This will only complain when the number of variables
being assigned matched the number of assigning variables.

### Examples

```ruby
# bad
a, b, c = 1, 2, 3
a, b, c = [1, 2, 3]

# good
one, two = *foo
a, b = foo()
a, b = b, a

a = 1
b = 2
c = 3
```

### References

* [https://rubystyle.guide#parallel-assignment](https://rubystyle.guide#parallel-assignment)

## Style/ParenthesesAroundCondition

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.9 | 0.56

This cop checks for the presence of superfluous parentheses around the
condition of if/unless/while/until.

### Examples

```ruby
# bad
x += 1 while (x < 10)
foo unless (bar || baz)

if (x > 10)
elsif (x < 3)
end

# good
x += 1 while x < 10
foo unless bar || baz

if x > 10
elsif x < 3
end
```
#### AllowInMultilineConditions: false (default)

```ruby
# bad
if (x > 10 &&
   y > 10)
end

# good
 if x > 10 &&
    y > 10
 end
```
#### AllowInMultilineConditions: true

```ruby
# good
if (x > 10 &&
   y > 10)
end
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
AllowSafeAssignment | `true` | Boolean
AllowInMultilineConditions | `false` | Boolean

### References

* [https://rubystyle.guide#no-parens-around-condition](https://rubystyle.guide#no-parens-around-condition)

## Style/PercentLiteralDelimiters

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.19 | 0.48.1

This cop enforces the consistent usage of `%`-literal delimiters.

Specify the 'default' key to set all preferred delimiters at once. You
can continue to specify individual preferred delimiters to override the
default.

### Examples

```ruby
# Style/PercentLiteralDelimiters:
#   PreferredDelimiters:
#     default: '[]'
#     '%i':    '()'

# good
%w[alpha beta] + %i(gamma delta)

# bad
%W(alpha #{beta})

# bad
%I(alpha beta)
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
PreferredDelimiters | `{"default"=>"()", "%i"=>"[]", "%I"=>"[]", "%r"=>"{}", "%w"=>"[]", "%W"=>"[]"}` | 

### References

* [https://rubystyle.guide#percent-literal-braces](https://rubystyle.guide#percent-literal-braces)

## Style/PercentQLiterals

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.25 | -

This cop checks for usage of the %Q() syntax when %q() would do.

### Examples

#### EnforcedStyle: lower_case_q (default)

```ruby
# The `lower_case_q` style prefers `%q` unless
# interpolation is needed.
# bad
%Q[Mix the foo into the baz.]
%Q(They all said: 'Hooray!')

# good
%q[Mix the foo into the baz]
%q(They all said: 'Hooray!')
```
#### EnforcedStyle: upper_case_q

```ruby
# The `upper_case_q` style requires the sole use of `%Q`.
# bad
%q/Mix the foo into the baz./
%q{They all said: 'Hooray!'}

# good
%Q/Mix the foo into the baz./
%Q{They all said: 'Hooray!'}
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
EnforcedStyle | `lower_case_q` | `lower_case_q`, `upper_case_q`

## Style/PerlBackrefs

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.13 | -

This cop looks for uses of Perl-style regexp match
backreferences like $1, $2, etc.

### Examples

```ruby
# bad
puts $1

# good
puts Regexp.last_match(1)
```

### References

* [https://rubystyle.guide#no-perl-regexp-last-matchers](https://rubystyle.guide#no-perl-regexp-last-matchers)

## Style/PreferredHashMethods

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | No | Yes  | 0.41 | 0.70

This cop (by default) checks for uses of methods Hash#has_key? and
Hash#has_value? where it enforces Hash#key? and Hash#value?
It is configurable to enforce the inverse, using `verbose` method
names also.

### Examples

#### EnforcedStyle: short (default)

```ruby
# bad
Hash#has_key?
Hash#has_value?

# good
Hash#key?
Hash#value?
```
#### EnforcedStyle: verbose

```ruby
# bad
Hash#key?
Hash#value?

# good
Hash#has_key?
Hash#has_value?
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
EnforcedStyle | `short` | `short`, `verbose`

### References

* [https://rubystyle.guide#hash-key](https://rubystyle.guide#hash-key)

## Style/Proc

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.9 | 0.18

This cop checks for uses of Proc.new where Kernel#proc
would be more appropriate.

### Examples

```ruby
# bad
p = Proc.new { |n| puts n }

# good
p = proc { |n| puts n }
```

### References

* [https://rubystyle.guide#proc](https://rubystyle.guide#proc)

## Style/RaiseArgs

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.14 | 0.40

This cop checks the args passed to `fail` and `raise`. For exploded
style (default), it recommends passing the exception class and message
to `raise`, rather than construct an instance of the error. It will
still allow passing just a message, or the construction of an error
with more than one argument.

The exploded style works identically, but with the addition that it
will also suggest constructing error objects when the exception is
passed multiple arguments.

### Examples

#### EnforcedStyle: exploded (default)

```ruby
# bad
raise StandardError.new("message")

# good
raise StandardError, "message"
fail "message"
raise MyCustomError.new(arg1, arg2, arg3)
raise MyKwArgError.new(key1: val1, key2: val2)
```
#### EnforcedStyle: compact

```ruby
# bad
raise StandardError, "message"
raise RuntimeError, arg1, arg2, arg3

# good
raise StandardError.new("message")
raise MyCustomError.new(arg1, arg2, arg3)
fail "message"
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
EnforcedStyle | `exploded` | `compact`, `exploded`

### References

* [https://rubystyle.guide#exception-class-messages](https://rubystyle.guide#exception-class-messages)

## Style/RandomWithOffset

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.52 | -

This cop checks for the use of randomly generated numbers,
added/subtracted with integer literals, as well as those with
Integer#succ and Integer#pred methods. Prefer using ranges instead,
as it clearly states the intentions.

### Examples

```ruby
# bad
rand(6) + 1
1 + rand(6)
rand(6) - 1
1 - rand(6)
rand(6).succ
rand(6).pred
Random.rand(6) + 1
Kernel.rand(6) + 1
rand(0..5) + 1

# good
rand(1..6)
rand(1...7)
```

### References

* [https://rubystyle.guide#random-numbers](https://rubystyle.guide#random-numbers)

## Style/RedundantBegin

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.10 | 0.21

This cop checks for redundant `begin` blocks.

Currently it checks for code like this:

### Examples

```ruby
# bad
def redundant
  begin
    ala
    bala
  rescue StandardError => e
    something
  end
end

# good
def preferred
  ala
  bala
rescue StandardError => e
  something
end

# bad
# When using Ruby 2.5 or later.
do_something do
  begin
    something
  rescue => ex
    anything
  end
end

# good
# In Ruby 2.5 or later, you can omit `begin` in `do-end` block.
do_something do
  something
rescue => ex
  anything
end

# good
# Stabby lambdas don't support implicit `begin` in `do-end` blocks.
-> do
  begin
    foo
  rescue Bar
    baz
  end
end
```

### References

* [https://rubystyle.guide#begin-implicit](https://rubystyle.guide#begin-implicit)

## Style/RedundantConditional

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.50 | -

This cop checks for redundant returning of true/false in conditionals.

### Examples

```ruby
# bad
x == y ? true : false

# bad
if x == y
  true
else
  false
end

# good
x == y

# bad
x == y ? false : true

# good
x != y
```

## Style/RedundantException

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.14 | 0.29

This cop checks for RuntimeError as the argument of raise/fail.

It checks for code like this:

### Examples

```ruby
# Bad
raise RuntimeError, 'message'

# Bad
raise RuntimeError.new('message')

# Good
raise 'message'
```

### References

* [https://rubystyle.guide#no-explicit-runtimeerror](https://rubystyle.guide#no-explicit-runtimeerror)

## Style/RedundantFreeze

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.34 | 0.66

This cop check for uses of Object#freeze on immutable objects.

### Examples

```ruby
# bad
CONST = 1.freeze

# good
CONST = 1
```

## Style/RedundantParentheses

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.36 | -

This cop checks for redundant parentheses.

### Examples

```ruby
# bad
(x) if ((y.z).nil?)

# good
x if y.z.nil?
```

## Style/RedundantReturn

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.10 | 0.14

This cop checks for redundant `return` expressions.

### Examples

```ruby
# These bad cases should be extended to handle methods whose body is
# if/else or a case expression with a default branch.

# bad
def test
  return something
end

# bad
def test
  one
  two
  three
  return something
end

# good
def test
  return something if something_else
end

# good
def test
  if x
  elsif y
  else
  end
end
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
AllowMultipleReturnValues | `false` | Boolean

### References

* [https://rubystyle.guide#no-explicit-return](https://rubystyle.guide#no-explicit-return)

## Style/RedundantSelf

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.10 | 0.13

This cop checks for redundant uses of `self`.

The usage of `self` is only needed when:

* Sending a message to same object with zero arguments in
  presence of a method name clash with an argument or a local
  variable.

* Calling an attribute writer to prevent an local variable assignment.

Note, with using explicit self you can only send messages with public or
protected scope, you cannot send private messages this way.

Note we allow uses of `self` with operators because it would be awkward
otherwise.

### Examples

```ruby
# bad
def foo(bar)
  self.baz
end

# good
def foo(bar)
  self.bar  # Resolves name clash with the argument.
end

def foo
  bar = 1
  self.bar  # Resolves name clash with the local variable.
end

def foo
  %w[x y z].select do |bar|
    self.bar == bar  # Resolves name clash with argument of the block.
  end
end
```

### References

* [https://rubystyle.guide#no-self-unless-required](https://rubystyle.guide#no-self-unless-required)

## Style/RedundantSortBy

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.36 | -

This cop identifies places where `sort_by { ... }` can be replaced by
`sort`.

### Examples

```ruby
# bad
array.sort_by { |x| x }
array.sort_by do |var|
  var
end

# good
array.sort
```

## Style/RegexpLiteral

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.9 | 0.30

This cop enforces using // or %r around regular expressions.

### Examples

#### EnforcedStyle: slashes (default)

```ruby
# bad
snake_case = %r{^[\dA-Z_]+$}

# bad
regex = %r{
  foo
  (bar)
  (baz)
}x

# good
snake_case = /^[\dA-Z_]+$/

# good
regex = /
  foo
  (bar)
  (baz)
/x
```
#### EnforcedStyle: percent_r

```ruby
# bad
snake_case = /^[\dA-Z_]+$/

# bad
regex = /
  foo
  (bar)
  (baz)
/x

# good
snake_case = %r{^[\dA-Z_]+$}

# good
regex = %r{
  foo
  (bar)
  (baz)
}x
```
#### EnforcedStyle: mixed

```ruby
# bad
snake_case = %r{^[\dA-Z_]+$}

# bad
regex = /
  foo
  (bar)
  (baz)
/x

# good
snake_case = /^[\dA-Z_]+$/

# good
regex = %r{
  foo
  (bar)
  (baz)
}x
```
#### AllowInnerSlashes: false (default)

```ruby
# If `false`, the cop will always recommend using `%r` if one or more
# slashes are found in the regexp string.

# bad
x =~ /home\//

# good
x =~ %r{home/}
```
#### AllowInnerSlashes: true

```ruby
# good
x =~ /home\//
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
EnforcedStyle | `slashes` | `slashes`, `percent_r`, `mixed`
AllowInnerSlashes | `false` | Boolean

### References

* [https://rubystyle.guide#percent-r](https://rubystyle.guide#percent-r)

## Style/RescueModifier

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.9 | 0.34

This cop checks for uses of rescue in its modifier form.

The cop to check `rescue` in its modifier form is added for following
reasons:

* The syntax of modifier form `rescue` can be misleading because it
  might led us to believe that `rescue` handles the given exception
  but it actually rescue all exceptions to return the given rescue
  block. In this case, value returned by handle_error or
  SomeException.

* Modifier form `rescue` would rescue all the exceptions. It would
  silently skip all exception or errors and handle the error.
  Example: If `NoMethodError` is raised, modifier form rescue would
  handle the exception.

### Examples

```ruby
# bad
some_method rescue handle_error

# bad
some_method rescue SomeException

# good
begin
  some_method
rescue
  handle_error
end

# good
begin
  some_method
rescue SomeException
  handle_error
end
```

### References

* [https://rubystyle.guide#no-rescue-modifiers](https://rubystyle.guide#no-rescue-modifiers)

## Style/RescueStandardError

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.52 | -

This cop checks for rescuing `StandardError`. There are two supported
styles `implicit` and `explicit`. This cop will not register an offense
if any error other than `StandardError` is specified.

### Examples

#### EnforcedStyle: implicit

```ruby
# `implicit` will enforce using `rescue` instead of
# `rescue StandardError`.

# bad
begin
  foo
rescue StandardError
  bar
end

# good
begin
  foo
rescue
  bar
end

# good
begin
  foo
rescue OtherError
  bar
end

# good
begin
  foo
rescue StandardError, SecurityError
  bar
end
```
#### EnforcedStyle: explicit (default)

```ruby
# `explicit` will enforce using `rescue StandardError`
# instead of `rescue`.

# bad
begin
  foo
rescue
  bar
end

# good
begin
  foo
rescue StandardError
  bar
end

# good
begin
  foo
rescue OtherError
  bar
end

# good
begin
  foo
rescue StandardError, SecurityError
  bar
end
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
EnforcedStyle | `explicit` | `implicit`, `explicit`

## Style/ReturnNil

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Disabled | Yes | Yes  | 0.50 | -

This cop enforces consistency between 'return nil' and 'return'.

Supported styles are: return, return_nil.

### Examples

#### EnforcedStyle: return (default)

```ruby
# bad
def foo(arg)
  return nil if arg
end

# good
def foo(arg)
  return if arg
end
```
#### EnforcedStyle: return_nil

```ruby
# bad
def foo(arg)
  return if arg
end

# good
def foo(arg)
  return nil if arg
end
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
EnforcedStyle | `return` | `return`, `return_nil`

## Style/SafeNavigation

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.43 | 0.56

This cop transforms usages of a method call safeguarded by a non `nil`
check for the variable whose method is being called to
safe navigation (`&.`). If there is a method chain, all of the methods
in the chain need to be checked for safety, and all of the methods will
need to be changed to use safe navigation. We have limited the cop to
not register an offense for method chains that exceed 2 methods.

Configuration option: ConvertCodeThatCanStartToReturnNil
The default for this is `false`. When configured to `true`, this will
check for code in the format `!foo.nil? && foo.bar`. As it is written,
the return of this code is limited to `false` and whatever the return
of the method is. If this is converted to safe navigation,
`foo&.bar` can start returning `nil` as well as what the method
returns.

### Examples

```ruby
# bad
foo.bar if foo
foo.bar.baz if foo
foo.bar(param1, param2) if foo
foo.bar { |e| e.something } if foo
foo.bar(param) { |e| e.something } if foo

foo.bar if !foo.nil?
foo.bar unless !foo
foo.bar unless foo.nil?

foo && foo.bar
foo && foo.bar.baz
foo && foo.bar(param1, param2)
foo && foo.bar { |e| e.something }
foo && foo.bar(param) { |e| e.something }

# good
foo&.bar
foo&.bar&.baz
foo&.bar(param1, param2)
foo&.bar { |e| e.something }
foo&.bar(param) { |e| e.something }
foo && foo.bar.baz.qux # method chain with more than 2 methods
foo && foo.nil? # method that `nil` responds to

# Method calls that do not use `.`
foo && foo < bar
foo < bar if foo

# This could start returning `nil` as well as the return of the method
foo.nil? || foo.bar
!foo || foo.bar

# Methods that are used on assignment, arithmetic operation or
# comparison should not be converted to use safe navigation
foo.baz = bar if foo
foo.baz + bar if foo
foo.bar > 2 if foo
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
ConvertCodeThatCanStartToReturnNil | `false` | Boolean
Whitelist | `present?`, `blank?`, `presence`, `try`, `try!` | Array

## Style/Sample

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.30 | -

This cop is used to identify usages of `shuffle.first`,
`shuffle.last`, and `shuffle[]` and change them to use
`sample` instead.

### Examples

```ruby
# bad
[1, 2, 3].shuffle.first
[1, 2, 3].shuffle.first(2)
[1, 2, 3].shuffle.last
[2, 1, 3].shuffle.at(0)
[2, 1, 3].shuffle.slice(0)
[1, 2, 3].shuffle[2]
[1, 2, 3].shuffle[0, 2]    # sample(2) will do the same
[1, 2, 3].shuffle[0..2]    # sample(3) will do the same
[1, 2, 3].shuffle(random: Random.new).first

# good
[1, 2, 3].shuffle
[1, 2, 3].sample
[1, 2, 3].sample(3)
[1, 2, 3].shuffle[1, 3]    # sample(3) might return a longer Array
[1, 2, 3].shuffle[1..3]    # sample(3) might return a longer Array
[1, 2, 3].shuffle[foo, bar]
[1, 2, 3].shuffle(random: Random.new)
```

### References

* [https://github.com/JuanitoFatas/fast-ruby#arrayshufflefirst-vs-arraysample-code](https://github.com/JuanitoFatas/fast-ruby#arrayshufflefirst-vs-arraysample-code)

## Style/SelfAssignment

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.19 | 0.29

This cop enforces the use the shorthand for self-assignment.

### Examples

```ruby
# bad
x = x + 1

# good
x += 1
```

### References

* [https://rubystyle.guide#self-assignment](https://rubystyle.guide#self-assignment)

## Style/Semicolon

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.9 | 0.19

This cop checks for multiple expressions placed on the same line.
It also checks for lines terminated with a semicolon.

### Examples

```ruby
# bad
foo = 1; bar = 2;
baz = 3;

# good
foo = 1
bar = 2
baz = 3
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
AllowAsExpressionSeparator | `false` | Boolean

### References

* [https://rubystyle.guide#no-semicolon](https://rubystyle.guide#no-semicolon)

## Style/Send

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Disabled | Yes | No | 0.33 | -

This cop checks for the use of the send method.

### Examples

```ruby
# bad
Foo.send(:bar)
quuz.send(:fred)

# good
Foo.__send__(:bar)
quuz.public_send(:fred)
```

### References

* [https://rubystyle.guide#prefer-public-send](https://rubystyle.guide#prefer-public-send)

## Style/SignalException

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.11 | 0.37

This cop checks for uses of `fail` and `raise`.

### Examples

#### EnforcedStyle: only_raise (default)

```ruby
# The `only_raise` style enforces the sole use of `raise`.
# bad
begin
  fail
rescue Exception
  # handle it
end

def watch_out
  fail
rescue Exception
  # handle it
end

Kernel.fail

# good
begin
  raise
rescue Exception
  # handle it
end

def watch_out
  raise
rescue Exception
  # handle it
end

Kernel.raise
```
#### EnforcedStyle: only_fail

```ruby
# The `only_fail` style enforces the sole use of `fail`.
# bad
begin
  raise
rescue Exception
  # handle it
end

def watch_out
  raise
rescue Exception
  # handle it
end

Kernel.raise

# good
begin
  fail
rescue Exception
  # handle it
end

def watch_out
  fail
rescue Exception
  # handle it
end

Kernel.fail
```
#### EnforcedStyle: semantic

```ruby
# The `semantic` style enforces the use of `fail` to signal an
# exception, then will use `raise` to trigger an offense after
# it has been rescued.
# bad
begin
  raise
rescue Exception
  # handle it
end

def watch_out
  # Error thrown
rescue Exception
  fail
end

Kernel.fail
Kernel.raise

# good
begin
  fail
rescue Exception
  # handle it
end

def watch_out
  fail
rescue Exception
  raise 'Preferably with descriptive message'
end

explicit_receiver.fail
explicit_receiver.raise
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
EnforcedStyle | `only_raise` | `only_raise`, `only_fail`, `semantic`

### References

* [https://rubystyle.guide#prefer-raise-over-fail](https://rubystyle.guide#prefer-raise-over-fail)

## Style/SingleLineBlockParams

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Disabled | Yes | No | 0.16 | 0.47

This cop checks whether the block parameters of a single-line
method accepting a block match the names specified via configuration.

For instance one can configure `reduce`(`inject`) to use |a, e| as
parameters.

Configuration option: Methods
Should be set to use this cop. Array of hashes, where each key is the
method name and value - array of argument names.

### Examples

#### Methods: [{reduce: %w[a b]}]

```ruby
# bad
foo.reduce { |c, d| c + d }
foo.reduce { |_, _d| 1 }

# good
foo.reduce { |a, b| a + b }
foo.reduce { |a, _b| a }
foo.reduce { |a, (id, _)| a + id }
foo.reduce { true }

# good
foo.reduce do |c, d|
  c + d
end
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
Methods | `{"reduce"=>["acc", "elem"]}`, `{"inject"=>["acc", "elem"]}` | Array

## Style/SingleLineMethods

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.9 | 0.19

This cop checks for single-line method definitions that contain a body.
It will accept single-line methods with no body.

### Examples

```ruby
# bad
def some_method; body end
def link_to(url); {:name => url}; end
def @table.columns; super; end

# good
def no_op; end
def self.resource_class=(klass); end
def @table.columns; end
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
AllowIfMethodIsEmpty | `true` | Boolean

### References

* [https://rubystyle.guide#no-single-line-methods](https://rubystyle.guide#no-single-line-methods)

## Style/SpecialGlobalVars

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes (Unsafe) | 0.13 | 0.36

This cop looks for uses of Perl-style global variables.

### Examples

#### EnforcedStyle: use_english_names (default)

```ruby
# good
puts $LOAD_PATH
puts $LOADED_FEATURES
puts $PROGRAM_NAME
puts $ERROR_INFO
puts $ERROR_POSITION
puts $FIELD_SEPARATOR # or $FS
puts $OUTPUT_FIELD_SEPARATOR # or $OFS
puts $INPUT_RECORD_SEPARATOR # or $RS
puts $OUTPUT_RECORD_SEPARATOR # or $ORS
puts $INPUT_LINE_NUMBER # or $NR
puts $LAST_READ_LINE
puts $DEFAULT_OUTPUT
puts $DEFAULT_INPUT
puts $PROCESS_ID # or $PID
puts $CHILD_STATUS
puts $LAST_MATCH_INFO
puts $IGNORECASE
puts $ARGV # or ARGV
puts $MATCH
puts $PREMATCH
puts $POSTMATCH
puts $LAST_PAREN_MATCH
```
#### EnforcedStyle: use_perl_names

```ruby
# good
puts $:
puts $"
puts $0
puts $!
puts $@
puts $;
puts $,
puts $/
puts $\
puts $.
puts $_
puts $>
puts $<
puts $$
puts $?
puts $~
puts $=
puts $*
puts $&
puts $`
puts $'
puts $+
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
EnforcedStyle | `use_english_names` | `use_perl_names`, `use_english_names`

### References

* [https://rubystyle.guide#no-cryptic-perlisms](https://rubystyle.guide#no-cryptic-perlisms)

## Style/StabbyLambdaParentheses

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.35 | -

Check for parentheses around stabby lambda arguments.
There are two different styles. Defaults to `require_parentheses`.

### Examples

#### EnforcedStyle: require_parentheses (default)

```ruby
# bad
->a,b,c { a + b + c }

# good
->(a,b,c) { a + b + c}
```
#### EnforcedStyle: require_no_parentheses

```ruby
# bad
->(a,b,c) { a + b + c }

# good
->a,b,c { a + b + c}
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
EnforcedStyle | `require_parentheses` | `require_parentheses`, `require_no_parentheses`

### References

* [https://rubystyle.guide#stabby-lambda-with-args](https://rubystyle.guide#stabby-lambda-with-args)

## Style/StderrPuts

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.51 | -

This cop identifies places where `$stderr.puts` can be replaced by
`warn`. The latter has the advantage of easily being disabled by,
the `-W0` interpreter flag or setting `$VERBOSE` to `nil`.

### Examples

```ruby
# bad
$stderr.puts('hello')

# good
warn('hello')
```

### References

* [https://rubystyle.guide#warn](https://rubystyle.guide#warn)

## Style/StringHashKeys

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Disabled | No | Yes  | 0.52 | 0.75

This cop checks for the use of strings as keys in hashes. The use of
symbols is preferred instead.

### Examples

```ruby
# bad
{ 'one' => 1, 'two' => 2, 'three' => 3 }

# good
{ one: 1, two: 2, three: 3 }
```

### References

* [https://rubystyle.guide#symbols-as-keys](https://rubystyle.guide#symbols-as-keys)

## Style/StringLiterals

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.9 | 0.36

Checks if uses of quotes match the configured preference.

### Examples

#### EnforcedStyle: single_quotes (default)

```ruby
# bad
"No special symbols"
"No string interpolation"
"Just text"

# good
'No special symbols'
'No string interpolation'
'Just text'
"Wait! What's #{this}!"
```
#### EnforcedStyle: double_quotes

```ruby
# bad
'Just some text'
'No special chars or interpolation'

# good
"Just some text"
"No special chars or interpolation"
"Every string in #{project} uses double_quotes"
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
EnforcedStyle | `single_quotes` | `single_quotes`, `double_quotes`
ConsistentQuotesInMultiline | `false` | Boolean

### References

* [https://rubystyle.guide#consistent-string-literals](https://rubystyle.guide#consistent-string-literals)

## Style/StringLiteralsInInterpolation

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.27 | -

This cop checks that quotes inside the string interpolation
match the configured preference.

### Examples

#### EnforcedStyle: single_quotes (default)

```ruby
# bad
result = "Tests #{success ? "PASS" : "FAIL"}"

# good
result = "Tests #{success ? 'PASS' : 'FAIL'}"
```
#### EnforcedStyle: double_quotes

```ruby
# bad
result = "Tests #{success ? 'PASS' : 'FAIL'}"

# good
result = "Tests #{success ? "PASS" : "FAIL"}"
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
EnforcedStyle | `single_quotes` | `single_quotes`, `double_quotes`

## Style/StringMethods

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Disabled | Yes | Yes  | 0.34 | 0.34.2

This cop enforces the use of consistent method names
from the String class.

### Examples

```ruby
# bad
'name'.intern
'var'.unfavored_method

# good
'name'.to_sym
'var'.preferred_method
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
PreferredMethods | `{"intern"=>"to_sym"}` | 

## Style/Strip

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.36 | -

This cop identifies places where `lstrip.rstrip` can be replaced by
`strip`.

### Examples

```ruby
# bad
'abc'.lstrip.rstrip
'abc'.rstrip.lstrip

# good
'abc'.strip
```

## Style/StructInheritance

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | No | 0.29 | -

This cop checks for inheritance from Struct.new.

### Examples

```ruby
# bad
class Person < Struct.new(:first_name, :last_name)
  def age
    42
  end
end

# good
Person = Struct.new(:first_name, :last_name) do
  def age
    42
  end
end
```

### References

* [https://rubystyle.guide#no-extend-struct-new](https://rubystyle.guide#no-extend-struct-new)

## Style/SymbolArray

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.9 | 0.49

This cop can check for array literals made up of symbols that are not
using the %i() syntax.

Alternatively, it checks for symbol arrays using the %i() syntax on
projects which do not want to use that syntax.

Configuration option: MinSize
If set, arrays with fewer elements than this value will not trigger the
cop. For example, a `MinSize of `3` will not enforce a style on an array
of 2 or fewer elements.

### Examples

#### EnforcedStyle: percent (default)

```ruby
# good
%i[foo bar baz]

# bad
[:foo, :bar, :baz]
```
#### EnforcedStyle: brackets

```ruby
# good
[:foo, :bar, :baz]

# bad
%i[foo bar baz]
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
EnforcedStyle | `percent` | `percent`, `brackets`
MinSize | `2` | Integer

### References

* [https://rubystyle.guide#percent-i](https://rubystyle.guide#percent-i)

## Style/SymbolLiteral

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.30 | -

This cop checks symbol literal syntax.

### Examples

```ruby
# bad
:"symbol"

# good
:symbol
```

## Style/SymbolProc

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes (Unsafe) | 0.26 | 0.64

Use symbols as procs when possible.

### Examples

```ruby
# bad
something.map { |s| s.upcase }

# good
something.map(&:upcase)
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
IgnoredMethods | `respond_to`, `define_method` | Array

## Style/TernaryParentheses

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.42 | 0.46

This cop checks for the presence of parentheses around ternary
conditions. It is configurable to enforce inclusion or omission of
parentheses using `EnforcedStyle`. Omission is only enforced when
removing the parentheses won't cause a different behavior.

### Examples

#### EnforcedStyle: require_no_parentheses (default)

```ruby
# bad
foo = (bar?) ? a : b
foo = (bar.baz?) ? a : b
foo = (bar && baz) ? a : b

# good
foo = bar? ? a : b
foo = bar.baz? ? a : b
foo = bar && baz ? a : b
```
#### EnforcedStyle: require_parentheses

```ruby
# bad
foo = bar? ? a : b
foo = bar.baz? ? a : b
foo = bar && baz ? a : b

# good
foo = (bar?) ? a : b
foo = (bar.baz?) ? a : b
foo = (bar && baz) ? a : b
```
#### EnforcedStyle: require_parentheses_when_complex

```ruby
# bad
foo = (bar?) ? a : b
foo = (bar.baz?) ? a : b
foo = bar && baz ? a : b

# good
foo = bar? ? a : b
foo = bar.baz? ? a : b
foo = (bar && baz) ? a : b
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
EnforcedStyle | `require_no_parentheses` | `require_parentheses`, `require_no_parentheses`, `require_parentheses_when_complex`
AllowSafeAssignment | `true` | Boolean

## Style/TrailingBodyOnClass

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.53 | -

This cop checks for trailing code after the class definition.

### Examples

```ruby
# bad
class Foo; def foo; end
end

# good
class Foo
  def foo; end
end
```

## Style/TrailingBodyOnMethodDefinition

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.52 | -

This cop checks for trailing code after the method definition.

### Examples

```ruby
# bad
def some_method; do_stuff
end

def f(x); b = foo
  b[c: x]
end

# good
def some_method
  do_stuff
end

def f(x)
  b = foo
  b[c: x]
end
```

## Style/TrailingBodyOnModule

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.53 | -

This cop checks for trailing code after the module definition.

### Examples

```ruby
# bad
module Foo extend self
end

# good
module Foo
  extend self
end
```

## Style/TrailingCommaInArguments

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.36 | -

This cop checks for trailing comma in argument lists.

### Examples

#### EnforcedStyleForMultiline: consistent_comma

```ruby
# bad
method(1, 2,)

# good
method(1, 2)

# good
method(
  1, 2,
  3,
)

# good
method(
  1,
  2,
)
```
#### EnforcedStyleForMultiline: comma

```ruby
# bad
method(1, 2,)

# good
method(1, 2)

# good
method(
  1,
  2,
)
```
#### EnforcedStyleForMultiline: no_comma (default)

```ruby
# bad
method(1, 2,)

# good
method(1, 2)

# good
method(
  1,
  2
)
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
EnforcedStyleForMultiline | `no_comma` | `comma`, `consistent_comma`, `no_comma`

### References

* [https://rubystyle.guide#no-trailing-params-comma](https://rubystyle.guide#no-trailing-params-comma)

## Style/TrailingCommaInArrayLiteral

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.53 | -

This cop checks for trailing comma in array literals.

### Examples

#### EnforcedStyleForMultiline: consistent_comma

```ruby
# bad
a = [1, 2,]

# good
a = [
  1, 2,
  3,
]

# good
a = [
  1,
  2,
]
```
#### EnforcedStyleForMultiline: comma

```ruby
# bad
a = [1, 2,]

# good
a = [
  1,
  2,
]
```
#### EnforcedStyleForMultiline: no_comma (default)

```ruby
# bad
a = [1, 2,]

# good
a = [
  1,
  2
]
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
EnforcedStyleForMultiline | `no_comma` | `comma`, `consistent_comma`, `no_comma`

### References

* [https://rubystyle.guide#no-trailing-array-commas](https://rubystyle.guide#no-trailing-array-commas)

## Style/TrailingCommaInHashLiteral

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.53 | -

This cop checks for trailing comma in hash literals.

### Examples

#### EnforcedStyleForMultiline: consistent_comma

```ruby
# bad
a = { foo: 1, bar: 2, }

# good
a = {
  foo: 1, bar: 2,
  qux: 3,
}

# good
a = {
  foo: 1,
  bar: 2,
}
```
#### EnforcedStyleForMultiline: comma

```ruby
# bad
a = { foo: 1, bar: 2, }

# good
a = {
  foo: 1,
  bar: 2,
}
```
#### EnforcedStyleForMultiline: no_comma (default)

```ruby
# bad
a = { foo: 1, bar: 2, }

# good
a = {
  foo: 1,
  bar: 2
}
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
EnforcedStyleForMultiline | `no_comma` | `comma`, `consistent_comma`, `no_comma`

## Style/TrailingMethodEndStatement

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.52 | -

This cop checks for trailing code after the method definition.

### Examples

```ruby
# bad
def some_method
do_stuff; end

def do_this(x)
  baz.map { |b| b.this(x) } end

def foo
  block do
    bar
  end end

# good
def some_method
  do_stuff
end

def do_this(x)
  baz.map { |b| b.this(x) }
end

def foo
  block do
    bar
  end
end
```

## Style/TrailingUnderscoreVariable

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.31 | 0.35

This cop checks for extra underscores in variable assignment.

### Examples

```ruby
# bad
a, b, _ = foo()
a, b, _, = foo()
a, _, _ = foo()
a, _, _, = foo()

# good
a, b, = foo()
a, = foo()
*a, b, _ = foo()
# => We need to know to not include 2 variables in a
a, *b, _ = foo()
# => The correction `a, *b, = foo()` is a syntax error

# good if AllowNamedUnderscoreVariables is true
a, b, _something = foo()
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
AllowNamedUnderscoreVariables | `true` | Boolean

## Style/TrivialAccessors

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.9 | 0.38

This cop looks for trivial reader/writer methods, that could
have been created with the attr_* family of functions automatically.

### Examples

```ruby
# bad
def foo
  @foo
end

def bar=(val)
  @bar = val
end

def self.baz
  @baz
end

# good
attr_reader :foo
attr_writer :bar

class << self
  attr_reader :baz
end
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
ExactNameMatch | `true` | Boolean
AllowPredicates | `true` | Boolean
AllowDSLWriters | `false` | Boolean
IgnoreClassMethods | `false` | Boolean
Whitelist | `to_ary`, `to_a`, `to_c`, `to_enum`, `to_h`, `to_hash`, `to_i`, `to_int`, `to_io`, `to_open`, `to_path`, `to_proc`, `to_r`, `to_regexp`, `to_str`, `to_s`, `to_sym` | Array

### References

* [https://rubystyle.guide#attr_family](https://rubystyle.guide#attr_family)

## Style/UnlessElse

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.9 | -

This cop looks for *unless* expressions with *else* clauses.

### Examples

```ruby
# bad
unless foo_bar.nil?
  # do something...
else
  # do a different thing...
end

# good
if foo_bar.present?
  # do something...
else
  # do a different thing...
end
```

### References

* [https://rubystyle.guide#no-else-with-unless](https://rubystyle.guide#no-else-with-unless)

## Style/UnneededCapitalW

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.21 | 0.24

This cop checks for usage of the %W() syntax when %w() would do.

### Examples

```ruby
# bad
%W(cat dog pig)
%W[door wall floor]

# good
%w/swim run bike/
%w[shirt pants shoes]
%W(apple #{fruit} grape)
```

## Style/UnneededCondition

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.57 | -

This cop checks for unnecessary conditional expressions.

### Examples

```ruby
# bad
a = b ? b : c

# good
a = b || c
```
```ruby
# bad
if b
  b
else
  c
end

# good
b || c

# good
if b
  b
elsif cond
  c
end
```

## Style/UnneededInterpolation

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.36 | -

This cop checks for strings that are just an interpolated expression.

### Examples

```ruby
# bad
"#{@var}"

# good
@var.to_s

# good if @var is already a String
@var
```

## Style/UnneededPercentQ

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.24 | -

This cop checks for usage of the %q/%Q syntax when '' or "" would do.

### Examples

```ruby
# bad
name = %q(Bruce Wayne)
time = %q(8 o'clock)
question = %q("What did you say?")

# good
name = 'Bruce Wayne'
time = "8 o'clock"
question = '"What did you say?"'
```

### References

* [https://rubystyle.guide#percent-q](https://rubystyle.guide#percent-q)

## Style/UnneededSort

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.55 | -

This cop is used to identify instances of sorting and then
taking only the first or last element. The same behavior can
be accomplished without a relatively expensive sort by using
`Enumerable#min` instead of sorting and taking the first
element and `Enumerable#max` instead of sorting and taking the
last element. Similarly, `Enumerable#min_by` and
`Enumerable#max_by` can replace `Enumerable#sort_by` calls
after which only the first or last element is used.

### Examples

```ruby
# bad
[2, 1, 3].sort.first
[2, 1, 3].sort[0]
[2, 1, 3].sort.at(0)
[2, 1, 3].sort.slice(0)

# good
[2, 1, 3].min

# bad
[2, 1, 3].sort.last
[2, 1, 3].sort[-1]
[2, 1, 3].sort.at(-1)
[2, 1, 3].sort.slice(-1)

# good
[2, 1, 3].max

# bad
arr.sort_by(&:foo).first
arr.sort_by(&:foo)[0]
arr.sort_by(&:foo).at(0)
arr.sort_by(&:foo).slice(0)

# good
arr.min_by(&:foo)

# bad
arr.sort_by(&:foo).last
arr.sort_by(&:foo)[-1]
arr.sort_by(&:foo).at(-1)
arr.sort_by(&:foo).slice(-1)

# good
arr.max_by(&:foo)
```

## Style/UnpackFirst

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.54 | -

This cop checks for accessing the first element of `String#unpack`
which can be replaced with the shorter method `unpack1`.

### Examples

```ruby
# bad
'foo'.unpack('h*').first
'foo'.unpack('h*')[0]
'foo'.unpack('h*').slice(0)
'foo'.unpack('h*').at(0)

# good
'foo'.unpack1('h*')
```

## Style/VariableInterpolation

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.9 | 0.20

This cop checks for variable interpolation (like "#@ivar").

### Examples

```ruby
# bad
"His name is #$name"
/check #$pattern/
"Let's go to the #@store"

# good
"His name is #{$name}"
/check #{$pattern}/
"Let's go to the #{@store}"
```

### References

* [https://rubystyle.guide#curlies-interpolate](https://rubystyle.guide#curlies-interpolate)

## Style/WhenThen

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.9 | -

This cop checks for *when;* uses in *case* expressions.

### Examples

```ruby
# bad
case foo
when 1; 'baz'
when 2; 'bar'
end

# good
case foo
when 1 then 'baz'
when 2 then 'bar'
end
```

### References

* [https://rubystyle.guide#one-line-cases](https://rubystyle.guide#one-line-cases)

## Style/WhileUntilDo

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.9 | -

Checks for uses of `do` in multi-line `while/until` statements.

### Examples

```ruby
# bad
while x.any? do
  do_something(x.pop)
end

# good
while x.any?
  do_something(x.pop)
end
```
```ruby
# bad
until x.empty? do
  do_something(x.pop)
end

# good
until x.empty?
  do_something(x.pop)
end
```

### References

* [https://rubystyle.guide#no-multiline-while-do](https://rubystyle.guide#no-multiline-while-do)

## Style/WhileUntilModifier

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.9 | 0.30

Checks for while and until statements that would fit on one line
if written as a modifier while/until. The maximum line length is
configured in the `Metrics/LineLength` cop.

### Examples

```ruby
# bad
while x < 10
  x += 1
end

# good
x += 1 while x < 10
```
```ruby
# bad
until x > 10
  x += 1
end

# good
x += 1 until x > 10
```

### References

* [https://rubystyle.guide#while-as-a-modifier](https://rubystyle.guide#while-as-a-modifier)

## Style/WordArray

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.9 | 0.36

This cop can check for array literals made up of word-like
strings, that are not using the %w() syntax.

Alternatively, it can check for uses of the %w() syntax, in projects
which do not want to include that syntax.

Configuration option: MinSize
If set, arrays with fewer elements than this value will not trigger the
cop. For example, a `MinSize` of `3` will not enforce a style on an
array of 2 or fewer elements.

### Examples

#### EnforcedStyle: percent (default)

```ruby
# good
%w[foo bar baz]

# bad
['foo', 'bar', 'baz']
```
#### EnforcedStyle: brackets

```ruby
# good
['foo', 'bar', 'baz']

# bad
%w[foo bar baz]
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
EnforcedStyle | `percent` | `percent`, `brackets`
MinSize | `2` | Integer
WordRegex | `(?-mix:\A(?:\p{Word}|\p{Word}-\p{Word}|\n|\t)+\z)` | 

### References

* [https://rubystyle.guide#percent-w](https://rubystyle.guide#percent-w)

## Style/YodaCondition

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | Yes | Yes  | 0.49 | 0.63

This cop can either enforce or forbid Yoda conditions,
i.e. comparison operations where the order of expression is reversed.
eg. `5 == x`

### Examples

#### EnforcedStyle: forbid_for_all_comparison_operators (default)

```ruby
# bad
99 == foo
"bar" != foo
42 >= foo
10 < bar

# good
foo == 99
foo == "bar"
foo <= 42
bar > 10
```
#### EnforcedStyle: forbid_for_equality_operators_only

```ruby
# bad
99 == foo
"bar" != foo

# good
99 >= foo
3 < a && a < 5
```
#### EnforcedStyle: require_for_all_comparison_operators

```ruby
# bad
foo == 99
foo == "bar"
foo <= 42
bar > 10

# good
99 == foo
"bar" != foo
42 >= foo
10 < bar
```
#### EnforcedStyle: require_for_equality_operators_only

```ruby
# bad
99 >= foo
3 < a && a < 5

# good
99 == foo
"bar" != foo
```

### Configurable attributes

Name | Default value | Configurable values
--- | --- | ---
EnforcedStyle | `forbid_for_all_comparison_operators` | `forbid_for_all_comparison_operators`, `forbid_for_equality_operators_only`, `require_for_all_comparison_operators`, `require_for_equality_operators_only`

### References

* [https://en.wikipedia.org/wiki/Yoda_conditions](https://en.wikipedia.org/wiki/Yoda_conditions)

## Style/ZeroLengthPredicate

Enabled by default | Safe | Supports autocorrection | VersionAdded | VersionChanged
--- | --- | --- | --- | ---
Enabled | No | Yes  | 0.37 | 0.39

This cop checks for numeric comparisons that can be replaced
by a predicate method, such as receiver.length == 0,
receiver.length > 0, receiver.length != 0,
receiver.length < 1 and receiver.size == 0 that can be
replaced by receiver.empty? and !receiver.empty?.

### Examples

```ruby
# bad
[1, 2, 3].length == 0
0 == "foobar".length
array.length < 1
{a: 1, b: 2}.length != 0
string.length > 0
hash.size > 0

# good
[1, 2, 3].empty?
"foobar".empty?
array.empty?
!{a: 1, b: 2}.empty?
!string.empty?
!hash.empty?
```
