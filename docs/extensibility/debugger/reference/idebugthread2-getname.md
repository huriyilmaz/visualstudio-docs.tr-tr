---
title: IDebugThread2::GetName | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::GetName
helpviewer_keywords:
- IDebugThread2::GetName
ms.assetid: eec54b8f-4a0e-4919-b0f9-81d4bd1e0b6f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9d4828b573585969154f2ad1d484c9fcdf767417
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718765"
---
# <a name="idebugthread2getname"></a>IDebugThread2::GetName
Bir iş parçacığının adını alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetName ( 
   BSTR* pbstrName
);
```

```csharp
int GetName ( 
   out string pbstrName
);
```

## <a name="parameters"></a>Parametreler
`pbstrName`\
[çıkış] İş parçacığının adını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Alınan ad her zaman görüntülenebilen bir addır ve bu ad iş parçacığı açıklar. İş parçacığı adı, adlandırılmış iş parçacıklarını destekleyen bir çalışma zamanı mimarisinden türetilmiş olabilir veya hata ayıklama altyapısından türetilen bir ad olabilir. Alternatif olarak, iş parçacığının adı [SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md) yöntemine yapılan bir çağrı yla ayarlanabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)
