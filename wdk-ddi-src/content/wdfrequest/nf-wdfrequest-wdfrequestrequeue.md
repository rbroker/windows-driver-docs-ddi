---
UID: NF:wdfrequest.WdfRequestRequeue
title: WdfRequestRequeue function
author: windows-driver-content
description: The WdfRequestRequeue method returns an I/O request to the head of the I/O queue from which it was delivered to the driver.
old-location: wdf\wdfrequestrequeue.htm
old-project: wdf
ms.assetid: 955859d2-7c4f-454c-8621-84bacf0b9770
ms.author: windowsdriverdev
ms.date: 1/11/2018
ms.keywords: wdf.wdfrequestrequeue, DFRequestObjectRef_a51243a8-1412-4765-93a1-7a8f3ab17814.xml, WdfRequestRequeue, PFN_WDFREQUESTREQUEUE, WdfRequestRequeue method, kmdf.wdfrequestrequeue, wdfrequest/WdfRequestRequeue
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: function
req.header: wdfrequest.h
req.include-header: Wdf.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 1.0
req.umdf-ver: 2.0
req.ddi-compliance: DriverCreate, InvalidReqAccess, InvalidReqAccessLocal, KmdfIrql, KmdfIrql2
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Wdf01000.sys (KMDF); WUDFx02000.dll (UMDF)
req.dll: 
req.irql: <=DISPATCH_LEVEL
topictype: 
-	APIRef
-	kbSyntax
apitype: 
-	LibDef
apilocation: 
-	Wdf01000.sys
-	Wdf01000.sys.dll
-	WUDFx02000.dll
-	WUDFx02000.dll.dll
apiname: 
-	WdfRequestRequeue
product: Windows
targetos: Windows
req.typenames: WDF_REQUEST_TYPE
req.product: Windows 10 or later.
---

# WdfRequestRequeue function


## -description


<p class="CCE_Message">[Applies to KMDF and UMDF]

The <b>WdfRequestRequeue</b> method returns an I/O request to the head of the I/O queue from which it was delivered to the driver.


## -syntax


````
NTSTATUS WdfRequestRequeue(
  _In_ WDFREQUEST Request
);
````


## -parameters




### -param Request [in]

A handle to a framework request object. 


## -returns


<b>WdfRequestRequeue</b>  returns STATUS_SUCCESS if the operation succeeds. Otherwise, this method might return one of the following values:
<table>
<tr>
<th>Return code</th>
<th>Description</th>
</tr>
<tr>
<td width="40%">
<dl>
<dt><b>STATUS_INVALID_PARAMETER</b></dt>
</dl>
</td>
<td width="60%">
An input parameter is invalid.

</td>
</tr>
<tr>
<td width="40%">
<dl>
<dt><b>STATUS_INVALID_DEVICE_REQUEST</b></dt>
</dl>
</td>
<td width="60%">
This value is returned if one of the following occurs:

<ul>
<li>
The specified I/O request did not come from an I/O queue.

</li>
<li>
The driver does not own the I/O request.

</li>
<li>
The request is cancelable.

</li>
<li>
The queue's dispatching method is not manual.

</li>
</ul>
</td>
</tr>
</table> 

This method might also return other <a href="https://msdn.microsoft.com/library/windows/hardware/ff557697">NTSTATUS values</a>.




A bug check occurs if the driver supplies an invalid object handle.



## -remarks


A driver can call <b>WdfRequestRequeue</b> only if it using the manual dispatching method for the I/O queue.

If the driver calls <b>WdfRequestRequeue</b> after calling <a href="..\wdfio\nf-wdfio-wdfioqueuepurge.md">WdfIoQueuePurge</a>, the requeue attempt may succeed before the purge is complete. In versions 1.9 and earlier of KMDF, this 
sequence causes the operating system to crash.  This problem is fixed in KMDF version 1.11 and later.

For more information about <b>WdfRequestRequeue</b>, see <a href="https://docs.microsoft.com/en-us/windows-hardware/drivers/wdf/requeuing-i-o-requests">Requeuing I/O Requests</a>.

