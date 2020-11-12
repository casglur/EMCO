# How to clean and format XML from project staff prior to loading into tei-publisher

Move notes
-
Move notes from within `<div type="textualNotes">` element and replace the corresponding `<ref target="n1782.1"><hi rend="sup">1</hi></ref>` elements with the note content. 

So if the source contains

    <div type="textualNotes">
        <note n="1" xml:id="n1782.1">
            <ab>
                <persName ref="emco-person-2">Dr</persName> and <persName ref="emco-person-211">M<hi rend="sup">rs</hi> 
                Beattie</persName> visited...
    
Next, move this up into the <body> area to where the note is being referenced, e.g. <ref target="n1782.1"><hi rend="sup">1</hi></ref>, and replace the reference with the note content    

Finally delete the <div type="textualNotes">` section once it is empty
    
Create Facsimile section and find and replace `<pb...` element attribute values and populate facsimile section values
-

1. Create a Facsimile section in between `<teiHeader>` and `<text>` sections

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

1. 


