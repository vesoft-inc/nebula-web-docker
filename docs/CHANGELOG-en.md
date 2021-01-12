# Change Log

## 2021.01.12 - v1.2.5-beta
- Fix:
  - Explore
    - Fixed vertices rendering problem for the undo operation
    - Limited the maximum vertices number when exploring


## 2020.12.29 - v1.2.4-beta
- Feature Enhancements:
  - Explore
    - Supports exporting the returned results as pictures
    - Supports double-click to do quick exploration

## 2020.12.23 - v1.2.3-beta
- Fix:
  - Import
    - Fixed incorrect parsing of CSV files
    - Fixed truncation of large files.

## 2020.12.17 - v1.2.2-beta
- Feature Enhancements:
  - Explore
    - Supports importing dangling edges
- Fix
  - Console
    - Fixed the sorting bugs

## 2020.11.02 - v1.2.1-beta
- Feature Enhancements:
  - Console
    - Supports visualization of FIND PATH
    - Supports AS clause in the Open In Explore

## 2020.10.19 - v1.2.0-beta
- Feature Enhancements:
  - Support visualized schema operations
    - Support retrieving, creating, and deleting graph spaces
    - Support retrieving, creating, updating, and deleting tags in a graph space 
    - Support retrieving, creating, updating, and deleting edge types in a graph space 
    - Support retrieving, creating, and deleting indexes in a graph space 

## 2020.8.20 - v1.1.1-beta
- Feature Enhancements:
  - Add the link to the Nebula Graph repo on the navigation bar 
- Fix
  - Explore 
    - Support using hash or uuid to pre-process strings to generate VIDs 
    - Fix precision of double data for the query result

## 2020.8.18 - v1.1.0-beta
- Feature Enhancements:
  - Explore 
    - Support query by index
    - Support pre-processing VIDs before query by VID
  - Console 
    - Support importing the results of vertex query into the graph exploration board
- Fix:
  - Explore 
    - Fixed the display problem for boolean properties
- Optimization
  - Improve text && interaction

## 2020.7.31 - v1.0.10-beta
- Feature Enhancements:
  - Explore - Add `limit` when expand
  - Console - Support exporting results in csv format.

## 2020.7.9 - v1.0.9-beta

- Fix:
  - Console - Support horizontal scroll bar when returning too many columns
  - Import - Support searching when selecting files
  - Import - Support importing timestamp data type
  - Explore - Fix query stitching problem when clicking the small icon

## 2020.7.3 - v1.0.8-beta

- Feature Enhancements:
  - Explore - Support edge attributes select to show
  - Console - Support show gql exec time cost

## 2020.7.1 - v1.0.7-beta

- Fix:
  - Console shortest|full path show problem fix

## 2020.6.13 - v1.0.6-beta

- Feature Enhancements:
  - Improve the display of Explore

## 2020.5.29 - v1.0.5-beta

- Feature Enhancements:
  - Imporve the interaction of Explore
  - Support long time connection
  - Modify the hotkey conflict of selecting multiple vertices at the same time. Drag to select with shift + click
  - Improve text && interaction

## 2020.4.23 - v1.0.4-beta

- Feature Enhancements:
  - Explore:
    - Support remove vertex explored
    - Support select multi edge to explore at same time
    - Support select multi select vertex by click with cmd/win key pressed down
  - Others:
    - Fix some experience bugs

## 2020.4.15 - v1.0.3-beta

- New Features
  - Import - You can now deploy the Nebula Studio service on remote servers, access it and import data to it remotely. The restriction of deploying Nebula Studio on your local host has been removed.
  - Explore - You can perform BIDIRECT query in Nebula Studio and select the color schemes by steps or tags to display newly-discovered nodes.

- Breaking Changes
  - Modified the project structure to enable to be deployed remote, please update the [repo](https://github.com/vesoft-inc/nebula-web-docker) by `git pull origin master && docker-compose pull`.


## 2020.3.31 - v1.0.2-beta

- New Features:
  - Visualization explore add edge attributes show && config tag fields show on graph

## 2020.3.2 - v1.0.1-beta

- Feature Enhancements:
  - Support spaces select and cache when executing in Console
  - Add more lines to show in Console

## 2020.1.16 - v1.0.0-beta

- New Features:
  - Console
  - Import Data
  - Visualization
- [User Manual](nebula-graph-studio-user-guide-en.md)
