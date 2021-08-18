---
description: Bu özellikle ilişkili özel görüntüleyicilerin listesini alır.
title: IDebugProperty3::GetCustomViewerList | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::GetCustomViewerList
helpviewer_keywords:
- IDebugProperty3::GetCustomViewerList
ms.assetid: 74490fd8-6f44-4618-beea-dab64961bb8a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9f8abc55fe52c48c20979f509bf626e1be697bb5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122063908"
---
# <a name="idebugproperty3getcustomviewerlist"></a>IDebugProperty3::GetCustomViewerList
Bu özellikle ilişkili özel görüntüleyicilerin listesini alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetCustomViewerList(
    ULONG                celtSkip,
    ULONG                celtRequested,
    DEBUG_CUSTOM_VIEWER* rgViewers,
    ULONG*               pceltFetched
);
```

```csharp
int GetCustomViewerList(
    uint                  celtSkip,
    uint                  celtRequested,
    DEBUG_CUSTOM_VIEWER[] rgViewers,
    out uint              pceltFetched
);
```

## <a name="parameters"></a>Parametreler
`celtSkip`\
[in] Atılacak izleyici sayısı.

`celtRequested`\
[in] Alınacak görüntüleyici sayısı (dizinin boyutunu da `rgViewers` belirtir).

`rgViewers`\
[in, out] Doldurulması [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) yapı dizisi.

`pceltFetched`\
[out] Döndürülen gerçek görüntüleyici sayısı.

## <a name="return-value"></a>Dönüş Değeri
Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
Tür görselleştiricileri desteklemek için bu yöntem çağrıyı [GetCustomViewerList yöntemine](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) iletir. İfade değerlendirici bu özelliğin türü için özel görüntüleyicileri de destekliyorsa, bu yöntem uygun özel görüntüleyicileri listeye ekleyebilirsiniz.

Tür [görselleştiricileri ile özel görüntüleyiciler arasındaki](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) farklar hakkında ayrıntılı bilgi için bkz. Tür Görselleştiricisi ve Özel Görüntüleyici.

## <a name="example"></a>Örnek
Aşağıdaki örnek, [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) arabirimini ortaya çıkaran **bir CProperty** nesnesi için bu yöntemin nasıl uygulandığını gösterir.

```cpp
STDMETHODIMP CProperty::GetCustomViewerList(ULONG celtSkip, ULONG celtRequested, DEBUG_CUSTOM_VIEWER* prgViewers, ULONG* pceltFetched)
{
    if (NULL == prgViewers)
    {
        return E_POINTER;
    }

    if (GetVisualizerService())
    {
        return m_pIEEVisualizerService->GetCustomViewerList(celtSkip, celtRequested, prgViewers, pceltFetched);
    }
    else
    {
        return E_NOTIMPL;
    }
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)
- [Tür Görselleştiricisi ve Özel Görüntüleyici](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
