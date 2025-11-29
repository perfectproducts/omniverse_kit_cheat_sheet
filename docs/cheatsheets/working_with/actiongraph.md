# ActionGraph

[Isaac Sim Standalone Examples](https://github.com/cpnota/isaacsim_standalone_examples)


## print all graphs and nodes 
[omni.graph.core Functions — Omniverse Kit](https://docs.omniverse.nvidia.com/kit/docs/omni.graph/latest/omni.graph.core.Functions.html)

[GraphController — Omniverse Kit](https://docs.omniverse.nvidia.com/kit/docs/omni.graph/latest/omni.graph.core/omni.graph.core.GraphController.html)

[Graph — Omniverse Kit](https://docs.omniverse.nvidia.com/kit/docs/omni.graph/latest/omni.graph.core/omni.graph.core.Graph.html)

[Node — Omniverse Kit](https://docs.omniverse.nvidia.com/kit/docs/omni.graph/latest/omni.graph.core/omni.graph.core.Node.html)



[Controller Class — kit-omnigraph](https://docs.omniverse.nvidia.com/kit/docs/omni.graph.docs/latest/howto/Controller.html)



```python
import omni.graph.core as og
# make sure we have the og core initialized by doing manual update 
omni.usd.get_context().manual_update(0.1)

# now we should be able to get it 
for graph in og.get_all_graphs():                    # yields og.Graph
	print("Graph:", graph.get_path_to_graph())
	for node in graph.get_nodes():
		print("  Node:", node.get_prim_path(), "Type:", node.get_type_name())
		for attr in node.get_attributes():
			print("   Attr:", attr.get_name())
```



## create variable 

use og.GraphController to create variables 

```python
og.GraphController.create_variable(graph, "myvar", og.Type(og.BaseDataType.FLOAT))
```



## connect variable to node attribute 

og.GraphController.connect()



## get node by path 



## creating a ReadVariable node 

configuring a ReadVariable node is a little tricky ... maybe there's a better way, here's my workaround: 

```python
ctrl = og.GraphController
graph_path = "/Root/MyGraph"
node = ctrl.create_node(f"{graph_path}/V9", "omni.graph.core.ReadVariable")
# get prim for node 
prim = stage.GetPrimAtPath(node.get_prim_path())
# this does not work for me 
#node.get_attribute("inputs:variableName").set("TSP_4_start")
name = "TSP_4_start"
# therefore work on prim attribute level 
# set graph relationship 
custom_relationship: Usd.Relationship = prim.CreateRelationship("inputs:graph")
custom_relationship.SetTargets([graph_path])
# set variable 
prim.CreateAttribute("inputs:variableName", Sdf.ValueTypeNames.String).Set(name)
```
# decouple cyclic behavior wiht CustomEvents 

# run timesample player readtime timeFromStart 

use the timeFromStart output of ReadTime node in order to get reliable behaviour for timesample player.




