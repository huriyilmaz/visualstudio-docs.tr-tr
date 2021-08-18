---
description: Belirli bir makine için ne tür bilgilerin alın olduğunu belirtir.
title: MACHINE_INFO_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MACHINE_INFO_FIELDS
helpviewer_keywords:
- MACHINE_INFO_FIELDS enumeration
ms.assetid: 2d61d206-7d40-4df1-8c88-1b3c9c78821e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 448edb134ba6065c85ee1547c73f45f9df769563
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122103149"
---
# <a name="machine_info_fields"></a>MACHINE_INFO_FIELDS
Belirli bir makine için ne tür bilgilerin alın olduğunu belirtir.

## <a name="syntax"></a>Syntax

```cpp
enum enum_MACHINE_INFO_FIELDS { 
   MCIF_NAME  = 0x00000001,
   MCIF_FLAGS = 0x00000002,
   MCIF_ALL   = 0x00000003
};
typedef DWORD MACHINE_INFO_FIELDS;
```

```csharp
public enum enum_MACHINE_INFO_FIELDS { 
   MCIF_NAME  = 0x00000001,
   MCIF_FLAGS = 0x00000002,
   MCIF_ALL   = 0x00000003
};
```

## <a name="fields"></a>Alanlar
 `MCIF_NAME`\
 Yapıda alanını `bstrName` başlatma/kullanma.

 `MCIF_FLAGS`\
 Yapıda alanını `Flags` başlatma/kullanma.

 `MIF_ALL`\
 Yapıda tüm alanları başlat/kullan.

## <a name="remarks"></a>Açıklamalar
 Bu değerler, MACHINE_INFO yapısının hangi üyelerinin başlat olacağını [belirtmek için](../../../extensibility/debugger/reference/machine-info.md) [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md) yöntemine geçirildi.

 Ayrıca, kullanılan `Fields` ve geçerli olan alanları belirtmek için `MACHINE_INFO` yapının üyesinde kullanılır.

 Bu bayraklar bit olarak birleştirilmiş `OR` olabilir.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md)
- [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)
