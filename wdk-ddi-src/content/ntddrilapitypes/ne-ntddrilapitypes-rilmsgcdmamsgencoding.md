---
UID: NE:ntddrilapitypes.RILMSGCDMAMSGENCODING
title: RILMSGCDMAMSGENCODING
author: windows-driver-content
description: This topic supports the Windows driver infrastructure and is not intended to be used directly from your code.
old-location: netvista\rilmsgcdmamsgencoding.htm
old-project: netvista
ms.assetid: d0bc5fa4-d08d-484c-b6e0-35c7f1d144c3
ms.author: windowsdriverdev
ms.date: 1/18/2018
ms.keywords: ntddrilapitypes/RIL_MSGCODING_LATIN_HEBREW, ntddrilapitypes/RILMSGCDMAMSGENCODING, netvista.rilmsgcdmamsgencoding, ntddrilapitypes/RIL_MSGCODING_OCTET, RIL_MSGCODING_7BITASCII, RIL_MSGCODING_LATIN_HEBREW, ntddrilapitypes/RIL_MSGCODING_UNICODE, RIL_MSGCODING_8BITGSM, RILMSGCDMAMSGENCODING, ntddrilapitypes/RIL_MSGCODING_7BITASCII, ntddrilapitypes/RIL_MSGCODING_KOREAN, ntddrilapitypes/RIL_MSGCODING_JIS, RIL_MSGCODING_KOREAN, RIL_MSGCODING_LATIN, RIL_MSGCODING_IA5, RIL_MSGCODING_OCTET, ntddrilapitypes/RIL_MSGCODING_MAX, RIL_MSGCODING_MAX, ntddrilapitypes/RIL_MSGCODING_IA5, RIL_MSGCODING_7BITGSM, ntddrilapitypes/RIL_MSGCODING_8BITGSM, ntddrilapitypes/RIL_MSGCODING_LATIN, RIL_MSGCODING_UNICODE, RILMSGCDMAMSGENCODING enumeration [Network Drivers Starting with Windows Vista], ntddrilapitypes/RIL_MSGCODING_7BITGSM, RIL_MSGCODING_JIS
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: enum
req.header: ntddrilapitypes.h
req.include-header: 
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
req.irql: 
topictype: 
-	APIRef
-	kbSyntax
apitype: 
-	HeaderDef
apilocation: 
-	ntddrilapitypes.h
apiname: 
-	RILMSGCDMAMSGENCODING
product: Windows
targetos: Windows
req.typenames: RILMSGCDMAMSGENCODING
---

# RILMSGCDMAMSGENCODING enumeration


## -description


This topic supports the Windows driver infrastructure and is not intended to be used directly from your code.


## -syntax


````
typedef enum _RILMSGCDMAMSGENCODING { 
  RIL_MSGCODING_7BITASCII,
  RIL_MSGCODING_UNICODE,
  RIL_MSGCODING_7BITGSM,
  RIL_MSGCODING_8BITGSM,
  RIL_MSGCODING_OCTET,
  RIL_MSGCODING_IA5,
  RIL_MSGCODING_JIS,
  RIL_MSGCODING_KOREAN,
  RIL_MSGCODING_LATIN_HEBREW,
  RIL_MSGCODING_LATIN,
  RIL_MSGCODING_MAX
} RILMSGCDMAMSGENCODING;
````


## -enum-fields




### -field RIL_MSGCODING_UNKNOWN



### -field RIL_MSGCODING_7BITASCII



### -field RIL_MSGCODING_UNICODE



### -field RIL_MSGCODING_7BITGSM



### -field RIL_MSGCODING_8BITGSM



### -field RIL_MSGCODING_OCTET



### -field RIL_MSGCODING_IA5



### -field RIL_MSGCODING_JIS



### -field RIL_MSGCODING_KOREAN



### -field RIL_MSGCODING_LATIN_HEBREW



### -field RIL_MSGCODING_LATIN



### -field RIL_MSGCODING_MAX

