---
description: Hata ayıklama altyapısının (DE) bir program düğümüne iliştirme nedenini belirtir.
title: ATTACH_REASON | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ATTACH_REASON
helpviewer_keywords:
- ATTACH_REASON enumeration
ms.assetid: 159fb70b-a344-4ba6-9115-b7eaa16e228f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2d47b655767815d8d15292f9fc5591a5ddd97808
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122057830"
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
İşlem şu anda hata ayıklama modunda olduğundan iliştirin.

`ATTACH_REASON_LAUNCH`\
ekleme işlemi başlatıldı.

`ATTACH_REASON_USER`\
Bir kullanıcı isteği nedeniyle iliştirin.

## <a name="remarks"></a>Açıklamalar
Bu değerler Attach ve Attach metotları [için](../../../extensibility/debugger/reference/idebugengine2-attach.md) parametre [olarak](../../../extensibility/debugger/reference/idebugprogramex2-attach.md) kullanılır.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg.h

Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [İliştir](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [İliştir](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)
