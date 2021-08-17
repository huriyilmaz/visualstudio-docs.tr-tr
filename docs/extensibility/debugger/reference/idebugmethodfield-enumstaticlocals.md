---
description: yönteminin statik yerel değişkenleri için bir numaralayıcı oluşturur.
title: IDebugMethodField::EnumStaticLocals | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumStaticLocals
helpviewer_keywords:
- IDebugMethodField::EnumStaticLocals method
ms.assetid: e0c522c4-f759-4c32-ae87-7abcb573e77d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 156df08f9df1ef6e6b8c72b3aa65e14dce84b531
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122078875"
---
# <a name="idebugmethodfieldenumstaticlocals"></a>IDebugMethodField::EnumStaticLocals
yönteminin statik yerel değişkenleri için bir numaralayıcı oluşturur.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT EnumStaticLocals( 
   IEnumDebugFields** ppLocals
);
```

```csharp
int EnumStaticLocals(
   out IEnumDebugFields ppLocals
);
```

## <a name="parameters"></a>Parametreler
`ppLocals`\
[out] Statik [yereller listesini temsil eden bir IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) nesnesi döndürür. Statik yerel ayar yoksa null değer döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, S_OK veya S_FALSE yerel olmayan bir değer döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Her öğe, farklı statik yerel türleri temsil eden bir [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) nesnesidir. Nesnenin tam olarak hangi statik yerel türü temsil ettiğini belirlemek için her nesnede [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) yöntemini çağırma.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
