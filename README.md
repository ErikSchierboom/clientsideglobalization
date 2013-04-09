Client-side globalization
===================

A small demo application that shows how to do client-side globalization using the [Globalize JavaScript library](https://github.com/jquery/globalize). The library itself is a small library without any dependencies and it makes globalization very easy:

    // First we set the global culture
    Globalize.culture("fr");

    // Then you can do culture-specific formatting
    Globalize.format(new Date(2012, 1, 20), 'D')  // Outputs "lundi 20 février 2012"

This project serves as an example of how easy it is to do client-side globalization. The project itself contains of a single HTML page which shows some globalized examples for every culture supported by the Globalize library.