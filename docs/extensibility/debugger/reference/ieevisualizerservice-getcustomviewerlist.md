---
description: Bu yöntem, bu hizmetin bildiği Görselleştiriciler türü listesini döndürür.
title: 'IEEVisualizerService:: GetCustomViewerList | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerService::GetCustomViewerList
helpviewer_keywords:
- IEEVisualizerService::GetCustomViewerList method
ms.assetid: 249d26ca-914f-43af-a400-8162477223f4
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0bd9c633c6b65bbd597619f9fd30487a734d9004
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102222906"
---
# <a name="ieevisualizerservicegetcustomviewerlist"></a>IEEVisualizerService::GetCustomViewerList
Bu yöntem, bu hizmetin bildiği Görselleştiriciler türü listesini döndürür.

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
'ndaki Atlanacak görselleştiricilerin sayısı.

`celRequested`\
'ndaki Alınacak görselleştiricilerin sayısı (Ayrıca dizinin boyutunu belirtir `rgViewers` ).

`rgViewers`\
[in, out] Doldurulacak [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) yapıları dizisi.

`pceltFetched`\
dışı Gerçekten alınan Görselleştiriciler sayısı.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
- [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) , istek türünü Görselleştiriciler için desteğinin bir parçası olarak bu yönteme geçirir. İfade değerlendirici aynı tür için özel görüntüleyiciler de sağlarsa, bu özel görüntüleyiciler için uygun şekilde doldurulmuş [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) yapılarını listeye ekleyebilir. [GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) 'un bu ek izleyicileri yansıttığından emin olun.

 Görselleştiriciler ve görüntüleyiciler arasındaki farklılıklarla ilgili ayrıntılar için bkz. [tür görselleştiricisi ve özel Görüntüleyici](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) .

## <a name="see-also"></a>Ayrıca bkz.
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
- [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)
- [GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)
- [Tür Görselleştiricisi ve Özel Görüntüleyici](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
