---
UID: NS:wmistr.tagWNODE_EVENT_ITEM
title: tagWNODE_EVENT_ITEM
author: windows-driver-content
description: The WNODE_EVENT_ITEM structure contains data generated by a driver for an event.
old-location: kernel\wnode_event_item.htm
old-project: kernel
ms.assetid: 1805d174-ac10-4e76-9e3f-e9e156b769ec
ms.author: windowsdriverdev
ms.date: 1/4/2018
ms.keywords: WNODE_EVENT_ITEM structure [Kernel-Mode Driver Architecture], *PWNODE_EVENT_ITEM, wmistr/PWNODE_EVENT_ITEM, PWNODE_EVENT_ITEM, kernel.wnode_event_item, WNODE_EVENT_ITEM, PWNODE_EVENT_ITEM structure pointer [Kernel-Mode Driver Architecture], tagWNODE_EVENT_ITEM, wmistr/WNODE_EVENT_ITEM, kstruct_d_f4a86459-f5b4-4c9f-a266-d73c9bcba0ac.xml
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: struct
req.header: wmistr.h
req.include-header: Wmistr.h
req.target-type: Windows
req.target-min-winverclnt: 
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
req.irql: PASSIVE_LEVEL (see Remarks section)
topictype: 
-	APIRef
-	kbSyntax
apitype: 
-	HeaderDef
apilocation: 
-	wmistr.h
apiname: 
-	WNODE_EVENT_ITEM
product: Windows
targetos: Windows
req.typenames: WNODE_EVENT_ITEM, *PWNODE_EVENT_ITEM
req.product: Windows 10 or later.
---

# tagWNODE_EVENT_ITEM structure


## -description


The <b>WNODE_EVENT_ITEM</b> structure contains data generated by a driver for an event.


## -syntax


````
typedef struct tagWNODE_EVENT_ITEM {
  struct _WNODE_HEADER  WnodeHeader;
} WNODE_EVENT_ITEM, *PWNODE_EVENT_ITEM;
````


## -struct-fields




### -field WnodeHeader

Specifies a <a href="..\wmistr\ns-wmistr-_wnode_header.md">WNODE_HEADER</a> structure that contains information common to all <b>WNODE_<i>XXX</i></b> structures, such as the buffer size, the GUID that represents a data block associated with a request, and flags that provide information about the <b>WNODE_<i>XXX</i></b> data being passed or returned.


### -field _WNODE_HEADER

 



## -remarks


The <b>WnodeHeader</b> member of the <b>WNODE_EVENT_ITEM</b> structure is followed by a structure whose type depends on the flags that are set in <b>WnodeHeader</b>. Possibilities include <a href="..\wmistr\ns-wmistr-tagwnode_all_data.md">WNODE_ALL_DATA</a>, <a href="..\wmistr\ns-wmistr-tagwnode_single_instance.md">WNODE_SINGLE_INSTANCE</a>, and <a href="..\wmistr\ns-wmistr-tagwnode_single_item.md">WNODE_SINGLE_ITEM</a>. For more information about the flags, see <a href="..\wmistr\ns-wmistr-_wnode_header.md">WNODE_HEADER</a>.

The <b>ProviderId</b> member of the <a href="..\wmistr\ns-wmistr-_wnode_header.md">WNODE_HEADER</a> structure for use in a <b>WNODE_EVENT_ITEM</b> structure should be initialized using <a href="..\wdm\nf-wdm-iowmideviceobjecttoproviderid.md">IoWMIDeviceObjectToProviderId</a>.

A driver generates only events that it has previously enabled in response to an <a href="https://msdn.microsoft.com/library/windows/hardware/ff550859">IRP_MN_ENABLE_EVENTS</a> request. To generate an event, a driver calls <a href="..\wdm\nf-wdm-iowmiwriteevent.md">IoWMIWriteEvent</a> and passes a pointer to the <b>WNODE_EVENT_ITEM</b>. WMI queues the event for delivery to all data consumers registered for that event.

For best performance, events should be small in size. However, if the amount of data for an event exceeds the maximum size defined in the registry, a driver can pass a <a href="..\wmistr\ns-wmistr-tagwnode_event_reference.md">WNODE_EVENT_REFERENCE</a>, which WMI uses to query for the related <b>WNODE_EVENT_ITEM</b>. For more information about defining and generating WMI events, see <a href="https://msdn.microsoft.com/5c2ed322-0fc9-4004-9a5f-f4d3c6a59fe9">Windows Management Instrumentation</a>.



## -see-also

<a href="..\wmistr\ns-wmistr-tagwnode_all_data.md">WNODE_ALL_DATA</a>

<a href="..\wdm\nf-wdm-iowmideviceobjecttoproviderid.md">IoWMIDeviceObjectToProviderId</a>

<a href="..\wmistr\ns-wmistr-tagwnode_single_item.md">WNODE_SINGLE_ITEM</a>

<a href="..\wdm\nf-wdm-iowmiwriteevent.md">IoWMIWriteEvent</a>

<a href="..\wmistr\ns-wmistr-tagwnode_event_reference.md">WNODE_EVENT_REFERENCE</a>

<a href="..\wmistr\ns-wmistr-tagwnode_single_instance.md">WNODE_SINGLE_INSTANCE</a>

<a href="https://msdn.microsoft.com/library/windows/hardware/ff550859">IRP_MN_ENABLE_EVENTS</a>

<a href="..\wmistr\ns-wmistr-_wnode_header.md">WNODE_HEADER</a>

 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20WNODE_EVENT_ITEM structure%20 RELEASE:%20(1/4/2018)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
