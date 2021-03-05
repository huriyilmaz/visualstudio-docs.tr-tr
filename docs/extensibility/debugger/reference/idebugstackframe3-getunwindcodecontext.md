---
description: Yığın geriye doğru izleme işlemi gerçekleştiyse bir konumu temsil eden kod bağlamını döndürür.
title: 'IDebugStackFrame3:: Getunıwıncode bağlamı | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame3::GetUnwindCodeContext
helpviewer_keywords:
- IDebugStackFrame3::GetUnwindCodeContext method
ms.assetid: b25f7e7d-2b24-48e4-93b3-829e61d73ebf
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1ef0a66729a2e9061a9e71ec0634a65999b55bf2
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102159737"
---
# <a name="idebugstackframe3getunwindcodecontext"></a>IDebugStackFrame3::GetUnwindCodeContext
Yığın geriye doğru izleme işlemi gerçekleştiyse bir konumu temsil eden kod bağlamını döndürür.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetUnwindCodeContext(
   IDebugCodeContext2 **ppCodeContext
);
```

```csharp
int GetUnwindCodeContext(
   out IDebugCodeContext2 ppCodeContext
);
```

## <a name="parameters"></a>Parametreler
`ppCodeContext`\
dışı Yığın geriye doğru meydana getirtiyse kod bağlamı konumunu temsil eden bir [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, bir yığın geri dönüşi sonrasında konum için bir kod bağlamı döndürebilse de, yığın geriye doğru bir şekilde geçerli yığın çerçevesinde gerçekleşebileceği anlamına gelmez.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
