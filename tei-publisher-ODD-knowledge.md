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

Predicates
-
You can specify when a rule will be applied to an element using the Predicate text box. For example, if you have an `ab` element and you only want a rule to apply when the ancestor element is a `div` with the `type` attribute `translation` **or** the webcomponent `view` has a value of `normalized` and the `ab` element has a `rend` attribute value of `indent` then enter the following into the box

    (ancestor::div[@type='translation'] or $parameters?view='normalized') and @rend='indent'

XPATH operations
-

Adding text in front of a value
--

For example, to add the word 'Page' in front of every page break number (the value of @n), under the **Parameters** section add a new parameter as:

    Parameter Name: Before
    Parameter: 'Page ' || @n
    
** Note that the Parameter value includes quote marks

Adding an attribute to every instance of an element
--

E.g. to add a `label` attribute to every instance of an anchor element (n.b. this works with the `Note` behaviour)

    Parameter Name: label
    Parameter: @n/string()

    Parameter Name: content    
    Parameter: let $n := @n return $get(.)/ancestor::TEI//div[@type='notes']//note[@n=$n]/node()
    
    

Formatting a date
--

To format an ISO date within a `<date>` element containg a `when` attribute add the following parameters:

    Parameter Name: default
    Parameter: .

    Parameter Name: alternate
    Parameter: format-date(@when, '[FNn], [D1o] [MNn], [Y]')

