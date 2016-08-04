How it works
------------

Triggering an [event](/docs/event.md "wikilink") on an [element](/element.md "wikilink"), also triggers the event on its parents (up the [element tree](/element_tree.md "wikilink")) and its children (down the [element tree](/element_tree.md "wikilink"))

<table>
<tbody>
<tr class="odd">
<td><p><strong>Example</strong></p></td>
<td></td>
<td><p><strong>Handlers which will get triggered</strong></p></td>
</tr>
<tr class="even">
<td><p>triggerEvent( “eventName”, root)</p></td>
<td><p><a href="/Image:Event_source_root.png.md" title="wikilink">Image:Event_source_root.png</a></p></td>
<td><p>addEventHandler( “eventName”, root )<br />
addEventHandler( “eventName”, resourceRoot ) <strong>*In any resource*</strong><br />
addEventHandler( “eventName”, anyPlayerElement )<br />
addEventHandler( “eventName”, anyVehicleElement )<br />
<strong>source is root</strong><br />
</p></td>
</tr>
<tr class="odd">
<td><p>triggerEvent( “eventName”, myPlayerElement )</p></td>
<td><p><a href="/Image:Event_source_player.png.md" title="wikilink">Image:Event_source_player.png</a></p></td>
<td><p>addEventHandler( “eventName”, root )<br />
addEventHandler( “eventName”, myPlayerElement )<br />
<strong>source is myPlayerElement</strong></p></td>
</tr>
<tr class="even">
<td><p>triggerEvent( “eventName”, resourceRoot)</p></td>
<td><p><a href="/Image:Event_source_resource.png.md" title="wikilink">Image:Event_source_resource.png</a></p></td>
<td><p>addEventHandler( “eventName”, root )<br />
addEventHandler( “eventName”, resourceRoot ) <strong>*Only in same resource*</strong><br />
addEventHandler( “eventName”, aVehicleElement )<br />
<strong>source is resourceRoot of the calling resource</strong><br />
</p></td>
</tr>
<tr class="odd">
<td><p>triggerEvent( “eventName”, myVehicleElement)</p></td>
<td><p><a href="/Image:Event_source_mapelement.png.md" title="wikilink">Image:Event_source_mapelement.png</a></p></td>
<td><p>addEventHandler( “eventName”, root )<br />
addEventHandler( “eventName”, resourceRoot ) <strong>*Only in resource vehicle was created in*</strong><br />
addEventHandler( “eventName”, myVehicleElement )<br />
<strong>source is myVehicleElement</strong><br />
</p></td>
</tr>
</tbody>
</table>
