---
title: ATTACH_REASON | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ATTACH_REASON
helpviewer_keywords:
- ATTACH_REASON enumeration
ms.assetid: 159fb70b-a344-4ba6-9115-b7eaa16e228f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ca871d9dac2b6f37018af925eece5c1a6f3d1585
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738132"
---
# <a name="attach_reason"></a>ATTACH_REASON
Hata ayıklama altyapısının (DE) bir program düğümüne iliştirme nedenini belirtir.

## <a name="syntax"></a>Syntax

```cpp
enum enum_ATTACH_REASON {
    ATTACH_REASON_LAUNCH = 0x0001,
    ATTACH_REASON_USER   = 0x0002,
    ATTACH_REASON_AUTO   = 0x0003
};
typedef DWORD ATTACH_REASON;
```

```csharp
public enum enum_ATTACH_REASON {
    ATTACH_REASON_LAUNCH = 0x0001,
    ATTACH_REASON_USER   = 0x0002,
    ATTACH_REASON_AUTO   = 0x0003
};
```

## <a name="fields"></a>Alanlar
`ATTACH_REASON_AUTO`\
İşlem şu anda hata ayıklama modunda olduğundan iliştirme.

`ATTACH_REASON_LAUNCH`\
İşlem başlatıldığından iliştirme.

`ATTACH_REASON_USER`\
Kullanıcı isteği nedeniyle iliştirme.

## <a name="remarks"></a>Açıklamalar
Bu değerler, [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) ve [Attach](../../../extensibility/debugger/reference/idebugprogramex2-attach.md) yöntemlerine parametre olarak kullanılır.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg. h

Ad alanı: Microsoft. VisualStudio. Debugger. Interop

Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Numaralandırmalar](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [İliştir](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [İliştir](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)
