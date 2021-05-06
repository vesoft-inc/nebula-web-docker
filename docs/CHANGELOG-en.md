# Change Log

## 2021.05.06 - v2.2.1
- Fix
  - Fix browser compatibility issues
  - Fix the rendering problem of big int type data
  - Fix the problem that no results can be obtained when importing data    
## 2021.04.23 - v2.2.0
- Feature Enhancements:
  - Explore
    - UI revision
    - Add operation panel and right-click menu, support zoom, dragging graph, modify vertex color and other operations
    - Support some operation shortcut keys operation
    - Support quick search of related vertexes in the canvas
    - Expanded function enhancement, support multi-step query
    - Added graph algorithm query function
- Fix:
  - Console
    - Fix the problem that the match return structure cannot lead to graph exploration

## 2021.03.24 - v2.1.9-beta
- Fix:
  - Import
    - Support import the integer type vertex id data

## 2021.03.01 - v2.1.8-beta
- Feature Enhancements:
  - Console
    - The history gql supports clearing
  - Explore
    - Optimize display of large amounts of data
    - Operation panel to add buttons to support zoom, drag and drop functions
## 2021.03.01 - v2.1.7-beta
- Feature Enhancements:
  - Console
    - EXPLAIN dot parameter results support graph
## 2021.02.22 - v2.1.6-beta
- Fix:
  - Fixed the inaccurate display when the number exceeds the precision
- Feature Enhancements:
  - Explore
    - Supported querying the integer type vertex id

## 2021.01.25 - v2.1.5-beta
- Fix:
  - Explore
    - Fix the rendering problem caused by the change of the returned data structure

## 2021.01.19 - v2.1.4-beta
- Feature Enhancements:
  - Schema
    - Supported configuring fixed string for space/tag/edge/index
  - Explore
    - When a vertex is selected, its information is fixed on the page
    - Configuration persistence for vertex/edge display


## 2021.01.12 - v2.1.3-beta
- Fix:
  - Explore
    - Fixed vertices rendering problem for the undo operation
    - Limited the maximum vertices number when exploring


## 2020.12.29 - v2.1.2-beta
- Feature Enhancements:
  - Explore
    - Supports exporting the returned results as pictures
    - Supports double-click to do quick exploration

## 2020.12.23 - v2.1.1-beta
- Fix:
  - Import
    - Fixed incorrect parsing of CSV files
    - Fixed truncation of large files.
    
## 2020.12.22 - v2.1.0-beta
- Feature Enhancements:
  - Console
    - Supports imporing subgraph with the `GET SUBGRAPH` statement
  - Import
    - Supports importing data
- Fix
  - Console
    - Fixes the sorting problem for the int/double columns
  - Explore 
    - Fixes the property display problem for vertices

## 2020.11.24 - v2.0.0-alpha
- Feature Enhancements:
  - Compatible with nebula graph v2.0.0-alpha
