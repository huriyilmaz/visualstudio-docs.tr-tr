---
title: IDebugDisassemblyStream2::GetCodeContext | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetCodeContext
helpviewer_keywords:
- IDebugDisassemblyStream2::GetCodeContext
ms.assetid: a6d0ae82-7617-4915-9713-369abe3e2e53
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a6b3864528ee90c22a1e7122eeaf1969f613cc8e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732290"
---
# <a name="idebugdisassemblystream2getcodecontext"></a>IDebugDisassemblyStream2::GetCodeContext
Belirtilen kod konum tanımlayıcısına karşılık gelen bir kod bağlamı nesnesi döndürür.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetCodeContext( 
   UINT64               uCodeLocationId,
   IDebugCodeContext2** ppCodeContext
);
```

```csharp
int GetCodeContext( 
   ulong                  uCodeLocationId,
   out IDebugCodeContext2 ppCodeContext
);
```

## <a name="parameters"></a>Parametreler
`uCodeLocationId`\
[içinde] Kod konum tanımlayıcısını belirtir. Kod konum tanımlayıcısının açıklaması için [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md) yönteminin Açıklamalar bölümüne bakın.

`ppCodeContext`\
[çıkış] İlişkili kod bağlamını temsil eden bir [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Kod konum tanımlayıcısı bir çağrıdan [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md) yöntemine döndürülebilir ve [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) yapısında görünebilir.

 Kod bağlamını kod konumu tanımlayıcısına dönüştürmek için [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md) yöntemini arayın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)
- [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
