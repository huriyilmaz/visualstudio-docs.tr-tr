---
description: Bu nesne tarafından temsil edilen özelliği yedeklebilecek alanı veya değişkeni (varsa) alır.
title: 'IDebugObject2:: GetBackingFieldForProperty | Microsoft Docs'
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
ms.openlocfilehash: 0019f890f8f487d455e92854f812296fa7dffd94fdde62c13505db2ba69bfe4f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121339287"
---
# <a name="idebugobject2getbackingfieldforproperty"></a>IDebugObject2::GetBackingFieldForProperty
Bu nesne tarafından temsil edilen özelliği yedeklebilecek alanı veya değişkeni (varsa) alır.

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
dışı Destek alanını açıklayan bir [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) nesnesi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa S_OK döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) nesnesi, bir yönetilen kod sınıfı özelliğini, diğer bir deyişle, Get ve/veya set erişimcisi olan bir yöntemi temsil eder. Bu tür özellikler genellikle özelliği tarafından yönetilen değeri içermesi için bir değişken gerektirir. Bu değişken, yedekleme alanı olarak bilinir. Nesne için bir yedekleme alanı yoksa, bir null değer döndürtığınızdan emin olun: bazı çağıranlar dönüş değerine dikkat ödemeyebilir ancak bunun yerine null değer döndürülüp döndürülmeyeceğini göz atalım `ppObject` .

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
