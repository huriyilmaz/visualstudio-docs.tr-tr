---
description: Bu işlemi durdurulmuş bir durumdan çalıştırmaya devam eder. Önceki yürütme durumu (bir adım gibi) korunur ve işlem yeniden yürütülmeye başlar.
title: 'IDebugProcess3:: Continue | Microsoft Docs'
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
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 11f2d5b652b950976834b8ba18f71a1dc0d1b34c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105081587"
---
# <a name="idebugprocess3continue"></a>IDebugProcess3::Continue
Bu işlemi durdurulmuş bir durumdan çalıştırmaya devam eder. Önceki yürütme durumu (bir adım gibi) korunur ve işlem yeniden yürütülmeye başlar.

> [!NOTE]
> Bu yöntem [devam etmek](../../../extensibility/debugger/reference/idebugprogram2-continue.md)yerine kullanılmalıdır.

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
'ndaki Devam etmek için iş parçacığını temsil eden bir [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) nesnesi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, kaç işlem hata ayıklandığına veya durdurma olayını hangi işlemin üretdiğine bakılmaksızın bu işlemde çağrılır. Uygulamanın önceki yürütme durumunu (bir adım gibi) yürütmesi ve yürütülmeye devam etmeden önce hiçbir daha durdurulmamış olsa da yürütmeye devam etmesi gerekir. Diğer bir deyişle, bu işlemdeki bir iş parçacığı adım adım bir işlem yapıyor ve başka bir işlem durdurulduğu için durdurulduysa ve daha sonra `Continue` çağrıldıysa, belirtilen iş parçacığının orijinal adım aşımı işlemini tamamlaması gerekir.

 **Uyarı** Bu çağrıyı gerçekleştirirken [olay](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) için bir durdurma olayı veya anında (zaman uyumlu) olay göndermeyin; Aksi takdirde hata ayıklayıcı yanıt vermeyi durdurabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Olay](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
