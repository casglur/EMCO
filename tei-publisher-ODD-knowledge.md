ODD Knowlege for use within the ODD Editor in TEI Publisher
=
CSS Operations
-

Use the `Renditions` section to add CSS rules.

Under the **Renditions** section enter the following

Leave `Scope` untouched, then in the empty Renditions box enter: 

```
    font-size: .85em;
    background-color: #C0C0C0;
    border-left: 1px solid black;
    border-right: 1px solid black;
    padding: 0 1em;
```

XPATH operations
-

Adding text in front of a value
--

For example, to add the word 'Page' in front of every page break number (the value of @n), under the **Parameters** section add a new parameter as:

    Parameter Name = Before
    Parameter = 'Page ' || @n
    
** Note that the Parameter value includes quote marks

Formatting a date
--

To format an ISO date within a `<date>` element containg a `when` attribute add the following parameters:

Parameter Name = default
Parameter = .

Parameter Name = alternate
Parameter = format-date(@when, '[FNn], [D1o] [MNn], [Y]')

