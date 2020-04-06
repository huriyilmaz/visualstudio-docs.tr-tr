---
title: IDebugDisassemblyStream2::GetCodeLocationId | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
helpviewer_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
ms.assetid: 567adfb8-2f54-499a-a027-e4ecb82277ef
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 32be70e11776177a0e68f09689c2262497703ab1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732245"
---
# <a name="idebugdisassemblystream2getcodelocationid"></a>IDebugDisassemblyStream2::GetCodeLocationId
Belirli bir kod bağlamı için kod konum tanımlayıcısı döndürür.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetCodeLocationId( 
   IDebugCodeContext2* pCodeContext,
   UINT64*             puCodeLocationId
);
```

```csharp
int GetCodeLocationId( 
   IDebugCodeContext2 pCodeContext,
   out ulong          puCodeLocationId
);
```

## <a name="parameters"></a>Parametreler
`pCodeContext`\
[içinde] Bir [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) nesnesi bir tanımlayıcıya dönüştürülecek.

`puCodeLocationId`[çıkış] Kod konum tanımlayıcısını döndürür. Bkz. Açıklamalar.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür. Kod `E_CODE_CONTEXT_OUT_OF_SCOPE` bağlamı geçerli yse ancak kapsam dışındaysa döndürür.

## <a name="remarks"></a>Açıklamalar
 Kod konum tanımlayıcısı, sökmeyi destekleyen hata ayıklama altyapısına (DE) özgüdür. Bu konum tanımlayıcısı, koddaki pozisyonları izlemek için DE tarafından dahili olarak kullanılır ve genellikle bir tür adres veya ofsettir. Tek gereksinim, bir konumun kod bağlamı başka bir konumun kod bağlamından daha azsa, ilk kod bağlamının karşılık gelen kod konum tanımlayıcısının da ikinci kod bağlamının kod konumu tanımlayıcıdan daha az olması gerekir.

 Kod konum tanımlayıcısının kod bağlamını almak için [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md) yöntemini arayın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)
