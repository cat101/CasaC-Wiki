* The dispatchers on the master node are invoked only if they are enabled and they receive any event that matches a zone mask
* One event may match multiple masks and therefore be received by a dispatcher multiple times
** This never happens because switches only belong to HouseAutomation24HsMask and sensors are partitioned among the alarm zones (they only belong to one zone)
* The HouseAutomation24Hs zone get automatically generated to trigger when switches that require global coordination at the master level need attention. 
** The global automatisms get handled on the houseAutomationDispatcher using the LIST_OF_GLOBAL_ACTIONS block
** The HouseAutomation24HsMask only contains switches and the other masks used by the alarm logic contain sensors. Internally the master fires local events using the HouseAutomation24Hs mask (e.g. EV_SUN_ENERGY_UP, EV_MAINSOK)
** Note that switches won't trigger any events except for the ones used in hose wide automatisms