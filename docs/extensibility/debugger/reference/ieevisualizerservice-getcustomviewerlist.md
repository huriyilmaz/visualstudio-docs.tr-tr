---
description: Bu yöntem, bu hizmetin bildiği tür görselleştiricilerinin listesini döndürür.
title: IEEVisualizerService::GetCustomViewerList | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerService::GetCustomViewerList
helpviewer_keywords:
- IEEVisualizerService::GetCustomViewerList method
ms.assetid: 249d26ca-914f-43af-a400-8162477223f4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 42a42c36eef04f1e858f2025703a74501e3c785a0bb5f2e17cd3b4e891ecf793
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121401901"
---
# <a name="ieevisualizerservicegetcustomviewerlist"></a>IEEVisualizerService::GetCustomViewerList
Bu yöntem, bu hizmetin bildiği tür görselleştiricilerinin listesini döndürür.

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
[in] Atlayabilirsiniz görselleştirici sayısı.

`celRequested`\
[in] Alınacak görselleştirici sayısı (dizinin boyutunu da `rgViewers` belirtir).

`rgViewers`\
[in, out] Doldurulması [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) yapı dizisi.

`pceltFetched`\
[out] Gerçekte alınan görselleştirici sayısı.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
- [GetCustomViewerList,](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) tür görselleştirici desteği kapsamında isteği bu yönteme iletir. İfade değerlendirici aynı tür için özel görüntüleyiciler de sağlarsa, bu özel görüntüleyiciler için uygun şekilde [doldurulmuş DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) yapıları listeye ekleyebilirsiniz. [GetCustomViewerCount'ın bu ek görüntüleyicileri](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) yansıtıyor olduğundan emin olun.

 [Görselleştiricilerle görüntüleyiciler arasındaki farklar hakkında ayrıntılı](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) bilgi için bkz. Tür Görselleştirici ve Özel Görüntüleyici.

## <a name="see-also"></a>Ayrıca bkz.
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
- [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)
- [GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)
- [Tür Görselleştiricisi ve Özel Görüntüleyici](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
