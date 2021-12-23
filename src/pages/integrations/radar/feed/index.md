---
title: Feed
---

[Radar](https://radar.com) is the leading geofencing and location tracking platform. You can use Radar SDKs and APIs to build a wide range of location-based product and service experiences, including pickup and delivery tracking, location-triggered notifications, location verification, store locators, address autocomplete, and more.
## Enable the Integration

You will need to set up a separate feed for each Platform you want to use Radar data for. For example, if you have iOS and Android platforms, you need to create two feeds. For the first, set the `Act as Application` field to `iOS` and for the second, set it to `Android`. For each feed, you will receive an API Key and Secret. Enter these credentials on the Radar Integrations page.

For more details, see the [Radar mParticle Feed documentation](https://radar.com/documentation/integrations#event-integrations-mparticle-feed).

## Input Data Details

Users in the Radar Feed are identified by Customer ID, Android ID or IDFV.

The Radar Feed sends custom events, with an event type of 'location', that track the movement of a user. It also sends user attributes relating to the user's last known location.

###Events
For a complete view of the events that Radar passes into mParticle, visit [Radar's mParticle Events Mapping documentation] (https://radar.com/documentation/integrations/mparticle#event-mapping)

All events include the following attributes:

  * `event_id`  
  * `location`  
  * `timestamp_unix_ms`  

### Radar Events & Custom Attributes
  * `user.entered_geofence`
    * `geofence_id`
    * `geofence_description`
    * `geofence_tag`
    * `geofence_external_id`
    * `confidence`
    
  * `user.exited_geofence`
    * `geofence_id`
    * `geofence_description`
    * `geofence_tag`
    * `geofence_external_id`
    * `confidence`
    * `duration`
  
The following events are sent only if 'Places' is enabled in Radar:

  * `user.entered_place`
    * `place_id`
    * `place_name`
    * `place_chain_name`
    * `place_chain_slug`
    * `place_facebook_id`
    * `place_categories`
    * `confidence`
    
  * `user.exited_place`
    * `place_id`
    * `place_name`
    * `place_chain_name`
    * `place_chain_slug`
    * `place_facebook_id`
    * `place_categories`
    * `confidence`
    * `duration`

The following events are sent only if 'Regions' is enabled in Radar:

  * `user.entered_region_country`
    * `region_code`
    * `region_name`
    * `confidence`
 
  * `user.exited_region_country`
    * `region_code`
    * `region_name`
    * `confidence`

  * `user.entered_region_state`
    * `region_code`
    * `region_name`
    * `confidence`
 
  * `user.exited_region_state`
    * `region_code`
    * `region_name`
    * `confidence`

  * `user.entered_region_dma`
    * `region_code`
    * `region_name`
    * `confidence`
 
  * `user.exited_region_dma`
    * `region_code`
    * `region_name`
    * `confidence`

The following events are sent only if 'Trip Tracking' is enabled in Radar:

  * `user.started_trip`
    * `trip_external_id`
    * `trip_metadata_{key}`
    * `trip_destination_geofence_tag`
    * `trip_destination_geofence_external_id`
 
  * `user.updated_trip`
    * `trip_external_id`
    * `trip_metadata_{key}`
    * `trip_destination_geofence_tag`
    * `trip_destination_geofence_external_id`

  * `user.approaching_trip_destination`
    * `trip_external_id`
    * `trip_metadata_{key}`
    * `trip_destination_geofence_tag`
    * `trip_destination_geofence_external_id`
 
  * `user.arrived_at_trip_destination`
    * `trip_external_id`
    * `trip_metadata_{key}`
    * `trip_destination_geofence_tag`
    * `trip_destination_geofence_external_id`

  * `user.stopped_trip`
    * `trip_external_id`
    * `trip_metadata_{key}`
    * `trip_destination_geofence_tag`
    * `trip_destination_geofence_external_id`


### User Attributes

For a complete view of the user attributes that Radar passes into mParticle, visit [Radar's mParticle User Mapping documentation] (https://radar.com/documentation/integrations/mparticle#user-mapping)

With each batch, Radar will update the following user attributes according to the user's last known location

  * `radar_id` - the radar ID of the user
  * `radar_location_latitude`
  * `radar_location_longitude`
  
The following four user attributes provide details for an array of geofences the user's last known location was in. All four arrays are in the same order so, for example, `radar_geofence_ids[2]` and `radar_geofence_descriptions[2]` refer to the same geofence.

  * `radar_geofence_ids`  
  * `radar_geofence_descriptions`  
  * `radar_geofence_tags`  
  * `radar_geofence_external_ids`  

If 'Places' is enabled the following attributes are sent for any Place associated with the user's last known location:

  * `radar_place_id`  
  * `radar_place_name`  
  * `radar_place_chain_name`  
  * `radar_place_chain_slug`  
  * `radar_place_facebook_id`    
  * `radar_place_categories`    
