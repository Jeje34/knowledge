# String

## contains()

    public boolean contains(CharSequence substring) {
        return indexOf(s.toString()) > -1;
    }

- contains() searches a substring in the given string. It returns true if substring are found in this string otherwise returns false.
- case sensitive
- does not accept 'null' argument : it will throw NullPointerException

## intern()