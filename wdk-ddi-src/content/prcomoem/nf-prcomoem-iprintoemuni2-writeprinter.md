---
UID: NF:prcomoem.IPrintOemUni2.WritePrinter
title: IPrintOemUni2::WritePrinter method
author: windows-driver-content
description: The IPrintOemUni2::WritePrinter method, if supported, enables a rendering plug-in to capture all output data generated by a Unidrv driver.
old-location: print\iprintoemuni2_writeprinter.htm
old-project: print
ms.assetid: 61901d4d-7821-40b4-aaef-fd679985abb3
ms.author: windowsdriverdev
ms.date: 1/18/2018
ms.keywords: IPrintOemUni2::WritePrinter, IPrintOemUni2 interface [Print Devices], WritePrinter method, print.iprintoemuni2_writeprinter, prcomoem/IPrintOemUni2::WritePrinter, print_unidrv-pscript_rendering_8dfd9075-d0a9-451b-bb31-9e1a55c16c1c.xml, WritePrinter method [Print Devices], WritePrinter, IPrintOemUni2, WritePrinter method [Print Devices], IPrintOemUni2 interface
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: method
req.header: prcomoem.h
req.include-header: Prcomoem.h
req.target-type: Desktop
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
req.lib: prcomoem.h
req.dll: 
req.irql: 
topictype: 
-	APIRef
-	kbSyntax
apitype: 
-	COM
apilocation: 
-	prcomoem.h
apiname: 
-	IPrintOemUni2.WritePrinter
product: Windows
targetos: Windows
req.typenames: *POEMPTOPTS, OEMPTOPTS
req.product: Windows 10 or later.
---

# IPrintOemUni2::WritePrinter method


## -description


The <code>IPrintOemUni2::WritePrinter</code> method, if supported, enables a rendering plug-in to capture all output data generated by a Unidrv driver. If this method is not supported, the output data would otherwise be sent to the spooler in a call to the spooler's WritePrinter API (described in the Microsoft Windows SDK documentation).


## -syntax


````
HRESULT WritePrinter(
   PDEVOBJ pdevobj,
   PVOID   pBuf,
   DWORD   cbBuffer,
   PDWORD  pcbWritten
);
````


## -parameters




### -param pdevobj

Pointer to a <a href="..\printoem\ns-printoem-_devobj.md">DEVOBJ</a> structure.


### -param pBuf

Pointer to the first byte of an array of bytes that contains the output data generated by the Unidrv driver.


### -param cbBuffer

Specifies the size, in bytes, of the array pointed to by <i>pBuf</i>.


### -param pcbWritten

Pointer to a DWORD value that receives the number of bytes of data that were successfully sent to the plug-in.


## -returns


If successful, this method returns S_OK. Otherwise, this method should return an appropriate value in the returned HRESULT.



## -remarks


At <a href="https://msdn.microsoft.com/library/windows/hardware/ff556211">DrvEnablePDEV</a> time, the Unidrv driver calls this method with <i>pBuf</i> and <i>pdevobj</i> set to <b>NULL</b>, and <i>cbBuf</i> set to 0, to detect whether the plug-in implements this function. The plug-in should return S_OK to indicate it implements this method, and should return E_NOTIMPL otherwise.

This method should report the number of bytes written to the spooler's <b>WritePrinter</b> function in <i>pcbWritten</i>. A value of zero carries no special meaning; errors must be reported through the returned HRESULT.

The <code>IPrintOemUni2::WritePrinter</code> method is optional. If a rendering plug-in implements this method, the plug-in's <a href="https://msdn.microsoft.com/library/windows/hardware/ff554253">IPrintOemUni::GetImplementedMethod</a> method must return S_OK when it receives "WritePrinter" as input.

