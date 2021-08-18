---
description: Bu yöntem görselleştirici için yeni bir nesnesi alır.
title: IEEVisualizerDataProvider::GetNewObjectForVisualizer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerDataProvider::GetNewObjectForVisualizer
helpviewer_keywords:
- IEEVisualizerDataProvider::GetNewObjectForVisualizer method
ms.assetid: a898d549-4898-4fde-aad1-e8bb89129652
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 19c8a3b0e6c91c1751462660a5c9f08913419890
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122095705"
---
# <a name="ieevisualizerdataprovidergetnewobjectforvisualizer"></a>IEEVisualizerDataProvider::GetNewObjectForVisualizer
Bu yöntem görselleştirici için yeni bir nesnesi alır. Bu yöntem her zaman mevcut nesneden yeni bir nesne oluşturur.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetNewObjectForVisualizer(
   IDebugObject** ppObject
);
```

```csharp
int GetNewObjectForVisualizer(
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>Parametreler
`ppObject`\
[out] Yeni nesne.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 `This method` şu anda temsil ettiği nesneyi yeniden değerlendirir ve sonucu yeni bir nesne olarak döndürür. Değerlendirme sonucunda mevcut nesne güncelleştirilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
