---
description: Bu işlemi durdurulmuş bir durumdan çalıştırmaya devam eder. Önceki yürütme durumu (bir adım gibi) temizlenir ve işlem yeniden yürütülmeye başlar.
title: 'IDebugProcess3:: Execute | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Execute
helpviewer_keywords:
- IDebugProcess3::Execute
ms.assetid: d831cd81-d7bf-4172-8517-aa699867791f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 149497bcee5c37813e9d1134237ddb991d5893da
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150256"
---
# <a name="idebugprocess3execute"></a>IDebugProcess3::Execute
Bu işlemi durdurulmuş bir durumdan çalıştırmaya devam eder. Önceki yürütme durumu (bir adım gibi) temizlenir ve işlem yeniden yürütülmeye başlar.

> [!NOTE]
> Bu yöntem, [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md)yerine kullanılmalıdır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Execute(
   IDebugThread2* pThread
);
```

```csharp
int Execute(
   IDebugThread2 pThread
);
```

## <a name="parameters"></a>Parametreler
`pThread`\
'ndaki Yürütülecek iş parçacığını temsil eden bir [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) nesnesi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Kullanıcı başka bir işlemin iş parçacığında durdurulmuş bir durumdan yürütülmeye başladığında, bu yöntem bu işlem üzerinde çağrılır. Bu yöntem, Kullanıcı IDE 'deki **hata ayıklama** menüsünden **Başlat** komutunu seçtiğinde de çağrılır. Bu yöntemin uygulanması, işlemdeki geçerli iş parçacığında [sürdürülmesi](../../../extensibility/debugger/reference/idebugthread2-resume.md) yöntemini çağırmak kadar basit olabilir.

> [!WARNING]
> Bu çağrıyı gerçekleştirirken [olay](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) için bir durdurma olayı veya anında (zaman uyumlu) olay göndermeyin; Aksi takdirde hata ayıklayıcı yanıt vermeyi durdurabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Sürdür](../../../extensibility/debugger/reference/idebugthread2-resume.md)
- [Olay](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
