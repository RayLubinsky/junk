<!-- lib/doc/tips.md -->

# Implementation Tips                                        <a name="top"></a>

  A collection of tips for some of the finer points of Ruby.

  [Optional arguments]    (#optional_arguments) <br/>
  [Hash option arguments] (#hash_options)       <br/>
  [Variable arguments]    (#variable_arguments) <br/>

## Optional arguments                         <a name="optional_arguments"></a>

  Method arguments may be provided a default value in the method definition;
  the caller of the method may choose to provide a value for that argument or
  not.

  Generally, optional arguments should follow any required arguments, although
  it appears that the set of optional arguments it can be placed anywhere among
  as long as (a) they stay together and (b) the first argument is a required
  argument.

  The following are valid:

```
  def method( req1,     req2,     req3,     opt1=nil, opt2=nil, opt3=nil  ) end
  def method( req1,     req2,     opt1=nil, opt2=nil, opt3=nil, req3      ) end
  def method( req1,     opt1=nil, opt2=nil, opt3=nil, req2,     req3      ) end
```

  But the following are not:

```
  def method( opt1=nil, opt2=nil, opt3=nil, req1,     req2,     req3      ) end
  def method( opt1=nil, req1,     req2,     req3,     opt2=nil, opt3=nil  ) end
  def method( req1,     opt1=nil, req2,     req3,     opt2=nil, opt3=nil  ) end
  def method( req1,     req2,     opt1=nil, req3,     opt2=nil, opt3=nil  ) end
  def method( req1,     opt1=nil, req2,     opt2=nil, req3,     opt3=nil  ) end
```

  At the point where the method is called, the arguments that are passed into
  the method are processed from left-to-right, first filling in all of the
  required arguments, then filling in optional arguments (regardless of where
  they show up in the method definition).

  Of the valid examples, the first would be the preferred way of defining the
  method because that is the order that arguments would be assigned when the
  method was executed.

  [Back to top](#top)

## Hash option arguments                            <a name="hash_options"></a>

  TODO

  [Back to top](#top)

## Variable arguments                         <a name="variable_arguments"></a>

  To define a method with a variable number of arguments, use a parameter whose
  name is prefixed with "\*"; a typical choice is "\*args".  For example:
  <br/><br/>

```
  def method(*args)
    args                                        # The argument list treated as an array
    args.count                                  # The number of arguments passed into the method
    args.each { |arg| do_something_with(arg) }  # Process each argument
    do_something_with(*args)                    # Pass the variable argument list to another method
    do_something_with(args)                     # Pass the arguments as an Array to another method
  end
```

  Because "\*args" allows any number of arguments, any of the following would
  be a valid call to "method":
  <br/><br/>

| Usage                                   | args.count  | args[0].class |
| --------------------------------------- |:-----------:| ------------- |
| method                                  | 0           | nil           |
| method(nil)                             | 1           | NilClass      |
| method('hello')                         | 1           | String        |
| method(1)                               | 1           | Fixnum        |
| method(1, 2, 3)                         | 3           | Fixnum        |
| method([1, 2, 3])                       | 1           | Array         |
| method({})                              | 1           | Hash          |
| method(:a => val1)                      | 1           | Hash          |
| method(:a => val1, :b => val2)          | 1           | Hash          |
| method({ :a => val1, :b => val2 })      | 1           | Hash          |
| method('hello', :a => val1, :b => val2) | 2           | String        |

  [Back to top](#top)
