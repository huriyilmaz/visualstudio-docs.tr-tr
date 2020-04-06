---
title: IEEVisualizerService::GetCustomViewerList | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerService::GetCustomViewerList
helpviewer_keywords:
- IEEVisualizerService::GetCustomViewerList method
ms.assetid: 249d26ca-914f-43af-a400-8162477223f4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f3808ad6fb511270ee3825601c476f10a8b77124
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718022"
---
# <a name="ieevisualizerservicegetcustomviewerlist"></a>IEEVisualizerService::GetCustomViewerList
Bu yöntem, bu hizmetin bildiği tür görüntüleyicilerin listesini döndürür.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetCustomViewerList(
   ULONG                celtSkip,
   ULONG                celtRequested,
   DEBUG_CUSTOM_VIEWER* rgViewers,
   ULONG*               pceltFetched
);
```

```csharp
int GetCustomViewerList(
   uint                  celtSkip,
   uint                  celtRequested,
   DEBUG_CUSTOM_VIEWER[] rgViewers,
   out uint              pceltFetched
);
```

## <a name="parameters"></a>Parametreler
`celtSkip`\
[içinde] Atlayacak görüntüleyici sayısı.

`celRequested`\
[içinde] Alınacak görüntüleyici sayısı `rgViewers` (dizinin boyutunu da belirtir).

`rgViewers`\
[içinde, dışarı] Doldurulacak [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) yapıları dizisi.

`pceltFetched`\
[çıkış] Görüntüleyicilerin sayısı aslında geri alındı.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
- [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) türü görselleştiriciler için destek bir parçası olarak bu yönteme istek geçer. İfade değerlendiricisi de aynı tür için özel görüntüleyenler sağlıyorsa, listeye bu özel görüntüleyenler için uygun şekilde doldurulmuş [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) yapıları ekleyebilir. [GetCustomViewerCount'ın](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) bu ek görüntüleyiciler yansıttığından emin olun.

 Görselleştiriciler ve görüntüleyenler arasındaki farklar hakkında ayrıntılar için [Görselleştirici Yazın ve Özel Görüntüleyici'ye](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) bakın.

## <a name="see-also"></a>Ayrıca bkz.
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
- [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)
- [GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)
- [Tür Görselleştiricisi ve Özel Görüntüleyici](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
