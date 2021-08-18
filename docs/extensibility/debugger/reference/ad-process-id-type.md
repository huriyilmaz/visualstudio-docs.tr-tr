---
description: İşlem kimliğinin bir işlem yapısında nasıl yorumlan AD_PROCESS_ID belirtir.
title: AD_PROCESS_ID_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AD_PROCESS_ID_TYPE
helpviewer_keywords:
- AD_PROCESS_ID_TYPE enumeration
ms.assetid: 0aab80e9-285a-4697-94ac-c864d42a6aaa
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 97187d49f73e53967ad172406d22073341822fbf
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122120536"
---
# <a name="ad_process_id_type"></a>AD_PROCESS_ID_TYPE
İşlem kimliğinin bir işlem yapısında nasıl [yorumlan AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) belirtir.

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
İşlem Kimliği bir sistem tanımlayıcısıdır. Kaynak `ProcessId.dwProcessId` yapısının [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) kullanın.

`AD_PROCESS_ID_GUID`\
İşlem Kimliği bir GUID'tir. Yapının `ProcessId.guidProcessId` alanını `AD_PROCESS_ID` kullanın.

## <a name="remarks"></a>Açıklamalar
Yapının `ProcessIdType` üyesi AD_PROCESS_ID [](../../../extensibility/debugger/reference/ad-process-id.md) yapısında yer alan işlem kimliğini tanımlamak için kullanılır. Yapıda birlikteliği `ProcessId` yorumlamayı belirler.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg.h

Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
