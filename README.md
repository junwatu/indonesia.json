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

