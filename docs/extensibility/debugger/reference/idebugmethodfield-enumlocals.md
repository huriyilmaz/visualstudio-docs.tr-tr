---
description: yönteminin seçili yerel değişkenleri için bir numaralayıcı oluşturur.
title: IDebugMethodField::EnumLocals | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumLocals
helpviewer_keywords:
- IDebugMethodField::EnumLocals method
ms.assetid: b0456a6d-2b96-49e2-a871-516571b4f6a5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2b9ea26c91f441ee5615e86bade7e1e412d59837e28d7fe3eedab06e715540c7
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121339602"
---
# <a name="idebugmethodfieldenumlocals"></a>IDebugMethodField::EnumLocals
yönteminin seçili yerel değişkenleri için bir numaralayıcı oluşturur.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT EnumLocals(
    IDebugAddress*     pAddress,
    IEnumDebugFields** ppLocals
);
```

```csharp
int EnumLocals(
    IDebugAddress        pAddress,
    out IEnumDebugFields ppLocals
);
```

## <a name="parameters"></a>Parametreler
`pAddress`\
[in] Yerellerin hangi bağlamı veya kapsamı seçerek hata ayıklama adresini temsil eden [bir IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) nesnesi.

`ppLocals`\
[out] Yerellerin [listesini temsil eden bir IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) nesnesi döndürür; aksi takdirde, yerel ayar yoksa null değer döndürür.

## <a name="return-value"></a>Dönüş Değeri
Başarılı olursa, S_OK döndürür veya S_FALSE yerel dil yoksa bu işlevi döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
Yalnızca verilen hata ayıklama adresini içeren blok içinde tanımlanan değişkenler numaralandı. Derleyici tarafından oluşturulan yereller dahil olmak üzere tüm yereller gerekli ise [EnumAllLocals yöntemini](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md) çağırın.

Bir yöntem birden çok kapsam bağlamı veya blok içerebilir. Örneğin, aşağıdaki contrived yöntemi üç kapsam içerir: iki iç blok ve yöntem gövdesi.

```csharp
public void func(int index)
{
    // Method body scope
    int a = 0;
    if (index == 1)
    {
        // Inner scope 1
        int temp1 = a;
    }
    else
    {
        // Inner scope 2
        int temp2 = a;
    }
}
```

[IDebugMethodField nesnesi](../../../extensibility/debugger/reference/idebugmethodfield.md) yöntemin `func` kendisini temsil eder. Adrese `EnumLocals` ayarlanmış [bir IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) ile yöntemini çağırma, değişkeni içeren bir `Inner Scope 1` sabit değer `temp1` döndürür, örneğin.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)
