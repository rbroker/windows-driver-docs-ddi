---
UID: NE:ntddk._PHYSICAL_COUNTER_RESOURCE_DESCRIPTOR_TYPE
title: "_PHYSICAL_COUNTER_RESOURCE_DESCRIPTOR_TYPE" (ntddk.h)
description: The PHYSICAL_COUNTER_RESOURCE_DESCRIPTOR_TYPE enumeration contains constants that indicate the type of hardware performance counter resource that is described by a PHYSICAL_COUNTER_RESOURCE_DESCRIPTOR structure.
old-location: kernel\physical_counter_resource_descriptor_type.htm
tech.root: kernel
ms.assetid: 58fa1312-eb21-405d-85de-59ea69d9447f
ms.date: 04/30/2018
ms.keywords: PHYSICAL_COUNTER_RESOURCE_DESCRIPTOR_TYPE, PHYSICAL_COUNTER_RESOURCE_DESCRIPTOR_TYPE enumeration [Kernel-Mode Driver Architecture], ResourceTypeExtendedCounterConfiguration, ResourceTypeMax, ResourceTypeOverflow, ResourceTypeRange, ResourceTypeSingle, _PHYSICAL_COUNTER_RESOURCE_DESCRIPTOR_TYPE, kernel.physical_counter_resource_descriptor_type, ntddk/PHYSICAL_COUNTER_RESOURCE_DESCRIPTOR_TYPE, ntddk/ResourceTypeExtendedCounterConfiguration, ntddk/ResourceTypeMax, ntddk/ResourceTypeOverflow, ntddk/ResourceTypeRange, ntddk/ResourceTypeSingle, sysenum_cb8d2405-4299-4e91-9f55-dc9c84587148.xml
ms.topic: enum
req.header: ntddk.h
req.include-header: Ntddk.h, Ntifs.h
req.target-type: Windows
req.target-min-winverclnt: Supported in Windows 7 and later versions of Windows.
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
topic_type:
-	APIRef
-	kbSyntax
api_type:
-	HeaderDef
api_location:
-	Ntddk.h
api_name:
-	PHYSICAL_COUNTER_RESOURCE_DESCRIPTOR_TYPE
product:
- Windows
targetos: Windows
req.typenames: PHYSICAL_COUNTER_RESOURCE_DESCRIPTOR_TYPE
---

# _PHYSICAL_COUNTER_RESOURCE_DESCRIPTOR_TYPE enumeration


## -description


The <b>PHYSICAL_COUNTER_RESOURCE_DESCRIPTOR_TYPE</b> enumeration contains constants that indicate the type of hardware performance counter resource that is described by a <a href="https://msdn.microsoft.com/library/windows/hardware/ff558796">PHYSICAL_COUNTER_RESOURCE_DESCRIPTOR</a> structure.


## -enum-fields




### -field ResourceTypeSingle

A single hardware counter. The counter is described by the <b>u.CounterIndex</b> member of the <b>PHYSICAL_COUNTER_RESOURCE_DESCRIPTOR</b> structure.


### -field ResourceTypeRange

A range of counter indexes. The counter indexes are described by the <b>u.Range</b> member of the <b>PHYSICAL_COUNTER_RESOURCE_DESCRIPTOR</b> structure.


### -field ResourceTypeExtendedCounterConfiguration

An extended counter configuration register address. The register address is contained in the <b>u.ExtendedRegisterAddress</b> member of the <b>PHYSICAL_COUNTER_RESOURCE_DESCRIPTOR</b> structure. This value is used only on Intel NetBurst systems.


### -field ResourceTypeOverflow

A counter overflow interrupt. The <b>u</b> member of the <b>PHYSICAL_COUNTER_RESOURCE_DESCRIPTOR</b> structure is not used for this counter resource type.


### -field ResourceTypeMax

The maximum value in this enumeration type. 


## -remarks



The <b>Type</b> member of a <b>PHYSICAL_COUNTER_RESOURCE_DESCRIPTOR</b> structure uses a <b>PHYSICAL_COUNTER_RESOURCE_DESCRIPTOR_TYPE</b> enumeration constant to indicate the type of counter resource that is described by the structure.




## -see-also




<a href="https://msdn.microsoft.com/library/windows/hardware/ff558796">PHYSICAL_COUNTER_RESOURCE_DESCRIPTOR</a>
 

 

