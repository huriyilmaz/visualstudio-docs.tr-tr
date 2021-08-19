---
description: Metodun seçili yerel değişkenleri için bir Numaralandırıcı oluşturur.
title: 'IDebugMethodField:: Enumyereller | Microsoft Docs'
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
ms.openlocfilehash: 4f5b89689f4ba0cbd72941aaa688d44ff565b8c9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122043368"
---
# <a name="idebugmethodfieldenumlocals"></a>IDebugMethodField::EnumLocals
Metodun seçili yerel değişkenleri için bir Numaralandırıcı oluşturur.

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
'ndaki Yerelleri alacağınız bağlamı veya kapsamı seçen hata ayıklama adresini temsil eden bir [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) nesnesi.

`ppLocals`\
dışı Yereller listesini temsil eden bir [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) nesnesi döndürür; Aksi takdirde, Yereller yoksa null değeri döndürür.

## <a name="return-value"></a>Dönüş Değeri
Başarılı olursa, S_OK döndürür veya Yereller yoksa S_FALSE döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
Yalnızca verilen hata ayıklama adresini içeren blok içinde tanımlanan değişkenler numaralandırılır. Derleyicinin ürettiği Yereller dahil tüm Yereller gerekliyse, [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md) metodunu çağırın.

Bir yöntem, birden fazla kapsam bağlamı veya blok içerebilir. Örneğin, aşağıdaki contrived yöntemi üç kapsam, iki iç blok ve Yöntem gövdesinin kendisini içerir.

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

[IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) nesnesi, `func` yöntemin kendisini temsil eder. `EnumLocals`Yöntemi bir [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) kümesi ile çağırmak `Inner Scope 1` `temp1` , örneğin değişkenini içeren bir sabit listesi döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)
