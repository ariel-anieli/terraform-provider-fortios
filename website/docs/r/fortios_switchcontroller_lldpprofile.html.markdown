---
subcategory: "FortiGate Switch-Controller"
layout: "fortios"
page_title: "FortiOS: fortios_switchcontroller_lldpprofile"
description: |-
  Configure FortiSwitch LLDP profiles.
---

# fortios_switchcontroller_lldpprofile
Configure FortiSwitch LLDP profiles.

## Example Usage

```hcl
resource "fortios_switchcontroller_lldpprofile" "trname" {
  auto_isl                 = "enable"
  auto_isl_hello_timer     = 3
  auto_isl_port_group      = 0
  auto_isl_receive_timeout = 60
  med_tlvs                 = "inventory-management network-policy"
  name                     = "1"
}
```

## Argument Reference

The following arguments are supported:

* `name` - Profile name.
* `med_tlvs` - Transmitted LLDP-MED TLVs (type-length-value descriptions).
* `n8021_tlvs` - Transmitted IEEE 802.1 TLVs. Valid values: `port-vlan-id`.
* `n8023_tlvs` - Transmitted IEEE 802.3 TLVs.
* `auto_isl` - Enable/disable auto inter-switch LAG. Valid values: `disable`, `enable`.
* `auto_isl_hello_timer` - Auto inter-switch LAG hello timer duration (1 - 30 sec, default = 3).
* `auto_isl_receive_timeout` - Auto inter-switch LAG timeout if no response is received (3 - 90 sec, default = 9).
* `auto_isl_port_group` - Auto inter-switch LAG port group ID (0 - 9).
* `auto_mclag_icl` - Enable/disable MCLAG inter chassis link. Valid values: `disable`, `enable`.
* `auto_isl_auth` - Auto inter-switch LAG authentication mode. Valid values: `legacy`, `strict`, `relax`.
* `auto_isl_auth_user` - Auto inter-switch LAG authentication user certificate.
* `auto_isl_auth_identity` - Auto inter-switch LAG authentication identity.
* `auto_isl_auth_reauth` - Auto inter-switch LAG authentication reauth period in seconds(10 - 3600, default = 3600).
* `auto_isl_auth_encrypt` - Auto inter-switch LAG encryption mode. Valid values: `none`, `mixed`, `must`.
* `auto_isl_auth_macsec_profile` - Auto inter-switch LAG macsec profile for encryption.
* `med_network_policy` - Configuration method to edit Media Endpoint Discovery (MED) network policy type-length-value (TLV) categories. The structure of `med_network_policy` block is documented below.
* `med_location_service` - Configuration method to edit Media Endpoint Discovery (MED) location service type-length-value (TLV) categories. The structure of `med_location_service` block is documented below.
* `custom_tlvs` - Configuration method to edit custom TLV entries. The structure of `custom_tlvs` block is documented below.
* `dynamic_sort_subtable` - Sort sub-tables, please do not set this parameter when configuring static sub-tables. Options: [ false, true, natural, alphabetical ]. false: Default value, do not sort tables; true/natural: sort tables in natural order. For example: [ a10, a2 ] --> [ a2, a10 ]; alphabetical: sort tables in alphabetical order. For example: [ a10, a2 ] --> [ a10, a2 ].
* `get_all_tables` - Get all sub-tables including unconfigured tables. Do not set this variable to true if you configure sub-table in another resource, otherwise, conflicts and overwrite will occur. Options: [ false, true ]. false: Default value, do not get unconfigured tables; true: get all tables including unconfigured tables. 
* `vdomparam` - Specifies the vdom to which the resource will be applied when the FortiGate unit is running in VDOM mode. Only one vdom can be specified. If you want to inherit the vdom configuration of the provider, please do not set this parameter.

The `med_network_policy` block supports:

* `name` - Policy type name.
* `status` - Enable or disable this TLV. Valid values: `disable`, `enable`.
* `vlan_intf` - VLAN interface to advertise; if configured on port.
* `assign_vlan` - Enable/disable VLAN assignment when this profile is applied on managed FortiSwitch port. Valid values: `disable`, `enable`.
* `vlan` - ID of VLAN to advertise, if configured on port (0 - 4094, 0 = priority tag).
* `priority` - Advertised Layer 2 priority (0 - 7; from lowest to highest priority).
* `dscp` - Advertised Differentiated Services Code Point (DSCP) value, a packet header value indicating the level of service requested for traffic, such as high priority or best effort delivery.

The `med_location_service` block supports:

* `name` - Location service type name.
* `status` - Enable or disable this TLV. Valid values: `disable`, `enable`.
* `sys_location_id` - Location service ID.

The `custom_tlvs` block supports:

* `name` - TLV name (not sent).
* `oui` - Organizationally unique identifier (OUI), a 3-byte hexadecimal number, for this TLV.
* `subtype` - Organizationally defined subtype (0 - 255).
* `information_string` - Organizationally defined information string (0 - 507 hexadecimal bytes).


## Attribute Reference

In addition to all the above arguments, the following attributes are exported:
* `id` - an identifier for the resource with format {{name}}.

## Import

SwitchController LldpProfile can be imported using any of these accepted formats:
```
$ terraform import fortios_switchcontroller_lldpprofile.labelname {{name}}

If you do not want to import arguments of block:
$ export "FORTIOS_IMPORT_TABLE"="false"
$ terraform import fortios_switchcontroller_lldpprofile.labelname {{name}}
$ unset "FORTIOS_IMPORT_TABLE"
```
