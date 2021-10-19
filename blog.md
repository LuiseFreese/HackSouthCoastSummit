# How 3 makers, 2 devs and a princess came together to save kittens for a hackathon

## The Story (Michael)

## The flic and the flow (Tomasz)

## The canvas app (Carmen)

With the data stored in Dataverse, the canvas app can be created to display the available information and inform the people where they can find fuel. The canvas app consists of a header (with the company logo, name and refresh icon) and a map control.

We are using the built-in map control, which allows us to display the gas stations with their appropriate color, automatically center on the user's current location and display additional information about each gas station when selecting the location pin.

To get the location pins on the map, we added the Dataverse table as a source in the `Items` property of the map control. We are currently not doing any filtering, but this could be added if needed. The latitude, longitude, labels and colors is each contained in a specific column within the data source. These are provided as values for the following properties (where the text between quotes is the name of the column in the Dataverse table):

- `ItemsLabels` = `"woi_name"`
- `ItemsLatitudes` = `"woi_latitude"`
- `ItemsLongitudes`= `"woi_longitude"`
- `ItemsColors` = `"woi_color"`

The `woi_colors` columns is defined as a calculated column that is influenced by the value of the `Petrol Status` column in the same table. `Petrol Status` contains the last known status of fuel at the respective station. The colors are defined as hex values with the following mapping:
| Last Known Status | Color | Color name |
|-------------------|-----------|-------------|
| Petrol | "#66FF00" | Light Green |
| No petrol | "#FF0000" | Red |
| Issue | "#FFBF00" | Amber |

The color of the grouped pins is defined by the `PinColor` property of the map control. It is set to `Green`, which is a darker color than the green used for the stations with fuel.

When a pin is selected, the info card is shown. This is defined by setting the `InfoCards` property of the map to `'Microsoft.Map.InfoCards'.OnClick`. The fields that are shown on the info card are defined by editing the `Fields` in the properties pane of the map. Four fields are shown on the info card:

- Name
- Address
- Postal code
- Modified on (to know when the station's status was last updated)

This can be seen on the below screenshot.
![Properties pane of the map control with fields expanded and showing "name", "address", "postal code" and "modified on"](docs/App-MapFields.png)

## The custom connector to Azure maps (Lee)

## The Spotify connector for the vibes (Yannick)

## The princess and the push (Luise)

Straight from the beginning of the hackathon, we took care of documenting our architecture decisions and how we would implement them. We set up a [GitHub repository](https://github.com/LuiseFreese/HacksouthCoastSummit), invited everyone in the team so they could commit their files. We continued to document all major steps so that everyone could use this as a reference to explain our solution, although each member was only in charge of their workload. Getting all information and documenting while building ensured accuracy but also gave an opportunity to think through the app and reflect on decisions.

We also published the solution itself in this repository to give community the chance to play with our app

## What can we learn from this epic quest? (everybody)

- do things the right way instead of trying to do everything but in a messy way
- take care of documentation
- team of diverse backgrounds, experiences and perspectives leads to great outcomes regarding
  - technical solution
  - learning
  - team spirit
