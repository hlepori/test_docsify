# Encoding a Route/Trajectory

## Encoding an FF-ICE Basic Route in FIXM

| **#** | **Business Rule desription** | **Applies to**<br>**FIXM model element** |
|:-|:-|:-|
| ffice_basic_rte_1 | An FF-ICE basic route ***shall*** include a series of `<fx:element>` in the order in which they will be flown. | `<fx:desired>` `<fx:filed>` `<fx:ranked>` |
| ffice_basic_rte_2 | Each `<fx:element>` of an FF-ICE basic route ***shall*** correspond to a point and route element that would be present in an FPL field 15c. | `<fx:element>` |
| ffice_basic_rte_3 | The first `<fx:element>` of an FF-ICE basic route ***shall*** include the `<fx:elementStartPoint>` with an `<fb:aerodromeReferencePoint>` capturing the reference to the departure aerodrome, with *optionally* its geographical location expressed as `<fb:referencePoint>`.<br><br> *Do NOT apply to air filed flight plan* | `<fx:element>` |
| ffice_basic_rte_4 | The first `<fx:element>` of an FF-ICE basic route ***shall*** include the `<fx:routeDesignatorToNextElement>` with either an `<fx:standardInstrumentDeparture>` capturing the reference to the SID to be flown, or an `<fx:otherRouteDesignator>` indicating a `DIRECT` route.<br><br> *Do NOT apply to air filed flight plan* | `<fx:element>` |
| ffice_basic_rte_5 | The first `<fx:element>` of an FF-ICE basic route ***shall*** include the `seqNum` set to `0`, indicating that this is the first `<fx:element>` of the basic route. | `<fx:element>` |
| ffice_basic_rte_6 | Each subsequent `<fx:element>` (except the last one) of an FF-ICE basic route ***shall*** include the `<fx:elementStartPoint>` capturing the reference to the significant point in the route, with optionally its geographical location expressed as `<fb:referencePoint>` (for aerodromes only) or as `<fb:position>`. | `<fx:element>` |
| ffice_basic_rte_7 | Each subsequent `<fx:element>` (except the last one) of an FF-ICE basic route ***shall*** include the `<fx:routeDesignatorToNextElement>` with an `<fx:standardInstrumentDeparture>`, `<fx:routeDesignator>` or `<fx:standardInstrumentArrival>` capturing the reference to the ATS route (SID, Enroute ATS Route or STAR) the flight will be on after crossing the `<fx:elementStartPoint>`, or an `<fx:otherRouteDesignator>` indicating either a `DIRECT` route or an `UNSPECIFIED` following a delay point. | `<fx:element>` |
| ffice_basic_rte_8 | Each subsequent `<fx:element>` (except the last one) of an FF-ICE basic route ***shall*** include the `seqNum` incremented as appropriate to reflect the order of the `<fx:element>` in the basic route.| `<fx:element>` |
| ffice_basic_rte_9 | The last `<fx:element>` of an FF-ICE basic route ***shall*** include the `<fx:elementStartPoint>` with an `<fb:aerodromeReferencePoint>` capturing the reference to the destination aerodrome, with *optionally* its geographical location expressed as `<fb:referencePoint>`. | `<fx:element>` |
| ffice_basic_rte_10 | The last `<fx:element>` of an FF-ICE basic route ***shall*** include the `seqNum` incremented as appropriate to reflect the order of the `<fx:element>` in the basic route. | `<fx:element>` |
| ffice_basic_rte_11 | The last `<fx:element>` of an FF-ICE basic route *shall not* contain a `<fx:routeDesignatorToNextElement>`.| `<fx:element>` |
| | | |
| | | |
| | | |
| | | |


## Encoding an FF-ICE Expanded Route in FIXM

