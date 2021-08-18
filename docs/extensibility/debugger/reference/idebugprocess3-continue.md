---
description: Bu işlemi durdurulmuş durumdan çalıştırmaya devam eder. Önceki yürütme durumu (adım gibi) korunur ve işlem yeniden yürütülmaya başlar.
title: IDebugProcess3::Continue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Continue
helpviewer_keywords:
- IDebugProcess3::Continue
ms.assetid: 57506242-5763-4c08-adb9-8a78ce02cebb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5ace819a6503525f6aa7c65dbcc60187492da3dd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122126693"
---
# <a name="idebugprocess3continue"></a>IDebugProcess3::Continue
Bu işlemi durdurulmuş durumdan çalıştırmaya devam eder. Önceki yürütme durumu (adım gibi) korunur ve işlem yeniden yürütülmaya başlar.

> [!NOTE]
> Bu yöntem, Continue yerine [kullanılmalıdır.](../../../extensibility/debugger/reference/idebugprogram2-continue.md)

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
`pThread`\
[in] Devam etmek için iş parçacığını temsil eden [bir IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) nesnesi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde hata kodunu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, kaç işlemde hata ayıklandı veya durdurma olayı oluşturan işlemden bağımsız olarak bu işlemde çağrılır. Uygulama önceki yürütme durumunu (örneğin, bir adım) tutmalı ve önceki yürütmesini tamamlamadan önce hiç durdurulmamıştı gibi yürütmeye devam edecektir. Başka bir ifadeyle, bu işlemde bir iş parçacığı bir adım adım işlem yapıyorsa ve başka bir işlem durdurulmuş ve ardından çağrıldıktan sonra durduruldu ise, belirtilen iş parçacığının özgün adım adım `Continue` işlemi tamamlaması gerekir.

 **Uyarı** Bu çağrıyı işleme sırasında Bir durdurma olayı veya hemen (zaman uyumlu) [olayı Event'e](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) göndermeyin; aksi takdirde hata ayıklayıcı yanıt vermemeyebilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Olay](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
