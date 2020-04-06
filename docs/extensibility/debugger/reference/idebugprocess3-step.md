---
title: IDebugProcess3::Adım | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Step
helpviewer_keywords:
- IDebugProcess3::Step
ms.assetid: 6ad9094c-27cc-4927-8a7c-1b4d97b2e436
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c5c4927f3f997b7fdbdca2b32977f2aa31a51219
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723556"
---
# <a name="idebugprocess3step"></a>IDebugProcess3::Step
İşlemin bir yönerge veya deyim adımı na neden olur.

> [!NOTE]
> Bu yöntem [Adım](../../../extensibility/debugger/reference/idebugprogram2-step.md)yerine kullanılmalıdır.

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
[içinde] Adımlanan iş parçacığı temsil eden bir [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) nesnesi.

`sk`\
[içinde] [STEPKIND](../../../extensibility/debugger/reference/stepkind.md) değerlerinden biri.

`step`\
[içinde] [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md) değerlerinden biri.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, S_OK döndürür; aksi takdirde hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 İş parçacıkları arasında iş parçacığı eşitleme veya iletişim olması durumunda, belirli bir iş parçacığı adımlanırken işlemdeki diğer iş parçacıkları çalıştırılmalıdır.

 **Uyarı** Bu aramayı işlerken Bir durdurma olayını veya [olay](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) anına anında (eşzamanlı) bir olay göndermeyin; aksi takdirde hata ayıklama asılabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [STEPKIND](../../../extensibility/debugger/reference/stepkind.md)
- [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md)
- [Olay](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
