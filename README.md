#Indonesia TopoJSON File

This file just include data for Indonesia provinces and places. 

##GeoJSON files

Generate `subunit.json` map file. This command will include Malaysia, Brunei, Singapore and Papua New Guinea maps. For smaller file size just remove **MYS**, **BRN**, **SGP** and **PNG** options.

    $ ogr2ogr -f GeoJSON -where "ADM0_A3 IN ('IDN','MYS','BRN','SGP', 'PNG')" subunits.json maps/ne_10m_admin_0_map_subunits.shp 

Generate `states_provinces.json` map file

    $ ogr2ogr -f GeoJSON -where "ISO_A2 = 'ID'" states_provinces.json  maps/ne_10m_admin_1_states_provinces.shp


Generate `places.json` map file
 
    $ ogr2ogr -f GeoJSON -where "ISO_A2 = 'ID' AND SCALERANK < 8" places.json maps/ne_10m_populated_places.shp 


##TopoJSON file

Generate topojson `indonesia.json` file

    $ topojson -o indonesia.json --id-property SU_A3 --properties -- subunits.json states_provinces.json places.json


##Demo

[http://bl.ocks.org/junwatu/ac08d962f07d770aba99](http://bl.ocks.org/junwatu/ac08d962f07d770aba99)

---

The MIT License (MIT)

Copyright (c) 2015 Equan Pr.

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
