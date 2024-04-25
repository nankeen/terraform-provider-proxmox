---
layout: page
title: proxmox_virtual_environment_hardware_mapping_usb
parent: Resources
subcategory: Virtual Environment
description: |-
  Manages a USB hardware mapping in a Proxmox VE cluster.
---

# Resource: proxmox_virtual_environment_hardware_mapping_usb

Manages a USB hardware mapping in a Proxmox VE cluster.

## Example Usage

```terraform
resource "proxmox_virtual_environment_hardware_mapping_usb" "example" {
  comment = "This is a comment"
  name    = "example"
  # The actual map of devices.
  map = [
    {
      comment = "This is a device specific comment"
      id      = "8087:0a2b"
      node    = "pve"
      # This attribute is optional, but can be used to map the device based on its port instead of only the device ID.
      path = "1-8.2"
    },
  ]
}
```

<!-- schema generated by tfplugindocs -->
## Schema

### Required

- `map` (Attributes Set) The actual map of devices for the hardware mapping. (see [below for nested schema](#nestedatt--map))
- `name` (String) The name of this hardware mapping.

### Optional

- `comment` (String) The comment of this USB hardware mapping.

### Read-Only

- `id` (String) The unique identifier of this USB hardware mapping resource.

<a id="nestedatt--map"></a>
### Nested Schema for `map`

Required:

- `id` (String) The ID of the map.
- `node` (String) The node name of the map.

Optional:

- `comment` (String) The comment of the mapped USB device.
- `path` (String) The path of the map. For hardware mappings of type USB the path is optional and indicates that the device is mapped through the device ID instead of ports.

## Import

Import is supported using the following syntax:

```shell
#!/usr/bin/env sh
# A USB hardware mapping can be imported using their name, e.g.:
terraform import proxmox_virtual_environment_hardware_mapping_usb.example example
```