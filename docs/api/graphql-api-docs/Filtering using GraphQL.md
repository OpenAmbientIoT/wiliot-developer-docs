Schema Documentation
====================

Location
--------

The location schema is used for filtering assets based on their location data. It can be used in combination with other filters, such as temperature or connectivity, to build complex queries. The location filter has three types: state, latest, and transition.

### State

The state filter retrieves assets that were located in a specific location according to the location metric, with an optional condition on the continuous duration they stayed there.

Example:

jsonCopy code

`location: {
state: {
locationValue: {equalTo: "l1"},
zoneValue: {includedIn: ["z1", "z2"]},
continuousDuration: {greaterThan: 60000} // in milliseconds
}
}`

### Latest

The latest filter is similar to the state filter but refers only to the last state in the provided timeframe.

Example:

jsonCopy code

`location: {
latest: {
locationValue: {equalTo: "l1"},
zoneValue: {includedIn: ["z1", "z2"]},
continuousDuration: {greaterThan: 60000} // in milliseconds
}
}`

### Transition

The transition filter retrieves assets that had a state change from a value to a value in the specified timeframe. You can specify either from or to, or both.

Example:

jsonCopy code

`location: {
transition: {
from: {
locationValue: {includedIn: ["l1"]},
zoneValue: {notIncludedIn: ["z1", "z2"]}
},
to: {
locationValue: {equalTo: "l1"}
},
orderIndex: 2
}
}`

Zone
----

Zones are areas within locations that can be used to further filter assets. Zones can be used with location filters to filter assets based on their zone information.

Example:

jsonCopy code

`location: {
state: {
locationValue: {equalTo: "l1"},
zoneValue: {includedIn: ["z1", "z2"]},
continuousDuration: {greaterThan: 60000} // in milliseconds
}
}`

Asset
-----

Assets represent individual items or devices that can be filtered and aggregated using the API. The asset schema includes fields like location, temperature, category, and more.

Example:

jsonCopy code

`assetFilter(
timeFrame: {greaterThan: 1675025670, lessThan: 1675125670},
accumulativeDuration: {greaterThan: 7200000},
location: {
state: {
locationValue: {includedIn: ["l1", "l2"]},
continuousDuration: {greaterThan: 3600000}
}
},
temperature: {
value: {greaterThan: 25}
}
) {...}`

Category
--------

Categories can be used to group assets based on their properties or function. The category filter can be used to filter assets that belong to specific categories.

Example:

jsonCopy code

`assetFilter(
timeFrame: {greaterThan: 1675025670, lessThan: 1675125670},
category: {id: {startsWith: "id"}},
nameFilter: {equalTo: "name"}
) {...}`

Examples
========

Example 1: Filter assets based on location and zone
---------------------------------------------------

Retrieve assets that were located in location "l1" and in zones "z1" or "z2" with a continuous duration greater than 60000 milliseconds.

jsonCopy code

`assetFilter(
timeFrame: {greaterThan: 1675025670, lessThan: 1675125670},
location: {
state: {
locationValue: {equalTo: "l1"},
zoneValue: {includedIn: ["z1", "z2"]},
continuousDuration: {greaterThan: 60000} // in milliseconds
}
}
) {
id
name
location {
id
name
}
}`

## Example 2: Filter assets based on location transitions

Retrieve assets that had a location transition from "l1" (not in zones "z1" or "z2") to "l1" (zones "z1" or "z2") in the specified time frame.

```json
assetFilter(
  timeFrame: {greaterThan: 1675025670, lessThan: 1675125670},
  location: {
    transition: {
      from: {
        locationValue: {includedIn: ["l1"]},
        zoneValue: {notIncludedIn: ["z1", "z2"]}
      },
      to: {
        locationValue: {equalTo: "l1"},
        zoneValue: {includedIn: ["z1", "z2"]}
      },
      orderIndex: 2
    }
  }
) {
  id
  name
  location {
    id
    name
  }
}
```

Example 3: Filter assets based on category and temperature
----------------------------------------------------------

Retrieve assets that belong to categories with an ID starting with "id" and have a temperature value less than 20.

jsonCopy code

`assetFilter(
  timeFrame: {greaterThan: 1675025670, lessThan: 1675125670},
  category: {id: {startsWith: "id"}},
  temperature: {
    value: {lessThan: 20}
  }
) {
  id
  name
  category {
    id
    name
  }
}`

Example 4: Filter assets based on the latest location and zone
--------------------------------------------------------------

Retrieve assets that are currently in location "l1" and in zones "z1" or "z2" with a continuous duration greater than 30000 milliseconds.

jsonCopy code

`assetFilter(
  timeFrame: {greaterThan: 1675025670, lessThan: 1675125670},
  location: {
    latest: {
      locationValue: {equalTo: "l1"},
      zoneValue: {includedIn: ["z1", "z2"]},
      continuousDuration: {greaterThan: 30000} // in milliseconds
    }
  }
) {
  id
  name
  location {
    id
    name
  }
}`

These examples demonstrate how to use the schema to filter assets based on various criteria like location, zone, asset properties, and category.






