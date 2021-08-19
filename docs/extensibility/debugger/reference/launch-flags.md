---
description: Hata ayıklama başlatma bayraklarını belirtir.
title: LAUNCH_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- LAUNCH_FLAGS
helpviewer_keywords:
- LAUNCH_FLAGS enumeration
ms.assetid: f51aab02-d257-4302-bb79-b7d8ba9ac4e5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6cd77725906a2780f9345bb4c64131ad943e8ceb
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122118144"
---
# <a name="launch_flags"></a>LAUNCH_FLAGS
Hata ayıklama başlatma bayraklarını belirtir.

## <a name="syntax"></a>Syntax

```cpp
enum enum_LAUNCH_FLAGS {
    LAUNCH_DEBUG      = 0x0000,
    LAUNCH_NODEBUG    = 0x0001,
    LAUNCH_ENABLE_ENC = 0x0002,
    LAUNCH_MERGE_ENV  = 0x0004
};
typedef DWORD LAUNCH_FLAGS;
```

```csharp
public enum enum_LAUNCH_FLAGS {
    LAUNCH_DEBUG      = 0x0000,
    LAUNCH_NODEBUG    = 0x0001,
    LAUNCH_ENABLE_ENC = 0x0002,
    LAUNCH_MERGE_ENV  = 0x0004
};
```

## <a name="fields"></a>Alanlar
`LAUNCH_DEBUG`\
Hata ayıklama işlemini başlatıyor.

`LAUNCH_NODEBUG`\
Hata ayıklamadan işlemi başlatıyor.

`LAUNCH_ENABLE_ENC`\
KULLANILANDIRILDI, KULLANILANDIRMADI.

`LAUNCH_MERGE_ENV`\
Işlemi başlatıyor ve ortamı başlatan konakla birleşiyor.

## <a name="remarks"></a>Açıklamalar
Bu değerler [LaunchSuspended yöntemine bağımsız değişken olarak](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) geçirildi.

Bu bayraklar bit olarak birleştirilmiş `OR` olabilir.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg.h

Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
