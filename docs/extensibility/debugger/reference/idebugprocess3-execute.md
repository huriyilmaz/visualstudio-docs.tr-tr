---
description: Bu işlemi durdurulmuş durumdan çalıştırmaya devam eder. Önceki yürütme durumu (örneğin, adım) temizlir ve işlem yeniden yürütülmaya başlar.
title: IDebugProcess3::Execute | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Execute
helpviewer_keywords:
- IDebugProcess3::Execute
ms.assetid: d831cd81-d7bf-4172-8517-aa699867791f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b32c80a904e9ec96fd5f49b3d54c75fce26327b3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122126680"
---
# <a name="idebugprocess3execute"></a>IDebugProcess3::Execute
Bu işlemi durdurulmuş durumdan çalıştırmaya devam eder. Önceki yürütme durumu (örneğin, adım) temizlir ve işlem yeniden yürütülmaya başlar.

> [!NOTE]
> Bu yöntem Execute yerine [kullanılmalıdır.](../../../extensibility/debugger/reference/idebugprogram2-execute.md)

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
[in] Yürütülecek [iş parçacığını temsil eden bir IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) nesnesi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde hata kodunu döndürür.

## <a name="remarks"></a>Açıklamalar
 Kullanıcı başka bir işlem iş parçacığında durdurulmuş durumdan yürütmeye başladığında, bu işlemde bu yöntem çağrılır. Kullanıcı IDE'de Hata Ayıkla **menüsünden Başlat** komutunu **seçerek de** bu yöntem çağrılır. Bu yöntemin uygulanması, işlemde geçerli iş parçacığında [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) yöntemini çağırma kadar basit olabilir.

> [!WARNING]
> Bu çağrıyı işleme sırasında Bir durdurma olayı veya hemen (zaman uyumlu) [olayı Event'e](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) göndermeyin; aksi takdirde hata ayıklayıcı yanıt vermemeyebilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Sürdür](../../../extensibility/debugger/reference/idebugthread2-resume.md)
- [Olay](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
