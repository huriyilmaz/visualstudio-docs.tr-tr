---
description: Bu yöntem, bu nesneyle ilişkili bağımsız değişken türlerinin sayısını döndürür.
title: 'IDebugBinder3:: GetTypeArgumentCount | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetTypeArgumentCount
helpviewer_keywords:
- IDebugBinder3::GetTypeArgumentCount method
ms.assetid: caf68de6-6f7c-4efd-b803-121347a5032e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3118d7e0fc4f493013a9a328cda0682fcc0707aa
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102174010"
---
# <a name="idebugbinder3gettypeargumentcount"></a>IDebugBinder3::GetTypeArgumentCount
Bu yöntem, bu nesneyle ilişkili bağımsız değişken türlerinin sayısını döndürür.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetTypeArgumentCount(
   UINT* uCount
);
```

```csharp
int GetTypeArgumentCount(
   out uint uCount
);
```

## <a name="parameters"></a>Parametreler
`uCount`\
dışı Bu nesneyle ilişkili bağımsız değişken türlerinin sayısı.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem tarafından döndürülen değer, [GetTypeArguments](../../../extensibility/debugger/reference/idebugbinder3-gettypearguments.md) yöntemiyle kullanılmak üzere bir dizi ayırmak için kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [GetTypeArguments](../../../extensibility/debugger/reference/idebugbinder3-gettypearguments.md)
