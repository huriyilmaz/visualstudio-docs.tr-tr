---
title: 'IDebugProcess3:: Step | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Step
helpviewer_keywords:
- IDebugProcess3::Step
ms.assetid: 6ad9094c-27cc-4927-8a7c-1b4d97b2e436
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 69f7c1736f786b2c59678826b71f7f9349629057
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99926252"
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
