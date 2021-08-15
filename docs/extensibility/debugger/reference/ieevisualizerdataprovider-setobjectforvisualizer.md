---
description: Bu yöntem görselleştiricinin temsil ettiği nesneyi değiştirir.
title: IEEVisualizerDataProvider::SetObjectForVisualizer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer
helpviewer_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer method
ms.assetid: 40dad2be-57ff-4f74-9d82-c48039c125c4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ebd0ff5ac54e7f6c634eb4321e8f8979b562536d3ad1e46b2abf0459fe694792
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121389442"
---
# <a name="ieevisualizerdataprovidersetobjectforvisualizer"></a>IEEVisualizerDataProvider::SetObjectForVisualizer
Bu yöntem görselleştiricinin temsil ettiği nesneyi değiştirir.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT SetObjectForVisualizer(
   IDebugObject*  pNewObject,
   BSTR*          error,
   IDebugObject** pException
);
```

```csharp
int SetObjectForVisualizer(
   IDebugObject     pNewObject,
   out string       error,
   out IDebugObject pException
);
```

## <a name="parameters"></a>Parametreler
`pNewObject`\
[in] Ayar için nesne.

`error`\
[out] Nesnesini ayarlarken bir hata oluştu ise, bu dize hata iletisini tutar.

`pException`\
[out] Bir hata varsa, bu nesne özel durum bilgilerini tutar.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Hata bilgisinin nasıl döndürüleceklerini belirlemek, uygulamacıya göredir. Ancak, bazı çağıranların yalnızca bir özel durum nesnesinin bir hata olduğunu bilmek için döndürüldü mü bakarak bakabilirsiniz, bu nedenle bir hata varsa bu yöntem her zaman bir özel durum nesnesi döndürür. Hata dizesi, çağıranın bunu kullanmak istediği durumda da sağlanmalıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
