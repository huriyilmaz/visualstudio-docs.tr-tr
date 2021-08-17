---
description: Özel görüntüleyiciyi veya tür görselleştiriciyi tanımlayan yapı.
title: DEBUG_CUSTOM_VIEWER | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_CUSTOM_VIEWER
helpviewer_keywords:
- DEBUG_CUSTOM_VIEWER structure
ms.assetid: 8e0ef3f0-0107-48e8-a037-6e52b4c4ed9d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 683164a2a3c6e6e63d4a783d55ea481d3eb8547f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122065104"
---
# <a name="debug_custom_viewer"></a>DEBUG_CUSTOM_VIEWER
Özel görüntüleyiciyi veya tür görselleştiriciyi tanımlayan yapı.

## <a name="syntax"></a>Syntax

```cpp
typedef struct tagDEBUG_CUSTOM_VIEWER {
    DWORD dwID;
    BSTR  bstrMenuName;
    BSTR  bstrDescription;
    GUID  guidLang;
    GUID  guidVendor;
    BSTR  bstrMetric;
} DEBUG_CUSTOM_VIEWER;
```

```csharp
public struct DEBUG_CUSTOM_VIEWER {
    public uint   dwID;
    public string bstrMenuName;
    public string bstrDescription;
    public Guid   guidLang;
    public Guid   guidVendor;
    public string bstrMetric;
};
```

## <a name="members"></a>Üyeler
`dwID`\
Bir tarafından uygulanan birden çok görüntüleyiciyi veya görselleştiriciyi ayırt etmek için bir `GUID` kimlik.

`bstrMenuName`\
Açılan menüde görünecek metin.

`bstrDescription`\
Özel görüntüleyicinin veya tür görselleştiricinin açıklaması (kullanılmazsa null değer olmalıdır).

`guidLang`\
Sağlayan ifade değerlendiricinin dili.

`guidVendor`\
Sağlayan ifade değerlendiricinin satıcısı.

`bstrMetric`\
Özel görüntüleyicinin veya tür görselleştiricinin depolandığı `CLSID` ölçüm.

## <a name="remarks"></a>Açıklamalar
Bu yapının listesi [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) yöntemine (ve uzantısına göre [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) yöntemine) yapılan bir çağrı tarafından döndürülür.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg.h

Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)
