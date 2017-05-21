# OsmData  
Une bibliothèque pour charger un fichier .osm (osm xml) dans un objet OsmData pour une manipulation facilitée.

# Attention 

N'utilisez cet outil que pour modifier des fichiers localement. **N'approchez pas les fichiers générés par cette bibliothèque des api de contribution à OpenStreetMap, les informations de modifications ne sont pas générées !**

# Utilisation

`from osmdata import *  
osm = OsmData()  
osm.load_xml_file(in_file.osm)  
for node_id in osm.find_nodes(lambda x: (x.has_tag("amenity"))):  
   t=osm.node(node_id).tags  
   ...  
   if osm.node(node_id).has_tag("amenity"):  
	   osm.node(node_id).set_tag("amenity","parking")  
	   osm.node(node_id).get_tag("amenity")  
	   osm.node(node_id).remove_tag("amenity")  
	   osm.node(node_id).location.move_to(lon,lat)  
   ...  
for way_id in osm.find_ways(lambda x: True):  
   nodes_list=osm.way(way_id).nodes  
   ...  
for member in osm.relations(rel_id).members:  
   id=member.id  
   type=member.ref_type  #"node"/"way"/"relation"  
   role=member.role
osm.save_xml_file(out_file.osm)  
`

Et d'autres bricoles à détailler


# État des lieux

La bibliothèque osmxml_routines.py reste à consolider. La partie OsmData semble relativement stable.