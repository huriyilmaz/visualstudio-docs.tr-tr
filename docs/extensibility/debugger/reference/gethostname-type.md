---
description: Konak adının türünü belirtir.
title: GETHOSTNAME_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- GETHOSTNAME_TYPE
helpviewer_keywords:
- GETHOSTNAME_TYPE enumeration
ms.assetid: 2be92bea-8133-412b-9015-1833baf16e1b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d16e9b2ce7e8320aeba97856f9beb883ffd5fe5d2504adbff64336007144d655
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121293293"
---
# <a name="gethostname_type"></a>GETHOSTNAME_TYPE
Konak adının türünü belirtir.

## <a name="syntax"></a>Syntax

```cpp
enum enum_GETHOSTNAME_TYPE {
    GHN_FRIENDLY_NAME = 0,
    GHN_FILE_NAME     = 1
};
typedef DWORD GETHOSTNAME_TYPE;
```

```csharp
public enum enum_GETHOSTNAME_TYPE {
    GHN_FRIENDLY_NAME = 0,
    GHN_FILE_NAME     = 1
};
```

## <a name="fields"></a>Alanlar
`GHN_FRIENDLY_NAME`\
Ana bilgisayarın kolay adını belirtir.

`GHN_FILE_NAME`\
Ana bilgisayarın dosya adını belirtir.

## <a name="remarks"></a>Açıklamalar
Bu değerler, farklı biçimlerde bir konak adı almak için [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md) yöntemine bağımsız değişken olarak geçirilebilir.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg.h

Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)
