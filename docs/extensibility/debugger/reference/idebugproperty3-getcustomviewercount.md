---
title: IDebugProperty3::GetCustomViewerCount | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::GetCustomViewerCount
helpviewer_keywords:
- IDebugProperty3::GetCustomViewerCount
ms.assetid: dc5bb3e4-dc85-46e4-98fa-c6be8583b985
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 16cb623f58668362e5e308e1d66dfd6ca7c0fb8c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721191"
---
# <a name="idebugproperty3getcustomviewercount"></a>IDebugProperty3::GetCustomViewerCount
Bu özellik için kullanılabilen özel görüntüleyenlerin sayısını alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetCustomViewerCount(
    ULONG* pcelt
);
```

```csharp
int GetCustomViewerCount(
    out uint pcelt
);
```

## <a name="parameters"></a>Parametreler
`pcelt`\
[çıkış] Bu özellik için kullanılabilen özel görüntüleyenlerin sayısı.

## <a name="return-value"></a>Dönüş Değeri
Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
Tür görselleştiricilerini desteklemek için, bu yöntem aramayı [GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) yöntemine ileter. İfade değerlendiricisi, bu özelliğin türü için özel görüntüleyenleri de destekliyorsa, bu yöntem döndürülen değere özel görüntüleyen sayısını ekler.

Tür görüntüleyiciler ve özel görüntüleyenler arasındaki farklar hakkında ayrıntılı bilgi için Type [Visualizer ve Custom Viewer'a](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)bakın.

## <a name="example"></a>Örnek
Aşağıdaki örnek, [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) arabirimini ortaya çıkaran bir **CProperty** nesnesi için bu yöntemin nasıl uygulanacağını gösterir.

```cpp
STDMETHODIMP CProperty::GetCustomViewerCount(ULONG* pcelt)
{
    if (pcelt == NULL)
    {
        return E_POINTER;
    }

    if (GetVisualizerService())
    {
        return m_pIEEVisualizerService->GetCustomViewerCount(pcelt);
    }
    else
    {
        return E_NOTIMPL;
    }
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)
- [Tür Görselleştiricisi ve Özel Görüntüleyici](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
