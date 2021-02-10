---
title: MODULE_INFO_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_INFO_FIELDS
helpviewer_keywords:
- MODULE_INFO_FIELDS enumeration
ms.assetid: 8bed85f4-235f-4192-b58f-5fad7a4d7a78
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 116eb36cf96284698a6d93730db39bb38d22b93e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99938713"
---
# <a name="module_info_fields"></a>MODULE_INFO_FIELDS
Hata ayıklama modülü bilgileri için bayrakları belirtir.

## <a name="syntax"></a>Syntax

```cpp
enum enum_MODULE_INFO_FIELDS { 
   MIF_NONE              = 0x0000,
   MIF_NAME              = 0x0001,
   MIF_URL               = 0x0002,
   MIF_VERSION           = 0x0004,
   MIF_DEBUGMESSAGE      = 0x0008,
   MIF_LOADADDRESS       = 0x0010,
   MIF_PREFFEREDADDRESS  = 0x0020,
   MIF_SIZE              = 0x0040,
   MIF_LOADORDER         = 0x0080,
   MIF_TIMESTAMP         = 0x0100,
   MIF_URLSYMBOLLOCATION = 0x0200,
   MIF_FLAGS             = 0x0400,
   MIF_ALLFIELDS         = 0x07ff
};
typedef DWORD MODULE_INFO_FIELDS;
```

```csharp
public enum enum_MODULE_INFO_FIELDS { 
   MIF_NONE              = 0x0000,
   MIF_NAME              = 0x0001,
   MIF_URL               = 0x0002,
   MIF_VERSION           = 0x0004,
   MIF_DEBUGMESSAGE      = 0x0008,
   MIF_LOADADDRESS       = 0x0010,
   MIF_PREFFEREDADDRESS  = 0x0020,
   MIF_SIZE              = 0x0040,
   MIF_LOADORDER         = 0x0080,
   MIF_TIMESTAMP         = 0x0100,
   MIF_URLSYMBOLLOCATION = 0x0200,
   MIF_FLAGS             = 0x0400,
   MIF_ALLFIELDS         = 0x07ff
};
```

## <a name="fields"></a>Alanlar
 `MIF_NONE`\
 Yapıdaki alanların hiçbirini başlatma/kullanma.

 `MIF_NAME`\
 `m_bstrName` [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) yapısındaki alanı başlatın/kullanın.

 `MIF_URL`\
 Yapıda alanı başlatın/kullanın `m_bstrUrl` `MODULE_INFO` .

 `MIF_VERSION`\
 Yapıda alanı başlatın/kullanın `m_bstrVersion` `MODULE_INFO` .

 `MIF_DEBUGMESSAGE`\
 Yapıda alanı başlatın/kullanın `m_bstrDebugMessage` `MODULE_INFO` .

 `MIF_LOADADDRESS`\
 Yapıda alanı başlatın/kullanın `m_addrLoadAddress` `MODULE_INFO` .

 `MIF_PREFFEREDADDRESS`\
 Yapıda alanı başlatın/kullanın `m_addrPreferredLoadAddress` `MODULE_INFO` .

 `MIF_SIZE`\
 Yapıda alanı başlatın/kullanın `m_dwSize` `MODULE_INFO` .

 `MIF_LOADORDER`\
 Yapıda alanı başlatın/kullanın `m_dwLoadOrder` `MODULE_INFO` .

 `MIF_TIMESTAMP`\
 Yapıda alanı başlatın/kullanın `m_TimeStamp` `MODULE_INFO` .

 `MIF_URLSYMBOLLOCATION`\
 Yapıda alanı başlatın/kullanın `m_bstrUrlSymbolLocation` `MODULE_INFO` .

 `MIF_FLAGS`\
 Yapıda alanı başlatın/kullanın `m_dwModuleFlags` `MODULE_INFO` .

 `MIF_ALLFIELDS`\
 Yapıdaki tüm alanları başlatın/kullanın `MODULE_INFO` .

## <a name="remarks"></a>Açıklamalar
 Bu değerler, [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) yapısının hangi alanlarının başlatıldığını göstermek Için [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) yöntemine bir bağımsız değişken olarak geçirilir.

 Bu değerler, `MODULE_INFO` hangi alanların kullanıldığını ve geçerli olduğunu göstermek için yapıda de kullanılır.

 Bu bayraklar bit düzeyinde birleştirilebilir `OR` .

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)
