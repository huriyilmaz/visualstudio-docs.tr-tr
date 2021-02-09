---
title: 'IDebugThread2:: Cansetnextdeyimizi | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::CanSetNextStatement
helpviewer_keywords:
- IDebugThread2::CanSetNextStatement
ms.assetid: 7014af80-ff4f-4790-a34b-0528918d1fa3
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6ce1d04303edb34de98ead8d416221e7f71338ac
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99909287"
---
# <a name="idebugthread2cansetnextstatement"></a>IDebugThread2::CanSetNextStatement
Geçerli yönerge işaretçisinin verilen yığın çerçevesine uygulanıp ayarlanamayacağını belirler.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT CanSetNextStatement ( 
   IDebugStackFrame2*  pStackFrame,
   IDebugCodeContext2* pCodeContext
);
```

```csharp
int CanSetNextStatement ( 
   IDebugStackFrame2  pStackFrame,
   IDebugCodeContext2 pCodeContext
);
```

## <a name="parameters"></a>Parametreler
`pStackFrame`\
Gelecekte kullanılmak üzere ayrılmıştır; null değere ayarlayın. Bu null bir değer ise, geçerli yığın çerçevesini kullanın.

`pCodeContext`\
'ndaki Yürütülmesi ve bağlamı için kod konumunu açıklayan bir [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) nesnesi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem döndürürse `S_OK` , bir sonraki ifadeyi ayarlamak Için [Setnextdeyimyöntemi](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md) çağırın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)
