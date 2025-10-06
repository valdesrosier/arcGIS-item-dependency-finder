# ArcGIS Item Dependency Finder

This notebook helps ArcGIS administrators, analysts, and developers trace relationships between items in ArcGIS Online or ArcGIS Enterprise.  

It identifies where a specific item—such as a Feature Layer, Web Map, Web Experience, Dashboard, or StoryMap—is used across your organization, and conversely, which maps, layers, or embedded apps are referenced within a given app.

---

## Overview

ArcGIS content is often interconnected across maps, apps, dashboards, and experiences. When maintaining or replacing a dataset or service, it can be difficult to answer questions like:

- Which apps use this feature layer?
- Which maps are included in this Experience Builder app?
- Does this StoryMap embed any dashboards or other apps?

This notebook scans item JSON data to detect:
- Referenced item IDs (`itemId`, `serviceItemId`)
- Referenced service URLs (`FeatureServer`, `MapServer`)
- Embedded apps or dashboards linked through iframes or URLs

The results display as HTML tables with clickable links for easy review.

---

## Features

| Capability | Description |
|-------------|--------------|
| Layer-to-App Trace | Input a Feature Layer item ID and find all Web Maps, Apps, and Experiences that use it |
| App-to-Content Trace | Input an App (Experience, Dashboard, or StoryMap) ID and find all referenced Web Maps and Layers |
| Embedded App Detection | Detects and lists embedded ArcGIS apps, Dashboards, Hub pages, and Survey123 forms |
| Portal Compatible | Works with both ArcGIS Online and ArcGIS Enterprise |
| Exportable Tables | Results display as HTML tables and can be exported from Pandas DataFrames |

---

## Supported Item Types

- Feature Layer / Feature Service
- Web Maps
- ArcGIS Experience Builder Applications
- ArcGIS Dashboards
- ArcGIS StoryMaps
- ArcGIS Hub

## Notes
This script performs read-only searches using the ArcGIS REST API.
It does not modify or delete content.
If you’re working in a large organization, you may want to limit the search by owner or organization ID instead of scanning all items (max_items=-1), as full searches can take several minutes.
