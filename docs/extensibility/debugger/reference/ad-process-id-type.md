---
description: AD_PROCESS_ID yapısındaki bir işlem KIMLIĞININ nasıl yorumlanacağını belirtir.
title: AD_PROCESS_ID_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AD_PROCESS_ID_TYPE
helpviewer_keywords:
- AD_PROCESS_ID_TYPE enumeration
ms.assetid: 0aab80e9-285a-4697-94ac-c864d42a6aaa
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f56ca1db0462a85bd68b193147f5dd3a46c6bee9
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164350"
---
# <a name="ad_process_id_type"></a>AD_PROCESS_ID_TYPE
[AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) yapısındaki BIR işlem kimliğinin nasıl yorumlanacağını belirtir.

## <a name="syntax"></a>Syntax

```cpp
enum enum_AD_PROCESS_ID {
    AD_PROCESS_ID_SYSTEM = 0,
    AD_PROCESS_ID_GUID   = 1
};
typedef DWORD AD_PROCESS_ID_TYPE;
```

```csharp
public enum enum_AD_PROCESS_ID {
    AD_PROCESS_ID_SYSTEM = 0,
    AD_PROCESS_ID_GUID   = 1
};
```

## <a name="fields"></a>Alanlar
`AD_PROCESS_ID_SYSTEM`\
İşlem KIMLIĞI bir sistem tanımlayıcısıdır. `ProcessId.dwProcessId` [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) yapısının alanını kullanın.

`AD_PROCESS_ID_GUID`\
İşlem KIMLIĞI bir GUID 'dir. `ProcessId.guidProcessId`Yapının alanını kullanın `AD_PROCESS_ID` .

## <a name="remarks"></a>Açıklamalar
`ProcessIdType`Yapıda bulunan Işlem kimliği türünü tanımlamak için [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) yapısının üyesi için kullanılır. Yapıdaki birleşimin nasıl yorumlanacağını belirler `ProcessId` .

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg. h

Ad alanı: Microsoft. VisualStudio. Debugger. Interop

Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