| **#** | **Encoding Rule** | **Applies to** |
|:-|:-|:-|
| ffice_exp_rte_1 | An FF-ICE Expanded Route ***shall*** include a series of `<fx:element>` included in the order in which they will be flown. | `<fx:desired>` `<fx:filed>` `<fx:ranked>` |
| ffice_exp_rte_2 | The first `<fx:element>` of an FF-ICE expanded route ***shall*** include the `<fx:elementStartPoint>` with an `<fb:aerodromeReferencePoint>` capturing the reference to the departure aerodrome with its geographical location expressed as `<fb:referencePoint>`.| `<fx:element>` |
| ffice_exp_rte_3 | The first `<fx:element>` of an FF-ICE expanded route ***shall*** include the `<fx:routeDesignatorToNextElement>` with either an `<fx:standardInstrumentDeparture>` capturing the reference to the SID to be flown, or an `<fx:otherRouteDesignator>` indicating a `DIRECT` route. | `<fx:element>` |
| ffice_exp_rte_4 | The first `<fx:element>` of an FF-ICE expanded route ***shall*** include the `seqNum` set to 0, indicating that this is the first `<fx:element>` of the expanded route. | `<fx:element>` |
| ffice_exp_rte_5 | Each subsequent `<fx:element>` (except the last one) of an FF-ICE expanded route ***shall*** include the `<fx:elementStartPoint>` capturing the reference to the next significant point in the route, with its geographical location expressed as `<fb:referencePoint>` (for aerodromes only) or as `<fb:position>`. This applies even if it is a point being traversed on the same ATS route, SID, or STAR as the previous `<fx:element>`. | `<fx:element>` |
| ffice_exp_rte_6 | Each subsequent `<fx:element>` (except the last one) of an FF-ICE expanded route ***shall*** include the `<fx:routeDesignatorToNextElement>` with an `<fx:standardInstrumentDeparture>`,`<fx:routeDesignator>` or `<fx:standardInstrumentArrival>` capturing the reference to the ATS route (SID, Enroute ATS Route or STAR) the flight will be on after crossing the `<fx:elementStartPoint>`, or an `<fx:otherRouteDesignator>` indicating either a `DIRECT` route or an `UNSPECIFIED` following a delay point. <br><br>*Note: in an expanded route, there may be a number of sequential `<fx:element>` all with the same `<fx:routeDesignatorToNextElement>`*;  | `<fx:element>` |
| ffice_exp_rte_7 | Each subsequent `<fx:element>` (except the last one) onf an FF-ICE expanded route ***shall*** include the `<fx:alongRouteDistance>` of the `<fx:elementStartPoint>`.| `<fx:element>` |
| ffice_exp_rte_8 | Each subsequent `<fx:element>` (except the last one) of an FF-ICE expanded route ***shall*** include the `seqNum` incremented as appropriate to reflect the order of the `<fx:element>` in the expanded route. | `<fx:element>` |
| ffice_exp_rte_9 | The last `<fx:element>` of an FF-ICE expanded route ***shall*** contain the `<fx:elementStartPoint>` with an `<fb:aerodromeReferencePoint>` capturing the reference to the destination aerodrome with its geographical location expressed as `<fb:referencePoint>`;| `<fx:element>` |
| ffice_exp_rte_10 | The last `<fx:element>` of an FF-ICE expanded route ***shall*** contain the `<fx:alongRouteDistance>` of the `<fx:elementStartPoint>`.| `<fx:element>` |
| ffice_exp_rte_11 | The last `<fx:element>` of an FF-ICE expanded route ***shall*** contain the `seqNum` incremented as appropriate to reflect the order of the `<fx:element>` in the expanded route.| `<fx:element>` |
| ffice_exp_rte_12 | The last `<fx:element>` of an FF-ICE expanded route ***shall*** contain *shall not* contain a `<fx:routeDesignatorToNextElement>`.| `<fx:element>` |
| | | |
| | | |
| | | |
| | | |




## Encoding an FF-ICE Trajectory in FIXM

| **#** | **Encoding Rule** | **Applies to** |
|:-|:-|:-|
| ffice_traj_1 | An `<fx:element>` having a `<fx:point4d>` with no associated `<fx:elementStartPoint>` ***shall*** still show an `<fx:alongRouteDistance>`. This ***shall*** be the projection of the `<fx:point4d>` `<fx:position>` onto the relevant route segment. This projection ***should*** be perpendicular to the trajectory. | `<fx:element>` |
| | | |
| | | |
| | | |

