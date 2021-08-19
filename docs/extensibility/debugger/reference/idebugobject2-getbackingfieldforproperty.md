---
description: Bu nesne tarafından temsil edilen özelliği destekleyen alanı veya değişkeni (varsa) alır.
title: IDebugObject2::GetBackingFieldForProperty | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::GetBackingFieldForProperty
helpviewer_keywords:
- IDebugObject2::GetBackingFieldForProperty method
ms.assetid: e72c6338-5573-4fad-8075-f3ade3435424
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c1f89f6158620578be58884a764773cb77b930a2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122043173"
---
# <a name="idebugobject2getbackingfieldforproperty"></a>IDebugObject2::GetBackingFieldForProperty
Bu nesne tarafından temsil edilen özelliği destekleyen alanı veya değişkeni (varsa) alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetBackingFieldForProperty(
   IDebugObject2** ppObject
);
```

```csharp
int GetBackingFieldForProperty(
   out IDebugObject2 ppObject
);
```

## <a name="parameters"></a>Parametreler
`ppObject`\
[out] Backing [alanını açıklayan bir IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) nesnesi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, S_OK; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 [IDebugObject2 nesnesi,](../../../extensibility/debugger/reference/idebugobject2.md) bir yönetilen kod sınıfı özelliğini, yani get ve/veya set erişimcisi olan bir yöntemi temsil eder. Bu tür özellikler genellikle bir değişkenin özelliği tarafından yönlendirilen değeri içermesi gerektirir. Bu değişken, destek alanı olarak bilinir. Nesne için bir backing alanı yoksa, null değer döndürerek emin olun: Bazı çağrılar dönüş değerine dikkat emiyor olabilir, ancak bunun yerine içinde bir null değerin döndürüldü olup olmadığını görmek için `ppObject` bakar.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
