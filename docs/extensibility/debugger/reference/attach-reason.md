---
title: ATTACH_REASON | Microsoft Dokümanlar
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738132"
---
# <a name="attach_reason"></a>ATTACH_REASON
Hata ayıklama altyapısının (DE) bir program düğümüne eklenmesinin nedenini belirtir.

## <a name="syntax"></a>Sözdizimi

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
İşlem şu anda hata ayıklama modunda olduğundan ekleyin.

`ATTACH_REASON_LAUNCH`\
İşlem başlatıldığı için ekle.

`ATTACH_REASON_USER`\
Kullanıcı isteği nedeniyle ekle.

## <a name="remarks"></a>Açıklamalar
Bu değerler [Ekle](../../../extensibility/debugger/reference/idebugengine2-attach.md) ve [Ekle](../../../extensibility/debugger/reference/idebugprogramex2-attach.md) yöntemlerine parametre olarak kullanılır.

## <a name="requirements"></a>Gereksinimler
Üstbilgi: msdbg.h

Ad alanı: Microsoft.VisualStudio.Debugger.Interop

Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Numaralandırma](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [İliştir](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [İliştir](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)
