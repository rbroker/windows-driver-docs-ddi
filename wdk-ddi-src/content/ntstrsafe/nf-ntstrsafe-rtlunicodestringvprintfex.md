---
UID: NF:ntstrsafe.RtlUnicodeStringVPrintfEx
title: RtlUnicodeStringVPrintfEx function
author: windows-driver-content
description: The RtlUnicodeStringVPrintfEx function creates a text string, with formatting that is based on supplied formatting information, and stores the string in a UNICODE_STRING structure.
old-location: kernel\rtlunicodestringvprintfex.htm
old-project: kernel
ms.assetid: da14f93d-c3db-4c54-8378-7492b79a5e18
ms.author: windowsdriverdev
ms.date: 1/4/2018
ms.keywords: RtlUnicodeStringVPrintfEx function [Kernel-Mode Driver Architecture], ntstrsafe/RtlUnicodeStringVPrintfEx, kernel.rtlunicodestringvprintfex, safestrings_293f1ca7-b9e4-4502-9d04-e656bac17288.xml, RtlUnicodeStringVPrintfEx
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: function
req.header: ntstrsafe.h
req.include-header: Ntstrsafe.h
req.target-type: Desktop
req.target-min-winverclnt: Available starting with Windows XP with Service Pack 1 (SP1).
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
-	RtlUnicodeStringVPrintfEx
product: Windows
targetos: Windows
req.typenames: *PBATTERY_REPORTING_SCALE, BATTERY_REPORTING_SCALE
---

# RtlUnicodeStringVPrintfEx function


## -description


The <b>RtlUnicodeStringVPrintfEx</b> function creates a text string, with formatting that is based on supplied formatting information, and stores the string in a <a href="..\wudfwdm\ns-wudfwdm-_unicode_string.md">UNICODE_STRING</a> structure.


## -syntax


````
NTSTATUS RtlUnicodeStringVPrintfEx(
  _Out_     PUNICODE_STRING  DestinationString,
  _Out_opt_ PUNICODE_STRING  RemainingString,
  _In_      DWORD            dwFlags,
  _In_      NTSTRSAFE_PCWSTR pszFormat,
  _In_      va_list          argList
);
````


## -parameters




### -param DestinationString [out]

Optional. A pointer to a <b>UNICODE_STRING</b> structure that receives a formatted string. <b>RtlUnicodeStringVPrintfEx</b> creates this string from the formatting string that <i>pszFormat</i> supplies and the function's argument list. The maximum number of characters in the string is NTSTRSAFE_UNICODE_STRING_MAX_CCH. <i>DestinationString</i> can be <b>NULL</b>, but only if STRSAFE_IGNORE_NULLS is set in <i>dwFlags</i>.


### -param RemainingString [out, optional]

Optional. If the caller supplies a non-<b>NULL</b> pointer to a <b>UNICODE_STRING</b> structure, <b>RtlUnicodeStringVPrintfE</b> sets this structure's <b>Buffer</b> member to the end of the formatted string, sets the structure's <b>Length</b> member to zero, and sets the structure's <b>MaximumLength</b> member to the number of bytes that are remaining in the destination buffer. <i>RemainingString</i> can be <b>NULL</b>, but only if STRSAFE_IGNORE_NULLS is set in <i>dwFlags</i>.


### -param dwFlags [in]

One or more flags and, optionally, a fill byte. The flags are defined as follows:




### -param pszFormat [in]

A pointer to a nul-terminated text string that contains <b>printf</b>-styled formatting directives. This pointer can be <b>NULL</b>, but only if STRSAFE_IGNORE_NULLS is set in <i>dwFlags</i>.


### -param argList [in]

A <b>va_list</b>-typed argument list. Arguments in this argument list will be interpreted by the using formatting string that <i>pszFormat</i> supplies.


##### - dwFlags.STRSAFE_FILL_BEHIND

If this flag is set and the function succeeds, the low byte of <i>dwFlags</i> is used to fill the portion of the destination buffer that follows the last character in the string.


##### - dwFlags.STRSAFE_IGNORE_NULLS

If this flag is set, the source or destination pointer, or both, can be <b>NULL</b>. <b>RtlUnicodeStringVPrintfEx</b> treats <b>NULL</b> source buffer pointers like empty strings (TEXT("")), which can be copied. <b>NULL</b> destination buffer pointers cannot receive nonempty strings.


##### - dwFlags.STRSAFE_NULL_ON_FAILURE

If this flag is set and the function fails, the destination buffer is set to an empty string (TEXT("")). This operation overwrites any preexisting buffer contents.


##### - dwFlags.STRSAFE_ZERO_LENGTH_ON_FAILURE

