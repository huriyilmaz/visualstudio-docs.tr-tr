---
description: Bu yöntem, Görselleştirici temsil ettiği nesneyi değiştirir.
title: 'IEEVisualizerDataProvider:: SetObjectForVisualizer | Microsoft Docs'
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
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2e0a59c10293d5d8cc13d46b625a7b43136cb71b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105091805"
---
# <a name="ieevisualizerdataprovidersetobjectforvisualizer"></a>IEEVisualizerDataProvider::SetObjectForVisualizer
Bu yöntem, Görselleştirici temsil ettiği nesneyi değiştirir.

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
'ndaki Ayarlanacak nesne.

`error`\
dışı Nesne ayarlanırken bir hata oluşursa, bu dize hata iletisini tutar.

`pException`\
dışı Bir hata oluşursa, bu nesne özel durum bilgilerini tutar.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu, hata bilgilerinin nasıl döndürüldüğünü belirleme uygulayıcısı 'na sahiptir. Ancak bazı çağıranlar yalnızca bir hata olduğunu anlamak için bir özel durum nesnesinin döndürülüp döndürülmeyeceğini görebilir, bu nedenle bir hata oluşursa bu yöntem her zaman bir özel durum nesnesi döndürmelidir. Çağıran tarafından kullanılması istediği durumlarda hata dizesi de sağlanmalıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
