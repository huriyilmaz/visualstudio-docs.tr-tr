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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7e53cb955cda833d2172ed369e5573f257082b08
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102225532"
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
Hata ayıklama işlemini başlatır.

`LAUNCH_NODEBUG`\
İşlemi hata ayıklamadan başlatır.

`LAUNCH_ENABLE_ENC`\
KULLANıM DıŞı, KULLANMAYıN.

`LAUNCH_MERGE_ENV`\
İşlemi başlatır ve ortamı Başlatan ana bilgisayarla birleştirir.

## <a name="remarks"></a>Açıklamalar
Bu değerler, [Launchaskıya alındı](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) yöntemine bir bağımsız değişken olarak geçirilir.

Bu bayraklar bit düzeyinde birleştirilebilir `OR` .

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg. h

Ad alanı: Microsoft. VisualStudio. Debugger. Interop

Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
