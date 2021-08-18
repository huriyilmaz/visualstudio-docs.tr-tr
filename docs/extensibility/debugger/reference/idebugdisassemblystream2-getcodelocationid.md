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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fce5176c8461f9e04859641bf33da9b60bbeb5ad
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122096576"
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
