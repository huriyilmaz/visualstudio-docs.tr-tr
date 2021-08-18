---
description: Bir yönerge veya deyimin adımına neden olur.
title: IDebugProcess3::Step | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 27dc90056c9c0e5c0521a4102cec4714c72b3cc9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122132827"
---
# <a name="idebugprocess3step"></a>IDebugProcess3::Step
Bir yönerge veya deyimin adımına neden olur.

> [!NOTE]
> Bu yöntem, Adım yerine [kullanılmalıdır.](../../../extensibility/debugger/reference/idebugprogram2-step.md)

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
[in] Basan iş parçacığını temsil eden [bir IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) nesnesi.

`sk`\
[in] [STEPKIND değerlerinden](../../../extensibility/debugger/reference/stepkind.md) biri.

`step`\
[in] [STEPUNIT değerlerinden](../../../extensibility/debugger/reference/stepunit.md) biri.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, S_OK; aksi takdirde hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 İş parçacıkları arasında herhangi bir iş parçacığı eşitlemesi veya iletişim olması durumunda, işlemde yer alan diğer iş parçacıkları belirli bir iş parçacığı adımlama sırasında çalışmalı.

 **Uyarı** Bu çağrıyı işleme sırasında Bir durdurma olayı veya hemen (zaman uyumlu) [olayı Event'e](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) göndermeyin; aksi takdirde hata ayıklayıcı yanıt vermemeyebilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [STEPKIND](../../../extensibility/debugger/reference/stepkind.md)
- [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md)
- [Olay](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
