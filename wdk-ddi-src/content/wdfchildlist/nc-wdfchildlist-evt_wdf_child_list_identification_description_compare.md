---
UID: NC:wdfchildlist.EVT_WDF_CHILD_LIST_IDENTIFICATION_DESCRIPTION_COMPARE
title: EVT_WDF_CHILD_LIST_IDENTIFICATION_DESCRIPTION_COMPARE
author: windows-driver-content
description: A driver's EvtChildListIdentificationDescriptionCompare event callback function compares one child identification description with another.
old-location: wdf\evtchildlistidentificationdescriptioncompare.htm
old-project: wdf
ms.assetid: b807f9f8-588f-4303-be97-a9fd4cff2bbd
ms.author: windowsdriverdev
ms.date: 1/11/2018
ms.keywords: wdf.evtchildlistidentificationdescriptioncompare, EvtChildListIdentificationDescriptionCompare callback function, EvtChildListIdentificationDescriptionCompare, EVT_WDF_CHILD_LIST_IDENTIFICATION_DESCRIPTION_COMPARE, EVT_WDF_CHILD_LIST_IDENTIFICATION_DESCRIPTION_COMPARE, wdfchildlist/EvtChildListIdentificationDescriptionCompare, DFDeviceObjectChildListRef_58ed75b3-f129-4cfb-8d36-577b1cb8ffa0.xml, kmdf.evtchildlistidentificationdescriptioncompare
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: callback
req.header: wdfchildlist.h
req.include-header: Wdf.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 1.0
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
req.irql: <= DISPATCH_LEVEL
topictype: 
-	APIRef
-	kbSyntax
apitype: 
-	UserDefined
apilocation: 
-	WdfChildlist.h
apiname: 
-	EvtChildListIdentificationDescriptionCompare
product: Windows
targetos: Windows
req.typenames: *PWDBGEXTS_THREAD_OS_INFO, WDBGEXTS_THREAD_OS_INFO
req.product: Windows 10 or later.
---

# EVT_WDF_CHILD_LIST_IDENTIFICATION_DESCRIPTION_COMPARE callback


## -description


<p class="CCE_Message">[Applies to KMDF only]

A driver's <i>EvtChildListIdentificationDescriptionCompare</i> event callback function compares one child identification description with another.


## -prototype


````
EVT_WDF_CHILD_LIST_IDENTIFICATION_DESCRIPTION_COMPARE EvtChildListIdentificationDescriptionCompare;

BOOLEAN EvtChildListIdentificationDescriptionCompare(
  _In_ WDFCHILDLIST                                 ChildList,
  _In_ PWDF_CHILD_IDENTIFICATION_DESCRIPTION_HEADER FirstIdentificationDescription,
  _In_ PWDF_CHILD_IDENTIFICATION_DESCRIPTION_HEADER SecondIdentificationDescription
)
{ ... }
````


## -parameters




### -param ChildList [in]

A handle to a framework child-list object.


### -param FirstIdentificationDescription [in]

A pointer to a <a href="..\wdfchildlist\ns-wdfchildlist-_wdf_child_identification_description_header.md">WDF_CHILD_IDENTIFICATION_DESCRIPTION_HEADER</a> structure that identifies the one child identification description.


### -param SecondIdentificationDescription [in]

A pointer to a WDF_CHILD_IDENTIFICATION_DESCRIPTION_HEADER structure that identifies another child identification description.


## -returns


The <i>EvtChildListIdentificationDescriptionCompare</i> callback function must return <b>TRUE</b> if the two child identification descriptions match. Otherwise, this function must return <b>FALSE</b>.



## -remarks


If a bus driver is using <a href="https://docs.microsoft.com/en-us/windows-hardware/drivers/wdf/dynamic-enumeration">dynamic enumeration</a>, it can register an <i>EvtChildListIdentificationDescriptionCompare</i> callback function by calling <a href="..\wdffdo\nf-wdffdo-wdffdoinitsetdefaultchildlistconfig.md">WdfFdoInitSetDefaultChildListConfig</a> or <a href="..\wdfchildlist\nf-wdfchildlist-wdfchildlistcreate.md">WdfChildListCreate</a>. The driver can also register a second, special-case <i>EvtChildListIdentificationDescriptionCompare</i> callback function when it calls <a href="..\wdfchildlist\nf-wdfchildlist-wdfchildlistretrievenextdevice.md">WdfChildListRetrieveNextDevice</a>.

The framework compares two identification descriptions when it must determine if both descriptions identify the same device.

The <i>EvtChildListIdentificationDescriptionCompare</i> callback function must compare the contents of two identification descriptions and return <b>TRUE</b> if they match. A driver must supply this callback function if the framework cannot call <a href="..\wdm\nf-wdm-rtlcomparememory.md">RtlCompareMemory</a> to compare the identification descriptions. (The framework cannot call <b>RtlCompareMemory</b> if the descriptions contain pointers to additional memory.)

If your driver does not provide an <i>EvtChildListIdentificationDescriptionCompare</i> callback function, the framework compares identification descriptions by calling <a href="..\wdm\nf-wdm-rtlcomparememory.md">RtlCompareMemory</a>.

The following steps describe a possible scenario:
<ol>
<li>
The driver calls <a href="..\wdfchildlist\nf-wdfchildlist-wdfchildlistretrieveaddressdescription.md">WdfChildListRetrieveAddressDescription</a> to obtain the address description that is associated with the framework's copy of an identification description, which is stored in a child list.

