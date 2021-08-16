---
description: Hata ayıklama modülü bilgileri için bayrakları belirtir.
title: MODULE_INFO_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_INFO_FIELDS
helpviewer_keywords:
- MODULE_INFO_FIELDS enumeration
ms.assetid: 8bed85f4-235f-4192-b58f-5fad7a4d7a78
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: abdd04428695e105b7e9f3e14e740beef3a347574171296768af9a9637eaa592
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121415287"
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
 Yapıda alanların hiçbirini başlatma/kullanma.

 `MIF_NAME`\
 Çalışma alanı `m_bstrName` yapısında alanı [MODULE_INFO.](../../../extensibility/debugger/reference/module-info.md)

 `MIF_URL`\
 Yapıda alanını `m_bstrUrl` `MODULE_INFO` başlatma/kullanma.

 `MIF_VERSION`\
 Yapıda alanını `m_bstrVersion` `MODULE_INFO` başlatma/kullanma.

 `MIF_DEBUGMESSAGE`\
 Yapıda alanını `m_bstrDebugMessage` `MODULE_INFO` başlatma/kullanma.

 `MIF_LOADADDRESS`\
 Yapıda alanını `m_addrLoadAddress` `MODULE_INFO` başlatma/kullanma.

 `MIF_PREFFEREDADDRESS`\
 Yapıda alanını `m_addrPreferredLoadAddress` `MODULE_INFO` başlatma/kullanma.

 `MIF_SIZE`\
 Yapıda alanını `m_dwSize` `MODULE_INFO` başlatma/kullanma.

 `MIF_LOADORDER`\
 Yapıda alanını `m_dwLoadOrder` `MODULE_INFO` başlatma/kullanma.

 `MIF_TIMESTAMP`\
 Yapıda alanını `m_TimeStamp` `MODULE_INFO` başlatma/kullanma.

 `MIF_URLSYMBOLLOCATION`\
 Yapıda alanını `m_bstrUrlSymbolLocation` `MODULE_INFO` başlatma/kullanma.

 `MIF_FLAGS`\
 Yapıda alanını `m_dwModuleFlags` `MODULE_INFO` başlatma/kullanma.

 `MIF_ALLFIELDS`\
 Yapıda tüm alanları `MODULE_INFO` başlat/kullan.

## <a name="remarks"></a>Açıklamalar
 Bu değerler, MODULE_INFO yapısının hangi alanlarının başlat olacağını belirtmek [için](../../../extensibility/debugger/reference/module-info.md) [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) yöntemine bağımsız değişken olarak geçirebilirsiniz.

 Bu değerler, kullanılan ve geçerli `MODULE_INFO` olan alanları belirtmek için yapıda da kullanılır.

 Bu bayraklar bit olarak birleştirilmiş `OR` olabilir.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)
