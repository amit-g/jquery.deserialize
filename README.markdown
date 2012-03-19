# jquery.deserialize

_Forked from [http://github.com/jakubpawlowicz/jquery.deserialize](http://github.com/jakubpawlowicz/jquery.deserialize)_

This is a very simple jQuery plugin providing 'deserialize' functionality to a form elements. In contrary to some other plugins available it doesn't reinvent the wheel (by utilizing native browser methods) and actually works.

## Basic usage:

    $("#form-id").deserialize(string, options)

## Additional options

### `blankToPlus`

Allows you to override the default setting where it is assumed that the blank is serailized as + instead of %20.
	
	// "one+two" would be deserialized as "one two" (this is default)
	
    $("#form-id").deserialize(string, {
        blankToPlus : true;
    })
	
	// one+two would be deserialized as one+two
	
    $("#form-id").deserialize(string, {
        blankToPlus : false;
    })
	
### `except` and `only`

Allows you to limit set of form fields by either black-listing (except) or white-listing (only):

    $("#form-id").deserialize(string, {
        except : ['generated_token', 'another_field']
    })

These options are exclusive: You cannot pass both in the same time.

### `callback` and `callback_on`

Allows you to pass function, called when certain fields are being populated:

    $("#form-id").deserialize(string,
        callback_on : ['one', 'two', 'three'],
        callback : function(name, value){
            # NOTE: works only in Firefox with Firebug installed
            console.log(name + " has been populated by " + value)
        }
    })

You can leave `callback_on` black to call given function on every populated field.

### `attribute`

Allows you to change default attribute (`name`), which will be used to match fields in this way: `[name='value']`.

_See `demo.html` for some examples._

## TODO:

 * allow to pass JSON objects as data for deserialization
 * `except`, `only` and `callback_on` options should accept regular expressions
 * add more examples to reflect all possible options
 * add possibility to chage the way the fields are matched

