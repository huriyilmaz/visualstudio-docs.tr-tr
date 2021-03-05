---
description: Bu sınıf için oluşturucular için bir Numaralandırıcı oluşturur.
title: 'IDebugClassField:: Enumoluşturucular | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumConstructors
helpviewer_keywords:
- IDebugClassField::EnumConstructors method
ms.assetid: 66a250b2-75a0-45aa-8d58-40f91cc4bf7b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 62b196b2fed8a3919968c72a7785a884196a86da
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164337"
---
# <a name="idebugclassfieldenumconstructors"></a>IDebugClassField::EnumConstructors
Bu sınıf için oluşturucular için bir Numaralandırıcı oluşturur.

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
'ndaki Sabit listesi için oluşturucuların türünü belirten [CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md) Numaralandırmadaki bir değer.

`ppEnum`\
dışı Oluşturucuların listesini temsil eden bir [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) nesnesi döndürür. Oluşturucu yoksa null değeri döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, S_OK döndürür veya Oluşturucu yoksa S_FALSE döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Sabit listesinin her öğesi bir Oluşturucu yöntemini açıklayan bir [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) nesnesidir.

 Oluşturucuların listesi genellikle derleyicinin sağladığı varsayılan oluşturucuları içermez.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md)
