---
title: 'IDebugCustomAttribute:: GetAttributeTypeField | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetAttributeTypeField
helpviewer_keywords:
- IDebugCustomAttribute::GetAttributeTypeField
ms.assetid: d6ce26d5-42ba-44c1-8659-0516db5bc82d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3fa72b6dfc02f29e5efd8d3e04f98f078cba66a2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99928451"
---
# <a name="idebugcustomattributegetattributetypefield"></a>IDebugCustomAttribute::GetAttributeTypeField
Özel öznitelik sınıfı türünü alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetAttributeTypeField( 
   IDebugClassField** ppCAType
);
```

```csharp
int GetAttributeTypeField(
   out IDebugClassField ppCAType
);
```

## <a name="parameters"></a>Parametreler
`ppCAType`\
dışı Özel özniteliğin bir örnek olduğu sınıfı temsil eden [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) nesnesini döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa S_OK döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Özel bir öznitelik her zaman bir sınıftır. Bu yöntem, bu sınıfı tanımlayan bir [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) nesnesine erişim sağlar.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