</li>
<li>
The framework traverses the child list. To determine if a child's identification description matches the one that the driver specified when it called <a href="..\wdfchildlist\nf-wdfchildlist-wdfchildlistretrieveaddressdescription.md">WdfChildListRetrieveAddressDescription</a>, the framework calls either the <i>EvtChildListIdentificationDescriptionCompare</i> callback function (if it exists) or <a href="..\wdm\nf-wdm-rtlcomparememory.md">RtlCompareMemory</a>.

</li>
<li>
If the two identification descriptions match (and the comparison returns <b>TRUE</b>), the framework stops traversing the list.

</li>
<li>
The framework copies the address description into memory that the driver supplied when it called <a href="..\wdfchildlist\nf-wdfchildlist-wdfchildlistretrieveaddressdescription.md">WdfChildListRetrieveAddressDescription</a>.

</li>
</ol>The framework can use <a href="..\wdm\nf-wdm-rtlcomparememory.md">RtlCompareMemory</a> to compare identification descriptions, if each description consists of a single structure with a predetermined size that is specified by the <b>IdentificationDescriptionSize</b> member of the <a href="..\wdfchildlist\ns-wdfchildlist-_wdf_child_identification_description_header.md">WDF_CHILD_IDENTIFICATION_DESCRIPTION_HEADER</a> structure. However, sometimes the description must also contain additional information that is stored in dynamically allocated memory. In this case, you will typically define a description structure so that a member points to the dynamically allocated memory, and your driver must provide an <i>EvtChildListIdentificationDescriptionCompare</i> callback function. 

This callback function determines if two identification descriptions represent the same device. The callback function might not have to compare all of the structure members to make that determination. For example, suppose that an identification description contains a serial number and a set of hardware identifiers, as follows:
<div class="code"><span codelanguage=""><table>
<tr>
<th></th>
</tr>
<tr>
<td>
<pre>typedef struct _PDO_IDENTIFICATION_DESCRIPTION {
  WDF_CHILD_IDENTIFICATION_DESCRIPTION_HEADER Header;
  ULONG DeviceSerialNumber;
  ULONG CchHardwareIds;
  PWCHAR HardwareIds;
} PDO_IDENTIFICATION_DESCRIPTION, *PPDO_IDENTIFICATION_DESCRIPTION;</pre>
</td>
</tr>
</table></span></div>In this case, the <i>EvtChildListIdentificationDescriptionCompare</i> callback function probably has to compare only the <b>DeviceSerialNumber</b> members to determine if two descriptions represent the same device.

If your driver calls <a href="..\wdfchildlist\nf-wdfchildlist-wdfchildlistretrievenextdevice.md">WdfChildListRetrieveNextDevice</a> to traverse a device list, you can provide an additional <i>EvtChildListIdentificationDescriptionCompare</i> callback function that the framework uses when looking for the next description to retrieve. The framework looks for child devices that match driver-supplied <a href="..\wdfchildlist\ne-wdfchildlist-_wdf_retrieve_child_flags.md">WDF_RETRIEVE_CHILD_FLAGS</a>-typed flags. If a driver provides a special <i>EvtChildListIdentificationDescriptionCompare</i> callback function, the framework uses the callback function to refine the search. If the driver does not supply a special <i>EvtChildListIdentificationDescriptionCompare</i> callback function, the framework does <i>not</i> call <a href="..\wdm\nf-wdm-rtlcomparememory.md">RtlCompareMemory</a>--it simply returns each child device that matches the specified flags. 

The only <a href="https://msdn.microsoft.com/BFD91F00-5D35-4AF8-A6B6-F27DF64605D8">framework child-list object method</a> that a driver's <i>EvtChildListIdentificationDescriptionCompare</i> callback function can call is <a href="..\wdfchildlist\nf-wdfchildlist-wdfchildlistgetdevice.md">WdfChildListGetDevice</a>.

The framework acquires an internal child-list object lock before calling the <i>EvtChildListIdentificationDescriptionCompare</i><i>EvtChildListIdentificationDescriptionCompare</i> callback function. The callback function must only perform operations that are related to the compare operation, such as calling framework memory object methods and accessing object context space. It must not call methods that access other drivers.

For more information about dynamic enumeration, see <a href="https://docs.microsoft.com/en-us/windows-hardware/drivers/wdf/enumerating-the-devices-on-a-bus">Enumerating the Devices on a Bus</a>.



## -see-also

<a href="..\wdfchildlist\nf-wdfchildlist-wdfchildlistretrievenextdevice.md">WdfChildListRetrieveNextDevice</a>

<a href="..\wdm\nf-wdm-rtlcomparememory.md">RtlCompareMemory</a>

<a href="..\wdfchildlist\nf-wdfchildlist-wdfchildlistgetdevice.md">WdfChildListGetDevice</a>

<a href="..\wdfchildlist\ne-wdfchildlist-_wdf_retrieve_child_flags.md">WDF_RETRIEVE_CHILD_FLAGS</a>

<a href="..\wdfchildlist\nf-wdfchildlist-wdfchildlistcreate.md">WdfChildListCreate</a>

<a href="..\wdfchildlist\ns-wdfchildlist-_wdf_child_identification_description_header.md">WDF_CHILD_IDENTIFICATION_DESCRIPTION_HEADER</a>

<a href="..\wdfchildlist\nf-wdfchildlist-wdfchildlistretrieveaddressdescription.md">WdfChildListRetrieveAddressDescription</a>

<a href="..\wdffdo\nf-wdffdo-wdffdoinitsetdefaultchildlistconfig.md">WdfFdoInitSetDefaultChildListConfig</a>

 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [wdf\wdf]:%20EVT_WDF_CHILD_LIST_IDENTIFICATION_DESCRIPTION_COMPARE callback function%20 RELEASE:%20(1/11/2018)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
