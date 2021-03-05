---
description: Belirli bir kod bağlamı için bir kod konum tanımlayıcısı döndürür.
title: 'IDebugDisassemblyStream2:: GetCodeLocationId | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
helpviewer_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
ms.assetid: 567adfb8-2f54-499a-a027-e4ecb82277ef
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8c1c3a6f7a9f2e2a0617f1322d17073a9dcc7c32
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102162943"
---
# <a name="idebugdisassemblystream2getcodelocationid"></a>IDebugDisassemblyStream2::GetCodeLocationId
Belirli bir kod bağlamı için bir kod konum tanımlayıcısı döndürür.

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
'ndaki Bir tanımlayıcıya dönüştürülecek bir [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) nesnesi.

`puCodeLocationId` dışı Kod konumu tanımlayıcısını döndürür. Bkz. açıklamalar.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür. `E_CODE_CONTEXT_OUT_OF_SCOPE`Kod bağlamı geçerli ancak kapsam dışında bir değer döndürür.

## <a name="remarks"></a>Açıklamalar
 Kod konumu tanımlayıcısı, ayrıştırılmış derlemeyi destekleme hata ayıklama altyapısına (DE) özgüdür. Bu konum tanımlayıcısı, koddaki konumları izlemek için DE tarafından dahili olarak kullanılır ve genellikle bir tür adres ya da fark olur. Tek gereksinim, bir konumun kod bağlamı başka bir konumun kod bağlamından azsa, ilk kod bağlamının karşılık gelen kod konumu tanımlayıcısının ikinci kod bağlamının kod konumu tanımlayıcısından de küçük olması gerekir.

 Kod konumu tanımlayıcısının kod bağlamını almak için [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md) yöntemini çağırın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)
