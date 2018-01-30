---
UID: NS:windot11._DOT11_PEER_INFO
title: _DOT11_PEER_INFO
author: windows-driver-content
description: Important  The Native 802.11 Wireless LAN interface is deprecated in Windows 10 and later.
old-location: netvista\dot11_peer_info.htm
old-project: netvista
ms.assetid: f1d5bbd9-45e3-4802-ab9b-77ff6bdcd6ec
ms.author: windowsdriverdev
ms.date: 1/18/2018
ms.keywords: PDOT11_PEER_INFO, DOT11_PEER_INFO structure [Network Drivers Starting with Windows Vista], netvista.dot11_peer_info, _DOT11_PEER_INFO, windot11/DOT11_PEER_INFO, DOT11_PEER_INFO, Native_802.11_data_types_411bca70-e6de-4dc0-8326-76f5eb5c6a86.xml, windot11/PDOT11_PEER_INFO, *PDOT11_PEER_INFO, PDOT11_PEER_INFO structure pointer [Network Drivers Starting with Windows Vista]
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: struct
req.header: windot11.h
req.include-header: Ndis.h
req.target-type: Windows
req.target-min-winverclnt: Available in Windows 7 and later versions of the Windows operating   systems.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: 
topictype: 
-	APIRef
-	kbSyntax
apitype: 
-	HeaderDef
apilocation: 
-	windot11.h
apiname: 
-	DOT11_PEER_INFO
product: Windows
targetos: Windows
req.typenames: *PDOT11_PEER_INFO, DOT11_PEER_INFO
req.product: Windows 10 or later.
---

# _DOT11_PEER_INFO structure


## -description


<div class="alert"><b>Important</b>  The <a href="https://msdn.microsoft.com/library/windows/hardware/ff560689">Native 802.11 Wireless LAN</a> interface is deprecated in Windows 10 and later. Please use the WLAN Device Driver Interface (WDI) instead. For more information about WDI, see <a href="https://msdn.microsoft.com/6EF92E34-7BC9-465E-B05D-2BCB29165A18">WLAN Universal Windows driver model</a>.</div><div> </div>The DOT11_PEER_INFO structure specifies information on a peer station within an independent basic
  service set (IBSS) network.
<div class="alert"><b>Note</b>  IBSS (Ad hoc) and SoftAP are deprecated. Starting with Windows 8.1 and Windows Server 2012 R2, use <a href="https://msdn.microsoft.com/library/windows/hardware/mt244265">Wi-Fi Direct</a>.</div><div> </div>

## -syntax


````
typedef struct _DOT11_PEER_INFO {
  DOT11_MAC_ADDRESS       MacAddress;
  USHORT                  usCapabilityInformation;
  DOT11_AUTH_ALGORITHM    AuthAlgo;
  DOT11_CIPHER_ALGORITHM  UnicastCipherAlgo;
  DOT11_CIPHER_ALGORITHM  MulticastCipherAlgo;
  BOOLEAN                 bWpsEnabled;
  USHORT                  usListenInterval;
  UCHAR                   ucSupportedRates[MAX_NUM_SUPPORTED_RATES_V2];
  USHORT                  usAssociationID;
  DOT11_ASSOCIATION_STATE AssociationState;
  DOT11_POWER_MODE        PowerMode;
  LARGE_INTEGER           liAssociationUpTime;
  DOT11_PEER_STATISTICS   Statistics;
} DOT11_PEER_INFO, *PDOT11_PEER_INFO;
````


## -struct-fields




### -field MacAddress

The media access control (MAC) address of the peer station within an independent BSS (IBSS)
     network.


### -field usCapabilityInformation

The 802.11 Capability Information field from the beacon or probe response frames that the 802.11
     station most recently received from the peer.


### -field AuthAlgo

The authentication algorithm that the 802.11 station resolved with the peer station during the
     association operation. For more information about the data type for the 
     <b>AuthAlgo</b> member, see 
     <a href="..\wlantypes\ne-wlantypes-_dot11_auth_algorithm.md">DOT11_AUTH_ALGORITHM</a>.
     

This member is not defined if the peer is not associated.


### -field UnicastCipherAlgo

