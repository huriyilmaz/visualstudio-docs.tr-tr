---
description: özelliğini alan yöntemini alır.
title: IDebugPropertyField::GetPropertyGetter | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPropertyField::GetPropertyGetter
helpviewer_keywords:
- IDebugPropertyField::GetPropertyGetter method
ms.assetid: ab9f861a-42ad-4a82-9ae6-2606176f755a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 59486320cc8265efe3c8597d07bbd98f69010fc2
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725170"
---
# <a name="idebugpropertyfieldgetpropertygetter"></a>IDebugPropertyField::GetPropertyGetter
özelliğini alan yöntemini alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetPropertyGetter( 
   IDebugMethodField** ppField
);
```

```cpp
int GetPropertyGetter(
   out IDebugMethodField ppField
);
```

## <a name="parameters"></a>Parametreler
`ppField`\
[out] Özelliğini alan yöntemi temsil eden bir [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, S_OK; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Özelliğini ayaran yöntemi almak için [GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md) yöntemini çağırır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)
- [GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md)
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
