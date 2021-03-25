---
description: Daha önce hata ayıklama altyapısı (DE) tarafından SDM 'ye gönderilen zaman uyumlu bir hata ayıklama olayının alındığını ve işlendiğini göstermek için oturum hata ayıklama Yöneticisi (SDM) tarafından çağırılır.
title: 'IDebugEngine2:: ContinueFromSynchronousEvent | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::ContinueFromSynchronousEvent
helpviewer_keywords:
- IDebugEngine2::ContinueFromSynchronousEvent
ms.assetid: 9a57dfcd-df8e-4be5-b1fe-bd853e3c6bb2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 64303d91ff9ab4743adc980bb8ee92f9bdec9345
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105093892"
---
# <a name="idebugengine2continuefromsynchronousevent"></a>IDebugEngine2::ContinueFromSynchronousEvent
Daha önce hata ayıklama altyapısı (DE) tarafından SDM 'ye gönderilen zaman uyumlu bir hata ayıklama olayının alındığını ve işlendiğini göstermek için oturum hata ayıklama Yöneticisi (SDM) tarafından çağırılır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT ContinueFromSynchronousEvent(
    IDebugEvent2* pEvent
);
```

```csharp
HRESULT ContinueFromSynchronousEvent(
    IDebugEvent2 pEvent
);
```

## <a name="parameters"></a>Parametreler
`pEvent`\
'ndaki Hata ayıklayıcının şimdi devam etmesi gereken daha önce gönderilen zaman uyumlu olayı temsil eden bir [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) nesnesi.

## <a name="return-value"></a>Dönüş Değeri
Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
Aynı parametresi, parametrenin gösterdiği olayın kaynağı olduğunu doğrulamalıdır `pEvent` .

## <a name="example"></a>Örnek
Aşağıdaki örnek, `CEngine` [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) arabirimini uygulayan basit bir nesne için bu yöntemin nasıl uygulanacağını gösterir.

```cpp
HRESULT CEngine::ContinueFromSynchronousEvent(IDebugEvent2* pEvent)
{
    HRESULT hr;

    // Create a pointer to a unique event interface defined for batch file
    // breaks.
    IAmABatchFileEvent *pBatEvent;
    // Check for successful query for the unique batch file event
    // interface.
    if (SUCCEEDED(pEvent->QueryInterface(IID_IAmABatchFileEvent,
                                        (void **)&pBatEvent)))
    {
        // Release the result of the QI.
        pBatEvent->Release();
        // Check thread message for notification to continue.
        if (PostThreadMessage(GetCurrentThreadId(),
                              WM_CONTINUE_SYNC_EVENT,
                              0,
                              0))
        {
            hr = S_OK;
        }
        else
        {
            hr = HRESULT_FROM_WIN32(GetLastError());
        }
    }
    else
    {
        hr = E_INVALIDARG;
    }
    return hr;
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
