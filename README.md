# HackSouthCoastSummit

![Petrol Push Logo](docs/Petrol%20Push.png)

Team Working on it - Petrol Push

## Purpose of Solution - Usecase

As there are fuel shortages in UK we wanted to have an easy solution to notify each other about the availability of fuel at gas stations.

We use the three event types of our Flic buttons to indicate if

- A gas station has fuel
- A gas station ran out of fuel
- There is an issue at gas station (long queue)

The gas stations are shown as red/amber/green pins on a map in a Power Apps canvas app

## Canvas App

* Uses the built-in maps component
* Data is stored in Dataverse

![app details](docs/App-Details.png)

![app map](docs/App-Map.png)

## Dataverse Tables

* Petrol Stations
* Availabilities

with following custom columns:

![datamodel](/docs/PetrolPush-datamodel.png)

## Spotify API

* App registration
* Custom connector is included in the solution

## Azure Maps

Uses Azure Maps API server to get location information on nearest gas station to button press events. See also [ARM template](src/AzureMaps_ARM.json)

![AzureMaps flow](docs/AzureMaps-flow.png)

## Power Automate flow Spotify

### Environment variables

Device ID (get through API)
Petrol Song URI (in the web player)
Issue Song URI (in the web player)

### workflow

* Trigger: When availability changes to `petrol`
* Action: Get all available Spotify devices
* Action: Filter array for configured device
* Condition: Check if device is connected
  * TRUE: Start resume a user#s playlist
  * FALSE: Terminate

![Spotify flow](docs/PetrolPush-FlowSpotify.png)

## Power Automate Flows

## Azure Maps

### Workflow

![PetrolRecords flow](docs/PetrolRecords-flow.png)
