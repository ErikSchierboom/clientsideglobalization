# Client-side globalization

A small demo application that shows how to do client-side globalization using the [Globalize JavaScript library](https://github.com/jquery/globalize). The library itself is a small library without any dependencies and it makes globalization very easy:

    // First we set the global culture
    Globalize.culture("fr");

    // Then you can do culture-specific formatting
    Globalize.format(new Date(2012, 1, 20), 'D')  // Outputs "lundi 20 février 2012"

To be able to do this, you need to add both the globalize library and the globalizations themselves to your page:

    <script type="text/javascript" src="Scripts/globalize.js"></script>
    <script type="text/javascript" src="Scripts/globalize.cultures.js"></script>

If you don't want to load all cultures, you can also only include the cultures you support:

    <script type="text/javascript" src="Scripts/globalize.js"></script>
    <script type="text/javascript" src="Scripts/globalize.culture.en-US.js"></script>    
    <script type="text/javascript" src="Scripts/globalize.culture.fr.js"></script>

## Implementation

This project serves as an example of how easy it is to do client-side globalization. The project itself contains of a single HTML page which shows some globalized examples for every culture supported by the Globalize library. 

The code to render the culture-specific examples is as follows:

    function createExamplesForCultureAsHtml(culture) {
        return '<tr>' +
                    '<td>' + culture.name + '</td>' +
                    '<td>' + culture.nativeName + '</td>' +
                    '<td>' + Globalize.format(new Date(2012, 1, 20), 'D', culture) + '</td>' +             // date example
                    '<td>' + Globalize.format(new Date(2012, 1, 20, 9, 15, 50), 'F', culture) + '</td>' +  // datetime example
                    '<td>' + Globalize.format(123456789, 'n', culture) + '</td>' +                         // large number example
                    '<td>' + Globalize.format(12.34, 'n', culture) + '</td>' +                             // floating-point number example
                    '<td>' + Globalize.format(1234.56, 'c', culture) + '</td>' +                           // currency example
                '</tr>';
    }

We call this code for every cultures that has been loaded (and that means _all_ cultures as we include the [**globalize.cultures.js**](Scripts/globalize.cultures.js) file):

    // For each culture, create the HTML for its examples and add it to the already created HTML examples
    $.each(Globalize.cultures, function (_, culture) {
        examplesAsHtml += createExamplesForCultureAsHtml(culture);
    });

Finally, we render the examples to the screen.

## License
[Apache License 2.0](LICENSE.md)