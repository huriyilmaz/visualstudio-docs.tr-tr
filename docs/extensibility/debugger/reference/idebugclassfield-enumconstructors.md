---
description: Bu sınıfın oluşturucuları için bir numaralayıcı oluşturur.
title: IDebugClassField::EnumConstructors | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumConstructors
helpviewer_keywords:
- IDebugClassField::EnumConstructors method
ms.assetid: 66a250b2-75a0-45aa-8d58-40f91cc4bf7b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a019a55fc9610e0953b6083ad901c16ae73d0907
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725291"
---
# <a name="idebugclassfieldenumconstructors"></a>IDebugClassField::EnumConstructors
Bu sınıfın oluşturucuları için bir numaralayıcı oluşturur.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT EnumConstructors( 
   CONSTRUCTOR_ENUM   cMatch,
   IEnumDebugFields** ppEnum
);
```

```csharp
int EnumConstructors(
   CONSTRUCTOR_ENUM     cMatch,
   out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>Parametreler
`cMatch`\
[in] Enumeration [CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md) türünü belirten bir değerdir.

`ppEnum`\
[out] Oluşturucu listesini [temsil eden bir IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) nesnesi döndürür. Oluşturucu yoksa null değer döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, S_OK veya S_FALSE oluşturucu yoksa bu işlevi döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Numaralamanın her öğesi, oluşturucu yöntemini açıklayan [bir IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) nesnesidir.

 Oluşturucu listesi genellikle bir derleyici tarafından sağlanan varsayılan oluşturucuları içermez.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md)
