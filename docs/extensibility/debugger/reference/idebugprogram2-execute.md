---
description: 'IDebugProgram2:: Execute bu programı durdurulmuş bir durumdan çalıştırmaya devam ediyor. Önceki yürütme durumu (bir adım gibi) temizlenir ve program yeniden yürütülmeye başlar.'
title: 'IDebugProgram2:: Execute | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Execute
helpviewer_keywords:
- IDebugProgram2::Execute
ms.assetid: f7205ce8-0ac6-4fcd-b6ec-b720b4fcaccf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6112dbf51664458bc2d592951dcc842d1352020b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105075997"
---
# <a name="idebugprogram2execute"></a>IDebugProgram2::Execute
Bu programı durdurulmuş bir durumdan çalıştırmaya devam eder. Önceki yürütme durumu (bir adım gibi) temizlenir ve program yeniden yürütülmeye başlar.

> [!NOTE]
> Bu yöntem kullanım dışıdır. Bunun yerine [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md) metodunu kullanın.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Execute(
   void
);
```

```csharp
int Execute();
```

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Kullanıcı başka bir programın iş parçacığında durdurulmuş bir durumdan yürütmeyi başlattığında, bu yöntem bu programda çağırılır. Bu yöntem, Kullanıcı IDE 'deki **hata ayıklama** menüsünden **Başlat** komutunu seçtiğinde de çağrılır. Bu yöntemin uygulanması, programdaki geçerli iş parçacığında [sürdürülür](../../../extensibility/debugger/reference/idebugthread2-resume.md) yöntemini çağırmak kadar basit olabilir.

> [!WARNING]
> Bu çağrıyı gerçekleştirirken [olay](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) için bir durdurma olayı veya anında (zaman uyumlu) olay göndermeyin; Aksi takdirde hata ayıklayıcı yanıt vermeyi durdurabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [Olay](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [Sürdür](../../../extensibility/debugger/reference/idebugthread2-resume.md)
