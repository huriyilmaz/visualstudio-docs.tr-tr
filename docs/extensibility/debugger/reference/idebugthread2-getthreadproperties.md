---
description: Bu iş parçacığını tanımlayan özellikleri alır.
title: 'IDebugThread2:: GetThreadProperties | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::GetThreadProperties
helpviewer_keywords:
- IDebugThread2::GetThreadProperties
ms.assetid: 304403fd-f4f8-4096-ac2c-bd3b59663aad
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fc681ff8258988c5a7f708d9ae2342f013010bd6
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105070940"
---
# <a name="idebugthread2getthreadproperties"></a>IDebugThread2::GetThreadProperties
Bu iş parçacığını tanımlayan özellikleri alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetThreadProperties (
    THREADPROPERTY_FIELDS dwFields,
    THREADPROPERTIES*     ptp
);
```

```csharp
int GetThreadProperties (
    enum_THREADPROPERTY_FIELDS dwFields,
    THREADPROPERTIES[]         ptp
);
```

## <a name="parameters"></a>Parametreler
`dwFields`\
'ndaki [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md) Numaralandırmadaki, doldurulacak alanları belirleyen bayrakların bir birleşimi `ptp` .

`ptp`\
[in, out] İş parçacığının özellikleriyle doldurulmuş bir [Threadproperties](../../../extensibility/debugger/reference/threadproperties.md) yapısı.

## <a name="return-value"></a>Dönüş Değeri
Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
Bu yöntemden döndürülen bilgiler genellikle **Iş parçacıkları** hata ayıklama penceresinde gösterilir.

## <a name="example"></a>Örnek
Aşağıdaki örnek, `CProgram` [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) arabirimini uygulayan basit bir nesne için bu yöntemin nasıl uygulanacağını gösterir.

```cpp
HRESULT CProgram::GetThreadProperties(THREADPROPERTY_FIELDS dwFields,
                                      THREADPROPERTIES *ptp)
{
    HRESULT hr = E_FAIL;

    // Check for valid argument.
    if (ptp)
    {
        // Create an array of buffers at ptp the size of the
        // THREADPROPERTIES structure and set all of the
        // buffers at ptp to 0.
        memset(ptp, 0, sizeof (THREADPROPERTIES));

        // Check if there is a valid THREADPROPERTY_FIELDS and the TPF_ID flag is set.
        if (dwFields & TPF_ID)
        {
            // Check for successful assignment of the current thread ID to
            // the dwThreadId of the passed THREADPROPERTIES.
            if (GetThreadId(&(ptp->dwThreadId)) == S_OK)
            {
                // Set the TPF_ID flag in the THREADPROPERTY_FIELDS enumerator
                // of the passed THREADPROPERTIES.
                ptp->dwFields |= TPF_ID;
            }
        }

        hr = S_OK;
    }
    else
        hr = E_INVALIDARG;

    return hr;
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)
- [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)