The unicast cipher algorithm that the 802.11 station resolved with the peer station during the
     association operation. For more information about the data type for the 
     <b>UnicastCipherAlgo</b> member, see 
     <a href="..\wlantypes\ne-wlantypes-_dot11_cipher_algorithm.md">DOT11_CIPHER_ALGORITHM</a>.
     

This member is not defined if the peer is not associated.


### -field MulticastCipherAlgo

The multicast cipher algorithm that the 802.11 station resolved with the peer station during the
     association operation. For more information about the data type for the 
     <b>MulticastCipherAlgo</b> member, see 
     <a href="..\wlantypes\ne-wlantypes-_dot11_cipher_algorithm.md">DOT11_CIPHER_ALGORITHM</a>.
     

This member is not defined if the peer is not associated.


### -field bWpsEnabled

A Boolean value that indicates whether WiFi Protected Setup (WPS) is enabled for the peer station.
     If <b>TRUE</b>, WPS is enabled, and the authentication and cipher algorithms that are used by the peer might be
     different from the algorithms that are enabled on the AP.
     

This member should not be used if the peer is not associated.


### -field usListenInterval

A USHORT value that defines the 802.11 Listen Interval field that was obtained from the
     association request.
     

This member has a value of zero if the peer is not associated.


### -field ucSupportedRates

A UCHAR value that specifies the data rates supported by the peer station. These rates are based
     on the 802.11 Supported Rates IE from the beacon or probe response frames that the 802.11 station most
     recently received from the peer.
     

Each entry in the 
     <b>ucPeerSupportedRates</b> array is the value of an index within the table of data rates returned
     through a query of 
     <mshelp:link keywords="netvista.oid_dot11_data_rate_mapping_table" tabindex="0">
     OID_DOT11_DATA_RATE_MAPPING_TABLE</mshelp:link>. The index value must be between 2 and 127.

This member has a value of zero if the peer is not associated.


### -field usAssociationID

A USHORT value that specifies the 802.11 Association ID field from the association or
     re-association response frames that the 802.11 station received from the AP.
     

This member has a value of 0xFFFF if the peer is not associated.


### -field AssociationState

A 
     <a href="..\windot11\ne-windot11-_dot11_association_state.md">DOT11_ASSOCIATION_STATE</a>-type value
     that indicates the 802.11 authentication and association state of the peer station. The state can be
     either 
     <b>dot11_assoc_state_auth_unassoc</b> or 
     <b>dot11_assoc_state_auth_assoc</b>.
     

In the 
     <i>IEEE 802.11 Standard</i>, the 802.11 authentication procedure is optional for an independent network.
     Therefore, depending upon the IHV implementation, the state represented by the 
     <b>dot11_assoc_state_auth_unassoc</b> enumeration value may not be applicable.


### -field PowerMode

A 
     <a href="..\windot11\ne-windot11-_dot11_power_mode.md">DOT11_POWER_MODE</a>-type value that describes
     the latest power management mode of the peer station.


### -field liAssociationUpTime

A LARGEINTEGER value that specifies the timestamp when the 802.11 association procedure successfully
     completed. The miniport driver calls 
     <a href="..\ndis\nf-ndis-ndisgetcurrentsystemtime.md">NdisGetCurrentSystemTime</a> to get
     the timestamp of the association completion.
     

This member has a value of zero if the peer is not associated.


### -field Statistics

The statistics counters for data traffic, defined by the 
     <a href="..\windot11\ns-windot11-_dot11_peer_statistics.md">DOT11_PEER_STATISTICS</a> structure.
     

This member has a value of zero if the peer is not associated.


## -see-also

<a href="..\windot11\ns-windot11-_dot11_peer_info_list.md">DOT11_PEER_INFO_LIST</a>

<a href="..\windot11\ne-windot11-_dot11_association_state.md">DOT11_ASSOCIATION_STATE</a>

<a href="..\windot11\ns-windot11-_dot11_peer_statistics.md">DOT11_PEER_STATISTICS</a>

<a href="..\windot11\ne-windot11-_dot11_power_mode.md">DOT11_POWER_MODE</a>

<a href="..\ndis\nf-ndis-ndisgetcurrentsystemtime.md">NdisGetCurrentSystemTime</a>

<a href="..\ntddndis\ns-ntddndis-_ndis_object_header.md">NDIS_OBJECT_HEADER</a>

 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20DOT11_PEER_INFO structure%20 RELEASE:%20(1/18/2018)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
