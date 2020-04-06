---
title: DEBUG_CUSTOM_VIEWER | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_CUSTOM_VIEWER
helpviewer_keywords:
- DEBUG_CUSTOM_VIEWER structure
ms.assetid: 8e0ef3f0-0107-48e8-a037-6e52b4c4ed9d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3de9b8f7ef30cffbdd78399dc831060e413ba51b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737539"
---
# <a name="debug_custom_viewer"></a>DEBUG_CUSTOM_VIEWER
Özel bir görüntüleyici veya yazı görselleştiricisi tanımlayan bir yapı.

## <a name="syntax"></a>Sözdizimi

```cpp
typedef struct tagDEBUG_CUSTOM_VIEWER {
    DWORD dwID;
    BSTR  bstrMenuName;
    BSTR  bstrDescription;
    GUID  guidLang;
    GUID  guidVendor;
    BSTR  bstrMetric;
} DEBUG_CUSTOM_VIEWER;
```

```csharp
public struct DEBUG_CUSTOM_VIEWER {
    public uint   dwID;
    public string bstrMenuName;
    public string bstrDescription;
    public Guid   guidLang;
    public Guid   guidVendor;
    public string bstrMetric;
};
```

## <a name="members"></a>Üyeler
`dwID`\
Birden çok görüntüleyeni veya görüntüleyicileri `GUID`ayırt etmek için bir kimlik.

`bstrMenuName`\
Açılan menüde görünecek metin.

`bstrDescription`\
Özel görüntüleyici veya tür görselleştiriciaçıklaması (kullanılmadığı takdirde null değeri olmalıdır).

`guidLang`\
Sağlayan ifade değerlendiricinin dili.

`guidVendor`\
Sağlayan ifade değerlendiricinin satıcısı.

`bstrMetric`\
Özel görüntüleyicinin veya yazı görselleştiricisinin `CLSID` depolandığı metrik.

## <a name="remarks"></a>Açıklamalar
Bu yapının listesi [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) yöntemine (ve eklentide [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) yöntemine) yapılan bir çağrıyla döndürülür.

## <a name="requirements"></a>Gereksinimler
Üstbilgi: msdbg.h

Ad alanı: Microsoft.VisualStudio.Debugger.Interop

Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)
