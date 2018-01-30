---
UID: NF:rilapi.RIL_Dial
title: RIL_Dial function
author: windows-driver-content
description: This topic supports the Windows driver infrastructure and is not intended to be used directly from your code.
old-location: netvista\ril_dial.htm
old-project: netvista
ms.assetid: 755a834b-6590-4289-99b1-058690c1ad4f
ms.author: windowsdriverdev
ms.date: 1/18/2018
ms.keywords: netvista.ril_dial, RIL_Dial, rilapi/RIL_Dial, RIL_Dial method [Network Drivers Starting with Windows Vista]
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: function
req.header: rilapi.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: Windows 10
req.target-min-winversvr: Windows Server 2016
req.kmdf-ver: 
req.umdf-ver: 
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: NtosKrnl.exe
req.dll: 
req.irql: 
topictype: 
-	APIRef
-	kbSyntax
apitype: 
-	HeaderDef
apilocation: 
-	rilapi.h
apiname: 
-	RIL_Dial
product: Windows
targetos: Windows
req.typenames: RH_QUERY_CONNECTION_PROPERTIES_OUTPUT_BUFFER, *PRH_QUERY_CONNECTION_PROPERTIES_OUTPUT_BUFFER
req.product: Windows 10 or later.
---

# RIL_Dial function


## -description


This topic supports the Windows driver infrastructure and is not intended to be used directly from your code. 

            


## -syntax


````
HRESULT  RIL_Dial(
   HRIL                               hRil,
   LPVOID                             lpContext,
   DWORD                              dwExecutor,
   const RILADDRESS                   lpraAddress,
   DWORD                              dwOptions,
   RILCALLTYPE                        dwType,
   const LPRILCALLMEDIAOFFERANSWERSET lprcmOfferAnswer
);
````


## -parameters




### -param hRil



### -param lpContext



### -param dwExecutor



### -param lpraAddress



### -param dwOptions



### -param dwType



### -param lprcmOfferAnswer



## -returns


If this method succeeds, it returns <b xmlns:loc="http://microsoft.com/wdcml/l10n">S_OK</b>. Otherwise, it returns an <b xmlns:loc="http://microsoft.com/wdcml/l10n">HRESULT</b> error code.

