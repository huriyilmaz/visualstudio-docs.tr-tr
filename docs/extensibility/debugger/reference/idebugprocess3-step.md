---
description: İşlemin bir yönerge veya ifadeye adımla çalışmasına neden olur.
title: 'IDebugProcess3:: Step | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Step
helpviewer_keywords:
- IDebugProcess3::Step
ms.assetid: 6ad9094c-27cc-4927-8a7c-1b4d97b2e436
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0d5c9e43676751a97baf0bf664c3da17dcf9aca5
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076530"
---
# <a name="idebugprocess3step"></a>IDebugProcess3::Step
İşlemin bir yönerge veya ifadeye adımla çalışmasına neden olur.

> [!NOTE]
> Bu yöntem, [adım](../../../extensibility/debugger/reference/idebugprogram2-step.md)yerine kullanılmalıdır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Step(
   IDebugThread2* pThread,
   STEPKIND       sk,
   STEPUNIT       step,
);
```

```csharp
int Step(
   IDebugThread2 pThread,
   enum_STEPKIND sk,
   enum_STEPUNIT step
);
```

## <a name="parameters"></a>Parametreler
`pThread`\
'ndaki Bulanan iş parçacığını temsil eden bir [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) nesnesi.

`sk`\
'ndaki [Stepkind](../../../extensibility/debugger/reference/stepkind.md) değerlerinden biri.

`step`\
'ndaki [Stepunit](../../../extensibility/debugger/reference/stepunit.md) değerlerinden biri.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa S_OK döndürür; Aksi takdirde hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 İş parçacıkları arasında herhangi bir iş parçacığı eşitlemesi veya iletişim olması durumunda, belirli bir iş parçacığı adımlarken işlemdeki diğer iş parçacıklarının çalışması gerekir.

 **Uyarı** Bu çağrıyı gerçekleştirirken [olay](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) için bir durdurma olayı veya anında (zaman uyumlu) olay göndermeyin; Aksi takdirde hata ayıklayıcı yanıt vermeyi durdurabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [STEPKIND](../../../extensibility/debugger/reference/stepkind.md)
- [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md)
- [Olay](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