If this flag is set and the function returns STATUS_BUFFER_OVERFLOW, the destination string length is set to zero bytes.


##### - dwFlags.STRSAFE_FILL_ON_FAILURE

If this flag is set and the function fails, the low byte of <i>dwFlags</i> is used to fill the entire destination buffer. This operation overwrites any preexisting buffer contents.


##### - dwFlags.STRSAFE_NO_TRUNCATION

If this flag is set and the function returns STATUS_BUFFER_OVERFLOW, the contents of the destination buffer are not modified.


## -returns


<b>RtlUnicodeStringVPrintfEx</b> returns one of the following NTSTATUS values. 
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
This <i>success</i> status means source data was present, and the strings were concatenated without truncation.

</td>
</tr>
<tr>
<td width="40%">
<dl>
<dt><b>STATUS_BUFFER_OVERFLOW</b></dt>
</dl>
</td>
<td width="60%">
This <i>warning</i> status means the copy operation did not complete due to insufficient space in the destination buffer. If STRSAFE_NO_TRUNCATION is set in <i>dwFlags</i>, the destination buffer is not modified. If the flag is not set, the destination buffer contains a truncated version of the copied string.

</td>
</tr>
<tr>
<td width="40%">
<dl>
<dt><b>STATUS_INVALID_PARAMETER</b></dt>
</dl>
</td>
<td width="60%">
This <i>error</i> status means the function received an invalid input parameter. For more information, see the following paragraph.

</td>
</tr>
</table> 

<b>RtlUnicodeStringVPrintfEx</b> returns the STATUS_INVALID_PARAMETER value when one of the following occurs:
<ul>
<li>The contents of a <b>UNICODE_STRING</b> structure are invalid.</li>
<li>An invalid flag is specified in <i>dwFlags</i>.</li>
<li>The destination buffer is already full.</li>
<li>A buffer pointer is <b>NULL</b> and the STRSAFE_IGNORE_NULLS flag is not specified in <i>dwFlags</i>.</li>
<li>The destination buffer pointer is <b>NULL</b>, but the buffer size is not zero.</li>
<li>The destination buffer pointer is <b>NULL</b>, or its length is zero, but a nonzero length source string is present.</li>
</ul>For information about how to test NTSTATUS values, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff565436">Using NTSTATUS Values</a>.



## -remarks


The <b>RtlUnicodeStringVPrintfEx</b> function uses the destination buffer's size to ensure that the string formatting operation does not write past the end of the buffer. By default, the function does <u>not</u> terminate the resultant string with a null character value (that is, with zero). As an option, the caller can use the STRSAFE_FILL_BEHIND flag and a fill byte value of zero to null-terminate a resultant string that does not occupy the entire destination buffer.

<b>RtlUnicodeStringVPrintfEx</b> adds to the functionality of the <a href="..\ntstrsafe\nf-ntstrsafe-rtlunicodestringvprintf.md">RtlUnicodeStringVPrintf</a> function by returning a <a href="..\wudfwdm\ns-wudfwdm-_unicode_string.md">UNICODE_STRING</a> structure that identifies the end of the destination string and the number of bytes that are left unused in that string. You can pass flags to <b>RtlUnicodeStringVPrintfEx</b> for additional control.

If the format string and the destination string overlap, the behavior of the function is undefined.

The <i>pszFormat</i> and <i>DestinationString</i> pointers cannot be <b>NULL</b> unless the STRSAFE_IGNORE_NULLS flag is set in <i>dwFlags</i>. If STRSAFE_IGNORE_NULLS is set, one or both of these pointers can be <b>NULL</b>. If the <i>DestinationString</i> pointer is <b>NULL</b>, the <i>pszFormat</i> pointer must be <b>NULL</b> or point to an empty string.

For more information about <b>va_list</b>-typed argument lists, see the Microsoft Windows SDK documentation.

For more information about the safe string functions, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff565508">Using Safe String Functions</a>.



## -see-also

<a href="..\ntstrsafe\nf-ntstrsafe-rtlunicodestringprintfex.md">RtlUnicodeStringPrintfEx</a>

<a href="..\wudfwdm\ns-wudfwdm-_unicode_string.md">UNICODE_STRING</a>

<a href="..\ntstrsafe\nf-ntstrsafe-rtlunicodestringprintf.md">RtlUnicodeStringPrintf</a>

<a href="..\ntstrsafe\nf-ntstrsafe-rtlunicodestringvprintf.md">RtlUnicodeStringVPrintf</a>

 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20RtlUnicodeStringVPrintfEx function%20 RELEASE:%20(1/4/2018)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
