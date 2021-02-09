---
title: 'IDebugThread2:: GetName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::GetName
helpviewer_keywords:
- IDebugThread2::GetName
ms.assetid: eec54b8f-4a0e-4919-b0f9-81d4bd1e0b6f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7a8a7a4f041e2a38cf1e24e8cf156d3e595010b6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893860"
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
dışı İş parçacığının adını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Alınan ad her zaman görüntülenebilen bir addır ve bu ad iş parçacığını açıklar. İş parçacığı adı, adlandırılmış iş parçacıklarını destekleyen bir çalışma zamanı mimarisinden türetilebilir veya hata ayıklama altyapısından türetilmiş bir ad olabilir. Alternatif olarak, iş parçacığının adı [SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md) yöntemine yapılan bir çağrıyla ayarlanabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)
