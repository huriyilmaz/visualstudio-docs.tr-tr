---
title: IEEVisualizerDataProvider::SetObjectForVisualizer | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer
helpviewer_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer method
ms.assetid: 40dad2be-57ff-4f74-9d82-c48039c125c4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ab63f1e74e0cd3ac64a4d7e7687a9136075b41a7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718086"
---
# <a name="ieevisualizerdataprovidersetobjectforvisualizer"></a>IEEVisualizerDataProvider::SetObjectForVisualizer
Bu yöntem, görselleştiricinin temsil ettiği nesneyi değiştirir.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT SetObjectForVisualizer(
   IDebugObject*  pNewObject,
   BSTR*          error,
   IDebugObject** pException
);
```

```csharp
int SetObjectForVisualizer(
   IDebugObject     pNewObject,
   out string       error,
   out IDebugObject pException
);
```

## <a name="parameters"></a>Parametreler
`pNewObject`\
[içinde] Ayarlanan nesne.

`error`\
[çıkış] Nesneyi ayarlayan bir hata varsa, bu dize hata iletisini tutar.

`pException`\
[çıkış] Bir hata varsa, bu nesne özel durum bilgilerini tutar.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Hata bilgilerinin nasıl döndürüldürün ne kadar olduğunu belirlemek uygulayıcıya kverilir. Ancak, bazı arayanlar yalnızca bir özel durum nesnesi bir hata olduğunu bilmek döndürüldü görmek için bakabilirsiniz mümkündür, bu nedenle bu yöntem her zaman bir hata varsa bir özel durum nesnesi döndürmelidir. Arayan kişinin bundan yararlanmak istemesi durumunda hata dizesi de sağlanmalıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
