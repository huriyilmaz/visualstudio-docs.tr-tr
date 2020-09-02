---
title: DISASSEMBLY_STREAM_FIELDS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- DISASSEMBLY_STREAM_FIELDS
helpviewer_keywords:
- DISASSEMBLY_STREAM_FIELDS enumeration
ms.assetid: cfc9b4de-c756-4844-bea7-d9f186a51d1b
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b67ccf926267e3475a43d7f09bf3ccb361dc8484
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68159302"
---
# <a name="disassembly_stream_fields"></a>DISASSEMBLY_STREAM_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ayrıştırılmış bir alan hakkında hangi bilgilerin alınması gerektiğini belirtir.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum enum_DISASSEMBLY_STREAM_FIELDS {   
   DSF_ADDRESS          = 0x00000001,  
   DSF_ADDRESSOFFSET    = 0x00000002,  
   DSF_CODEBYTES        = 0x00000004,  
   DSF_OPCODE           = 0x00000008,  
   DSF_OPERANDS         = 0x00000010,  
   DSF_SYMBOL           = 0x00000020,  
   DSF_CODELOCATIONID   = 0x00000040,  
   DSF_POSITION         = 0x00000080,  
   DSF_DOCUMENTURL      = 0x00000100,  
   DSF_BYTEOFFSET       = 0x00000200,  
   DSF_FLAGS            = 0x00000400,  
   DSF_OPERANDS_SYMBOLS = 0x00010000,  
   DSF_ALL              = 0x000107ff  
};  
typedef DWORD DISASSEMBLY_STREAM_FIELDS;  
```  
  
```csharp  
public enum enum_DISASSEMBLY_STREAM_FIELDS {   
   DSF_ADDRESS          = 0x00000001,  
   DSF_ADDRESSOFFSET    = 0x00000002,  
   DSF_CODEBYTES        = 0x00000004,  
   DSF_OPCODE           = 0x00000008,  
   DSF_OPERANDS         = 0x00000010,  
   DSF_SYMBOL           = 0x00000020,  
   DSF_CODELOCATIONID   = 0x00000040,  
   DSF_POSITION         = 0x00000080,  
   DSF_DOCUMENTURL      = 0x00000100,  
   DSF_BYTEOFFSET       = 0x00000200,  
   DSF_FLAGS            = 0x00000400,  
   DSF_OPERANDS_SYMBOLS = 0x00010000,  
   DSF_ALL              = 0x000107ff  
};  
```  
  
## <a name="members"></a>Üyeler  
 DSF_ADDRESS  
 Alanı başlatın/kullanın `bstrAddress` .  
  
 DSF_ADDRESSOFFSET  
 Alanı başlatın/kullanın `bstrAddressOffset` .  
  
 DSF_CODEBYTES  
 Alanı başlatın/kullanın `bstrCodeBytes` .  
  
 DSF_OPCODE  
 Alanı başlatın/kullanın `bstrOpCode` .  
  
 DSF_OPERANDS  
 Alanı başlatın/kullanın `bstrOperands` .  
  
 DSF_SYMBOL  
 Alanı başlatın/kullanın `bstrSymbol` .  
  
 DSF_CODELOCATIONID  
 Alanı başlatın/kullanın `uCodeLocationId` .  
  
 DSF_POSITION  
 Ve alanlarını başlatın/ `posBeg` kullanın `posEnd` .  
  
 DSF_DOCUMENTURL  
 Alanı başlatın/kullanın `bstrDocumentUrl` .  
  
 DSF_BYTEOFFSET  
 Alanı başlatın/kullanın `dwByteOffset` .  
  
 DSF_FLAGS  
 `dwFlags`([DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)) alanını başlatın/kullanın.  
  
 DSF_OPERANDS_SYMBOLS  
 Alana sembol adlarını ekleyin `bstrOperands` .  
  
 DSF_ALL  
 Ayrıştırılmış akış için tüm alanları belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) yapısının hangi alanlarının başlatıldığını göstermek için [Read](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) yöntemine bir parametre olarak geçirilir.  
  
 Yapı öğesi için, `dwFields` `DisassemblyData` Yapı döndürüldüğünde hangi alanların kullanıldığını ve geçerli olduğunu göstermek için kullanılır.  
  
 Bu değerler, bit düzeyinde birleştirilebilir `OR` .  
  
## <a name="requirements"></a>Gereksinimler  
 Üst bilgi: msdbg. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Numaralandırmalar](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)   
 [Okuyamaz](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)   
 [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)
