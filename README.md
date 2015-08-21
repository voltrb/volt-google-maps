# Google Maps Volt Component

(still a work in progress)

Provides a simple google maps integration.

First signup for a google maps api key here:

https://developers.google.com/maps/documentation/javascript/tutorial

Next put it in your config/app.rb file:

    config.public.google_maps_api_key = '....'

Add this line to your application's Gemfile:

    gem 'volt-google_maps'

And then execute:

    bundle

Then install the component in the config/dependencies.rb file of any components you want google maps in:

    component 'google_maps'

Lastly, use the google_maps tag:

    <style>
      .google-map {
        height: 400px;
        width: 600px;
      }
    </style>
    <div class="google-map">
      <:google_maps />
    </div>

The map will take up the width of the div, so we add the style tag.

The google_map tag can be passed many attributes:

- zoom - integer for different zoom levels
- center - the address to center the map on
- markers - an array of marker Models  (with _address and _content) or address strings

So component call signature for your views is next:
```xml
<:google_maps center="{{ page._address }}" zoom="{{ page._zoom }}" markers="{{ page._markers }}" />
```

Marker Model can be created in your controller like this
```ruby
page._markers.create({address: 'San Francisco', content: 'Hello World'})
```
