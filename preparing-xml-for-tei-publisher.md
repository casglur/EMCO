# How to clean and format XML from project staff prior to loading into tei-publisher

## Move notes

Move notes from within `<div type="textualNotes">` element and replace the corresponding `<ref target="n1782.1"><hi rend="sup">1</hi></ref>` elements with the note content. 

So if the source contains

    <div type="textualNotes">
        <note n="1" xml:id="n1782.1">
            <ab>
                <persName ref="emco-person-2">Dr</persName> and <persName ref="emco-person-211">M<hi rend="sup">rs</hi> 
                Beattie</persName> visited...
    
Next, move this up into the <body> area to where the note is being referenced, e.g. <ref target="n1782.1"><hi rend="sup">1</hi></ref>, and replace the reference with the note content    

Finally delete the <div type="textualNotes">` section once it is empty
    
## Create Facsimile section and find and replace `<pb...` element attribute values and populate facsimile section values

### Create a **facsimile** section in between `<teiHeader>` and `<text>` sections

    <facsimile xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
        <surface n="" xml:id="surf-pb">
            <graphic mimeType="image/jpeg" url="MS 551.1.1.jpg" height="50px" rend="thumbnail"/>
            <zone xml:id="zone-pb-1">
                <graphic mimeType="image/jpeg" url="MS 551.1.1.jpg" height="50px" rend="thumbnail"/>
                <graphic mimeType="image/png" url="MS 551.1.1.png" width="380px" rend="facstab"/>
            </zone>
            ...
        </surface>
    </facsimile>

### Find and replace `<pb>` element values between `<body>` and `<facsimile>` sections

If `<pb>` element in `<body>` section contains the following:

    <pb facs="MS 30_2_65_p01.jpg"/>
    
Then corresponding `<graphic>` and `<zone>` elements must be created and the IDs from these elements replace the attribute values in the `<pb>` element within the `<body>` section, i.e.

#### `<body>` section is...

    <pb facs="MS 30_2_65_p01.jpg"/>

#### `<facsimile>` section requires...

    <facsimile xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
        <surface n="" xml:id="surf-pb">
            <graphic mimeType="image/jpeg" url="MS 30_2_65_p01.jpg" height="50px" rend="thumbnail"/> <!-- This should be set to the first page of the correspondence -->
            <zone xml:id="zone-pb-1">
                <graphic mimeType="image/jpeg" url="MS 30_2_65_p01.jpg" height="50px" rend="thumbnail"/>
                <graphic mimeType="image/jpg" url="MS 30_2_65_p01.jpg" width="380px" rend="facstab"/>
            </zone>
            ...
        </surface>
    </facsimile>

#### `<body>` section gets updated to ...

    <pb n="1" xml:id="pb-orig-1" facs="#zone-pb-1"/>

This process repeats for every `<pb>` element within the `<body>` section

## URLs - Undo URL encoding and find and replace `&` `"` symbols with `&amp;` and `&quot;`

1. Find all instances of URLs that have been URL encoded, e.g. ones that begin


    https%3A%2F%2Fbooks.google.co.uk%2F
    
     
1. Copy and paste the URL into the decoder at: https://meyerweb.com/eric/tools/dencoder/ and press the **decode** button

1. Copy and paste the decoded URL into a text editor and find and replace any `&` characters in the URL with `&amp;` symbol, and any `"` symbols with `&quot;`

# Inline bibliographic references

Inline bibiliographic references should use the `<ref>` element as follows

    <ref target="emco-bibl-22" type="editorial"><hi rend="italic">Companions Without Vows: Relationships among Eighteenth- Century British Women</hi></ref>
   
The `type` attribute can be either `editorial` or `historical` the difference being, an editorial reference is a text we used in editing the letters, whereas a historical reference is a work that Montagu read.
