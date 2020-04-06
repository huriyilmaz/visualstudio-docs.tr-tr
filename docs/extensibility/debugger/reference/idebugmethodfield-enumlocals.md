---
title: IDebugMethodField::EnumLocals | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumLocals
helpviewer_keywords:
- IDebugMethodField::EnumLocals method
ms.assetid: b0456a6d-2b96-49e2-a871-516571b4f6a5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 08872160860d0d442f9807705dea70190dff9b28
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727210"
---
# <a name="idebugmethodfieldenumlocals"></a>IDebugMethodField::EnumLocals
Yöntemin seçili yerel değişkenleri için bir sayısallaştırıcı oluşturur.

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
[içinde] Yerel leri almak için bağlam veya kapsamı seçen hata ayıklama adresini temsil eden bir [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) nesnesi.

`ppLocals`\
[çıkış] Yerel lerin listesini temsil eden bir [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) nesnesini döndürür; aksi takdirde, yerel halk yoksa null bir değer verir.

## <a name="return-value"></a>Dönüş Değeri
Başarılı olursa, yerel halk yoksa S_OK veya S_FALSE döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
Yalnızca verilen hata ayıklama adresini içeren blok içinde tanımlanan değişkenler numaralandırılır. Derleyici tarafından oluşturulan yerel halk lar da dahil olmak üzere tüm yerel halklar gerekiyorsa, [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md) yöntemini arayın.

Yöntem, birden çok kapsam bağlamı veya blok içerebilir. Örneğin, aşağıdaki contrived yöntemi üç kapsamları, iki iç blok ve yöntem gövdesi kendisi içerir.

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

[IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) nesnesi `func` yöntemin kendisini temsil eder. Metnin `EnumLocals` `Inner Scope 1` adrese ayarlı bir `temp1` [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) ile çağrılması, örneğin değişkeni içeren bir numaralandırmayı döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)
