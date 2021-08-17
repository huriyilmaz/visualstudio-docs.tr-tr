---
description: IDebugProgram2::Continue bu programı durdurulmuş durumdan çalıştırmaya devam eder. Önceki yürütme durumu (adım gibi) korunur ve program yeniden yürütülmaya başlar.
title: IDebugProgram2::Continue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Continue
helpviewer_keywords:
- IDebugProgram2::Continue
ms.assetid: e5a6e02a-d21b-4a03-a034-e8de1f71ce2e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b29952af05a864a11e54c602afc559d03d5203faa354559f65079cb73a00cc43
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121416072"
---
# <a name="idebugprogram2continue"></a>IDebugProgram2::Continue
Bu programı durdurulmuş durumdan çalıştırmaya devam eder. Önceki yürütme durumu (adım gibi) korunur ve program yeniden yürütülmaya başlar.

> [!NOTE]
> Bu yöntem kullanım dışıdır. Bunun yerine [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md) yöntemini kullanın.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Continue( 
   IDebugThread2* pThread
);
```

```csharp
int Continue( 
   IDebugThread2 pThread
);
```

## <a name="parameters"></a>Parametreler
`pThread` [in] İş [parçacığını temsil eden bir IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) nesnesi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, kaç programın hatadan ayıklandıklarına veya durdurma olayı oluşturan programa bakılmaksızın bu programda çağrılır. Uygulama önceki yürütme durumunu (örneğin, bir adım) tutmalı ve önceki yürütmesini tamamlamadan önce hiç durdurulmamıştı gibi yürütmeye devam edecektir. Yani, bu programda bir iş parçacığı bir adım adım işlem yapıyorsa ve başka bir program durdurulmuş ve ardından bu yöntem çağrıldıktan sonra durdurulmuşsa, programın özgün adım adım işlemini tamamlaması gerekir.

> [!WARNING]
> Bu çağrıyı işleme sırasında Bir durdurma olayı veya hemen (zaman uyumlu) [olayı Event'e](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) göndermeyin; aksi takdirde hata ayıklayıcı yanıt vermemeyebilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [Olay](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
