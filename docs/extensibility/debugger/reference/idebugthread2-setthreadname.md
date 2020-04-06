---
title: IDebugThread2::SetThreadName | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::SetThreadName
helpviewer_keywords:
- IDebugThread2::SetThreadName
ms.assetid: fa934121-3f58-44dc-9c30-d3f752e44c8b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b3d39c99049c4c4583fbda466712c5b216137316
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718669"
---
# <a name="idebugthread2setthreadname"></a>IDebugThread2::SetThreadName
İş parçacığının adını ayarlar.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT SetThreadName ( 
   LPCOLESTR pszName
);
```

```csharp
int SetThreadName ( 
   string pszName
);
```

## <a name="parameters"></a>Parametreler
`pszName`\
[içinde] İş parçacığının adı.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 İş parçacığı adını almak için [GetName](../../../extensibility/debugger/reference/idebugthread2-getname.md) yöntemini arayın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [GetName](../../../extensibility/debugger/reference/idebugthread2-getname.md)
