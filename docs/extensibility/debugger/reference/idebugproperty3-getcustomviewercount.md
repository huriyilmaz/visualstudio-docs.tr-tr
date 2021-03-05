---
description: Bu özellik için kullanılabilir olabilecek özel görüntüleyicilerin sayısını alır.
title: 'IDebugProperty3:: GetCustomViewerCount | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::GetCustomViewerCount
helpviewer_keywords:
- IDebugProperty3::GetCustomViewerCount
ms.assetid: dc5bb3e4-dc85-46e4-98fa-c6be8583b985
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 58ad7ffc1b3250f5002f9f08208c464d14a2cc15
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102171402"
---
# <a name="idebugproperty3getcustomviewercount"></a>IDebugProperty3::GetCustomViewerCount
Bu özellik için kullanılabilir olabilecek özel görüntüleyicilerin sayısını alır.

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
dışı Bu özellik için kullanılabilen özel görüntüleyicilerin sayısı.

## <a name="return-value"></a>Dönüş Değeri
Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
Tür görselleştiricilerini desteklemek için bu yöntem çağrıyı [GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) yöntemine iletir. İfade değerlendirici bu özelliğin türü için özel görüntüleyiciler de destekliyorsa, bu yöntem döndürülen değere özel görüntüleyicilerin sayısını ekler.

Tür Görselleştiriciler ve özel görüntüleyiciler arasındaki farklılıklar hakkında ayrıntılı bilgi için bkz. [tür görselleştiricisi ve özel Görüntüleyici](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md).

## <a name="example"></a>Örnek
Aşağıdaki örnek, [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) arabirimini kullanıma sunan bir **cproperty** nesnesi için bu yöntemin nasıl uygulanacağını gösterir.

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
