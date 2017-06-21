# OsmData  
Une bibliothèque pour charger un fichier .osm (osm xml) dans un objet OsmData pour une manipulation facilitée.

# Attention 

N'utilisez cet outil que pour modifier des fichiers localement. **N'approchez pas les fichiers générés par cette bibliothèque des api de contribution à OpenStreetMap, les informations de modifications ne sont pas générées !**

# Utilisation

    from osmdata import *  
    osm = OsmData()  
    osm.load_xml_file(in_file.osm)  
    for node in osm.find_nodes(lambda x: (x.has_tag("amenity"))):  
      id=node.id
	  t=node.tags  
      ...  
      if node.has_tag("amenity"):  
 	      value=node.get_tag("amenity")  
          node.set_tag("amenity","parking")  
	      node.remove_tag("amenity")  
	      node.location.move_to(lon,lat)  
      ...  
    for way in osm.find_ways(lambda x: True):  
       nodes_list=way.nodes  
       ...  
    for member in osm.relations(rel_id).members:  
       id=member.id  
       type=member.ref_type  #"node"/"way"/"relation"  
       role=member.role
    osm.save_xml_file(out_file.osm)  


Et d'autres bricoles à détailler


# État des lieux

La bibliothèque osmxml_routines.py reste à consolider. La partie OsmData semble relativement stable.

# Remerciements
Cette bibliothèque reprend en grande partie les dénominations utilisées dans l'API Maperipy de [Maperitive](http://maperitive.net).