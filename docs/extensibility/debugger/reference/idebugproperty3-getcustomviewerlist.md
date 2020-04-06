---
title: IDebugProperty3::GetCustomViewerList | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::GetCustomViewerList
helpviewer_keywords:
- IDebugProperty3::GetCustomViewerList
ms.assetid: 74490fd8-6f44-4618-beea-dab64961bb8a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 212f8d251232d35ee7d9cc46074a21239eea29f4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721164"
---
# <a name="idebugproperty3getcustomviewerlist"></a>IDebugProperty3::GetCustomViewerList
Bu özellik ile ilişkili özel görüntüleyenlerin listesini alır.

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
[içinde] Atlayacak izleyici sayısı.

`celtRequested`\
[içinde] Alınacak izleyici sayısı `rgViewers` (dizinin boyutunu da belirtir).

`rgViewers`\
[içinde, dışarı] Doldurulacak [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) yapıları dizisi.

`pceltFetched`\
[çıkış] Gerçek izleyici sayısı döndürülür.

## <a name="return-value"></a>Dönüş Değeri
Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
Tür görselleştiricilerini desteklemek için, bu yöntem aramayı [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) yöntemine ileter. İfade değerlendiricisi, bu özelliğin türü için özel görüntüleyenleri de destekliyorsa, bu yöntem listeye uygun özel görüntüleyenleri ekleyebilir.

Tür görselleştiricileri ve özel görüntüleyenler arasındaki farklar hakkında ayrıntılar için [Type Visualizer](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) ve Custom Viewer'a bakın.

## <a name="example"></a>Örnek
Aşağıdaki örnek, [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) arabirimini ortaya çıkaran bir **CProperty** nesnesi için bu yöntemin nasıl uygulanacağını gösterir.

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
