# Microsoft.Web/sites/virtualNetworkConnections template reference
API Version: 2015-08-01
## Template format

To create a Microsoft.Web/sites/virtualNetworkConnections resource, add the following JSON to the resources section of your template.

```json
{
  "name": "string",
  "type": "Microsoft.Web/sites/virtualNetworkConnections",
  "apiVersion": "2015-08-01",
  "id": "string",
  "kind": "string",
  "location": "string",
  "tags": {},
  "properties": {
    "vnetResourceId": "string",
    "certThumbprint": "string",
    "certBlob": "string",
    "routes": [
      {
        "id": "string",
        "name": "string",
        "kind": "string",
        "location": "string",
        "type": "string",
        "tags": {},
        "properties": {
          "name": "string",
          "startAddress": "string",
          "endAddress": "string",
          "routeType": "string"
        }
      }
    ],
    "resyncRequired": boolean,
    "dnsServers": "string"
  },
  "resources": []
}
```
## Property values

The following tables describe the values you need to set in the schema.

<a id="Microsoft.Web/sites/virtualNetworkConnections" />
### Microsoft.Web/sites/virtualNetworkConnections object
|  Name | Type | Required | Value |
|  ---- | ---- | ---- | ---- |
|  name | string | Yes |  |
|  type | enum | Yes | Microsoft.Web/sites/virtualNetworkConnections |
|  apiVersion | enum | Yes | 2015-08-01 |
|  id | string | No | Resource Id |
|  kind | string | No | Kind of resource |
|  location | string | Yes | Resource Location |
|  tags | object | No | Resource tags |
|  properties | object | Yes | [VnetInfoProperties object](#VnetInfoProperties) |
|  resources | array | No | [gateways](./virtualNetworkConnections/gateways.md) |


<a id="VnetInfoProperties" />
### VnetInfoProperties object
|  Name | Type | Required | Value |
|  ---- | ---- | ---- | ---- |
|  vnetResourceId | string | No | The vnet resource id |
|  certThumbprint | string | No | The client certificate thumbprint |
|  certBlob | string | No | A certificate file (.cer) blob containing the public key of the private key used to authenticate a
            Point-To-Site VPN connection. |
|  routes | array | No | The routes that this virtual network connection uses. - [VnetRoute object](#VnetRoute) |
|  resyncRequired | boolean | No | Flag to determine if a resync is required |
|  dnsServers | string | No | Dns servers to be used by this VNET. This should be a comma-separated list of IP addresses. |


<a id="VnetRoute" />
### VnetRoute object
|  Name | Type | Required | Value |
|  ---- | ---- | ---- | ---- |
|  id | string | No | Resource Id |
|  name | string | No | Resource Name |
|  kind | string | No | Kind of resource |
|  location | string | Yes | Resource Location |
|  type | string | No | Resource type |
|  tags | object | No | Resource tags |
|  properties | object | No | [VnetRouteProperties object](#VnetRouteProperties) |


<a id="VnetRouteProperties" />
### VnetRouteProperties object
|  Name | Type | Required | Value |
|  ---- | ---- | ---- | ---- |
|  name | string | No | The name of this route. This is only returned by the server and does not need to be set by the client. |
|  startAddress | string | No | The starting address for this route. This may also include a CIDR notation, in which case the end address must not be specified. |
|  endAddress | string | No | The ending address for this route. If the start address is specified in CIDR notation, this must be omitted. |
|  routeType | string | No | The type of route this is:
            DEFAULT - By default, every web app has routes to the local address ranges specified by RFC1918
            INHERITED - Routes inherited from the real Virtual Network routes
            STATIC - Static route set on the web app only

            These values will be used for syncing a Web App's routes with those from a Virtual Network. This operation will clear all DEFAULT and INHERITED routes and replace them
            with new INHERITED routes. |

