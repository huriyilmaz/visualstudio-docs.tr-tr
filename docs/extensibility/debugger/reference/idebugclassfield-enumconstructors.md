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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122119730"
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
