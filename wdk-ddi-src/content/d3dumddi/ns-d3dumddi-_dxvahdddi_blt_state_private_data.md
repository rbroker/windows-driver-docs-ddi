---
UID: NS:d3dumddi._DXVAHDDDI_BLT_STATE_PRIVATE_DATA
title: "_DXVAHDDDI_BLT_STATE_PRIVATE_DATA"
author: windows-driver-content
description: The DXVAHDDDI_BLT_STATE_PRIVATE_DATA structure describes data that specifies the private bit-block transfer (bitblt) state.
old-location: display\dxvahdddi_blt_state_private_data.htm
old-project: display
ms.assetid: f9c0f137-e84c-4626-aa6a-dce352bf7bb0
ms.author: windowsdriverdev
ms.date: 12/29/2017
ms.keywords: display.dxvahdddi_blt_state_private_data, d3dumddi/DXVAHDDDI_BLT_STATE_PRIVATE_DATA, DXVA2_Structs_162bb87d-6383-4c29-b137-0316ace07a65.xml, DXVAHDDDI_BLT_STATE_PRIVATE_DATA structure [Display Devices], DXVAHDDDI_BLT_STATE_PRIVATE_DATA, _DXVAHDDDI_BLT_STATE_PRIVATE_DATA
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: struct
req.header: d3dumddi.h
req.include-header: D3dumddi.h
req.target-type: Windows
req.target-min-winverclnt: DXVAHDDDI_BLT_STATE_PRIVATE_DATA is supported beginning with the Windows 7 operating system.
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
-	d3dumddi.h
apiname:
-	DXVAHDDDI_BLT_STATE_PRIVATE_DATA
product: Windows
targetos: Windows
req.typenames: DXVAHDDDI_BLT_STATE_PRIVATE_DATA
---

# _DXVAHDDDI_BLT_STATE_PRIVATE_DATA structure


## -description


The DXVAHDDDI_BLT_STATE_PRIVATE_DATA structure describes data that specifies the private bit-block transfer (bitblt) state. 


## -syntax


````
typedef struct _DXVAHDDDI_BLT_STATE_PRIVATE_DATA {
  GUID Guid;
  UINT DataSize;
  VOID *pData;
} DXVAHDDDI_BLT_STATE_PRIVATE_DATA;
````


## -struct-fields




### -field Guid

[in] A GUID that identifies the private bitblt state.  


### -field DataSize

[in] The size, in bytes, of the private bitblt state data. 


### -field pData

[in/out] A pointer to the private bitblt state data. The caller sets <b>pData</b> to <b>NULL</b> to retrieve the size of the private bitblt state data. 


## -remarks


Unlike other bitblt states (<a href="..\d3dumddi\ne-d3dumddi-_dxvahdddi_blt_state.md">DXVAHDDDI_BLT_STATE</a>), the Direct3D runtime does not maintain the private bitblt state. An application and the driver communicate the private bitblt state directly in a proprietary manner, which consists of setting and retrieving the private bitblt state. To set private bitblt state, the application causes the Direct3D runtime to specify the DXVAHDDDI_BLT_STATE_PRIVATE state in the <b>State</b> member of the <a href="..\d3dumddi\ns-d3dumddi-_d3dddiarg_dxvahd_setvideoprocessbltstate.md">D3DDDIARG_DXVAHD_SETVIDEOPROCESSBLTSTATE</a> structure in a call to the driver's <a href="..\d3dumddi\nc-d3dumddi-pfnd3dddi_dxvahd_setvideoprocessbltstate.md">SetVideoProcessBltState</a> function. To retrieve private bitblt state, the application causes the Direct3D runtime to call the driver's <a href="..\d3dumddi\nc-d3dumddi-pfnd3dddi_dxvahd_getvideoprocessbltstateprivate.md">GetVideoProcessBltStatePrivate</a> function. 



## -see-also

<a href="..\d3dumddi\ns-d3dumddi-_d3dddiarg_dxvahd_setvideoprocessbltstate.md">D3DDDIARG_DXVAHD_SETVIDEOPROCESSBLTSTATE</a>

<a href="..\d3dumddi\nc-d3dumddi-pfnd3dddi_dxvahd_setvideoprocessbltstate.md">SetVideoProcessBltState</a>

<a href="..\d3dumddi\ne-d3dumddi-_dxvahdddi_blt_state.md">DXVAHDDDI_BLT_STATE</a>

<a href="..\d3dumddi\nc-d3dumddi-pfnd3dddi_dxvahd_getvideoprocessbltstateprivate.md">GetVideoProcessBltStatePrivate</a>

 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20DXVAHDDDI_BLT_STATE_PRIVATE_DATA structure%20 RELEASE:%20(12/29/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
