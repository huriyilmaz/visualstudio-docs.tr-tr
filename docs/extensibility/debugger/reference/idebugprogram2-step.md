---
description: Bir adım gerçekleştirir.
title: IDebugProgram2::Step | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Step
helpviewer_keywords:
- IDebugProgram2::Step
ms.assetid: e4c2ffce-9810-4088-8162-eac9ef04f2a9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 038c490fb9e889199193463f098e44386556b3fb
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122071650"
---
# <a name="idebugprogram2step"></a>IDebugProgram2::Step
Bir adım gerçekleştirir.

> [!NOTE]
> Bu yöntem kullanım dışıdır. Bunun yerine [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md) yöntemini kullanın.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Step( 
   IDebugThread2*  pThread,
   STEPKIND        sk,
   STEPUNIT        step
);
```

```csharp
int Step( 
   IDebugThread2  pThread,
   enum_STEPKIND  sk,
   enum_STEPUNIT  step
);
```

## <a name="parameters"></a>Parametreler
`pThread`\
[in] Basan iş parçacığını temsil eden bir [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) nesnesi.

`sk`\
[in] [STEPKIND numaralama](../../../extensibility/debugger/reference/stepkind.md) değerinden adım türlerini belirten bir değer.

`step`\
[in] [STEPUNIT enumerasyonundan](../../../extensibility/debugger/reference/stepunit.md) adım birimini belirten bir değer (örneğin, deyim veya yönergeye göre).

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 İş parçacıkları arasında herhangi bir iş parçacığı eşitlemesi veya iletişim olması durumunda, belirli bir iş parçacığı adımlama sırasında programda diğer iş parçacıklarının çalışması gerekir.

> [!WARNING]
> Bu çağrıyı işleme sırasında Bir durdurma olayı veya hemen (zaman uyumlu) [olayı Event'e](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) göndermeyin; aksi takdirde hata ayıklayıcı yanıt vermemeyebilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [Olay](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
