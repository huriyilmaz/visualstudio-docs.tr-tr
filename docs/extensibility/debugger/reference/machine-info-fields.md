---
title: MACHINE_INFO_FIELDS | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MACHINE_INFO_FIELDS
helpviewer_keywords:
- MACHINE_INFO_FIELDS enumeration
ms.assetid: 2d61d206-7d40-4df1-8c88-1b3c9c78821e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 89a2552bb6a8bea88f54a897b829ab89b30ff413
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714518"
---
# <a name="machine_info_fields"></a>MACHINE_INFO_FIELDS
Belirli bir makine için ne tür bilgiler alıncaya kadar bilgi alınmasını belirtir.

## <a name="syntax"></a>Sözdizimi

```cpp
enum enum_MACHINE_INFO_FIELDS { 
   MCIF_NAME  = 0x00000001,
   MCIF_FLAGS = 0x00000002,
   MCIF_ALL   = 0x00000003
};
typedef DWORD MACHINE_INFO_FIELDS;
```

```csharp
public enum enum_MACHINE_INFO_FIELDS { 
   MCIF_NAME  = 0x00000001,
   MCIF_FLAGS = 0x00000002,
   MCIF_ALL   = 0x00000003
};
```

## <a name="fields"></a>Alanlar
 `MCIF_NAME`\
 Yapıdaki `bstrName` alanı başlatma/kullanma.

 `MCIF_FLAGS`\
 Yapıdaki `Flags` alanı başlatma/kullanma.

 `MIF_ALL`\
 Yapıdaki tüm alanların başlatılması/kullanılması.

## <a name="remarks"></a>Açıklamalar
 Bu değerler, [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md) yapının hangi üyelerinin baş harfe alınmasını göstermek için [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md) yöntemine aktarılır.

 Ayrıca `MACHINE_INFO` yapının `Fields` üyesi hangi alanların kullanıldığını ve geçerli olduğunu belirtmek için kullanılır.

 Bu bayraklar biraz ile `OR`birleştirilebilir.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Numaralandırma](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md)
- [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)
