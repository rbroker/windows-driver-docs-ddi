---
UID: NF:ntstrsafe.RtlUnicodeStringCchCatN
title: RtlUnicodeStringCchCatN function
author: windows-driver-content
description: The RtlUnicodeStringCchCatN function concatenates two strings that are contained in UNICODE_STRING structures while limiting the size of the copied string.
old-location: kernel\rtlunicodestringcchcatn.htm
old-project: kernel
ms.assetid: 03715e4e-6f8a-402d-9544-b01cc06d1809
ms.author: windowsdriverdev
ms.date: 1/4/2018
ms.keywords: safestrings_3958e107-6da7-4bf5-a592-097ddb52c1b2.xml, ntstrsafe/RtlUnicodeStringCchCatN, kernel.rtlunicodestringcchcatn, RtlUnicodeStringCchCatN function [Kernel-Mode Driver Architecture], RtlUnicodeStringCchCatN
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: function
req.header: ntstrsafe.h
req.include-header: Ntstrsafe.h
req.target-type: Desktop
req.target-min-winverclnt: Available in Windows XP with Service Pack 1 (SP1) and later versions of Windows.
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
req.lib: Ntstrsafe.lib
req.dll: 
req.irql: PASSIVE_LEVEL
topictype: 
-	APIRef
-	kbSyntax
apitype: 
-	LibDef
apilocation: 
-	Ntstrsafe.lib
-	Ntstrsafe.dll
apiname: 
-	RtlUnicodeStringCchCatN
product: Windows
targetos: Windows
req.typenames: *PBATTERY_REPORTING_SCALE, BATTERY_REPORTING_SCALE
---

# RtlUnicodeStringCchCatN function


## -description


The <b>RtlUnicodeStringCchCatN</b> function concatenates two strings that are contained in <a href="..\wudfwdm\ns-wudfwdm-_unicode_string.md">UNICODE_STRING</a> structures while limiting the size of the copied string.


## -syntax


````
NTSTATUS RtlUnicodeStringCchCatN(
  _Inout_ PUNICODE_STRING  DestinationString,
  _In_    PCUNICODE_STRING SourceString,
  _In_    size_t           cchToAppend
);
````


## -parameters




### -param DestinationString [in, out]

A pointer to a <b>UNICODE_STRING</b> structure. This structure includes a buffer that, on input, contains a destination string to which the source string will be concatenated. On output, this buffer is the destination buffer that contains the entire resultant string. The source string is added to the end of the destination string. The maximum number of characters in the structure's string buffer is NTSTRSAFE_UNICODE_STRING_MAX_CCH.


### -param SourceString [in]

A pointer to a <b>UNICODE_STRING</b> structure. This structure includes a buffer that contains the source string. This string will be added to the end of the destination string. The maximum number of characters in the structure's string buffer is NTSTRSAFE_UNICODE_STRING_MAX_CCH.


### -param cchToAppend [in]

The maximum number of characters to append to the string that the <i>DestinationString</i> parameter describes.


## -returns


<b>RtlUnicodeStringCchCatN</b> returns one of the following NTSTATUS values. 
<table>
<tr>
<th>Return code</th>
<th>Description</th>
</tr>
<tr>
<td width="40%">
<dl>
<dt><b>STATUS_SUCCESS</b></dt>
</dl>
</td>
<td width="60%">
This <i>success</i> status means that source data was present, the strings were concatenated without truncation, and the resultant destination buffer is null-terminated.

</td>
</tr>
<tr>
<td width="40%">
<dl>
<dt><b>STATUS_BUFFER_OVERFLOW</b></dt>
</dl>
</td>
<td width="60%">
This <i>warning</i> status means that the concatenated operation did not complete because of insufficient buffer space. The destination buffer contains a truncated, null-terminated version of the intended result.

</td>
</tr>
<tr>
<td width="40%">
<dl>
<dt><b>STATUS_INVALID_PARAMETER</b></dt>
</dl>
</td>
<td width="60%">
This <i>error</i> status means that the function received an invalid input parameter. For more information, see the following list.

</td>
</tr>
</table> 

<b>RtlUnicodeStringCchCatN</b> returns the STATUS_INVALID_PARAMETER value when one of the following occurs:
<ul>
<li>The contents of the <b>UNICODE_STRING</b> structure are invalid.</li>
<li>The destination buffer is already full.</li>
<li>A buffer pointer is <b>NULL</b>.</li>
<li>The destination buffer's length is zero, but a nonzero length source string is present.</li>
<li>The <i>cchToAppend</i> parameter's value is greater than NTSTRSAFE_UNICODE_STRING_MAX_CCH.</li>
</ul>For information about how to test NTSTATUS values, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff565436">Using NTSTATUS Values</a>.



## -remarks


The <b>RtlUnicodeStringCchCatN</b> function uses the destination buffer's size to ensure that the concatenation operation does not write past the end of the buffer. The function does <u>not</u> terminate the resultant string with a null character value (that is, with zero).

If the source and destination strings overlap, the behavior of the function is undefined.

The <i>SourceString</i> and <i>DestinationString</i> pointers cannot be <b>NULL</b>. If you need to handle <b>NULL</b> pointer values, use the <a href="..\ntstrsafe\nf-ntstrsafe-rtlunicodestringcchcatnex.md">RtlUnicodeStringCchCatNEx</a> function.

For more information about the safe string functions, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff565508">Using Safe String Functions</a>. 



## -see-also

<a href="..\ntstrsafe\nf-ntstrsafe-rtlunicodestringcchcatnex.md">RtlUnicodeStringCchCatNEx</a>

<a href="..\ntstrsafe\nf-ntstrsafe-rtlunicodestringcbcatn.md">RtlUnicodeStringCbCatN</a>

<a href="..\wudfwdm\ns-wudfwdm-_unicode_string.md">UNICODE_STRING</a>

 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20RtlUnicodeStringCchCatN function%20 RELEASE:%20(1/4/2018)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
