---
description: Bu özellik için kullanılabilen özel görüntüleyici sayısını alır.
title: IDebugProperty3::GetCustomViewerCount | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::GetCustomViewerCount
helpviewer_keywords:
- IDebugProperty3::GetCustomViewerCount
ms.assetid: dc5bb3e4-dc85-46e4-98fa-c6be8583b985
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9482b1f2fcf594de5f9ba33b902e35eda6010168
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122063947"
---
# <a name="idebugproperty3getcustomviewercount"></a>IDebugProperty3::GetCustomViewerCount
Bu özellik için kullanılabilen özel görüntüleyici sayısını alır.

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
[out] Bu özellik için kullanılabilen özel görüntüleyici sayısı.

## <a name="return-value"></a>Dönüş Değeri
Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
Bu yöntem, tür görselleştiricilerini desteklemek için çağrıyı [GetCustomViewerCount yöntemine](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) iletir. İfade değerlendirici bu özelliğin türü için özel görüntüleyicileri de destekliyorsa, bu yöntem döndürülen değere özel görüntüleyici sayısını ekler.

Tür görselleştiricileri ile özel görüntüleyiciler arasındaki farklar hakkında ayrıntılı bilgi için bkz. [Tür Görselleştiricisi ve Özel Görüntüleyici.](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)

## <a name="example"></a>Örnek
Aşağıdaki örnek, [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) arabirimini ortaya çıkaran **bir CProperty** nesnesi için bu yöntemin nasıl uygulandığını gösterir.

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
