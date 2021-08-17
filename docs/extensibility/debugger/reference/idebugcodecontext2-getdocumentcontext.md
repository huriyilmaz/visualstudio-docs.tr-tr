---
description: Bu kod bağlamına karşılık gelen belge bağlamını alır.
title: IDebugCodeContext2::GetDocumentContext | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2::GetDocumentContext
helpviewer_keywords:
- IDebugCodeContext2::GetDocumentContext
ms.assetid: d552cc92-963f-43c1-949f-ae6b63a427b8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9aadc89257d86bac9432026d368c1f84e963152a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122079837"
---
# <a name="idebugcodecontext2getdocumentcontext"></a>IDebugCodeContext2::GetDocumentContext
Bu kod bağlamına karşılık gelen belge bağlamını alır. Belge bağlamı, kaynak dosyada bu yönergeyi oluşturan kaynak koda karşılık gelen bir konumu temsil eder.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetDocumentContext( 
   IDebugDocumentContext2** ppSrcCxt
);
```

```csharp
int GetDocumentContext( 
   out IDebugDocumentContext2 ppSrcCxt
);
```

## <a name="parameters"></a>Parametreler
`ppSrcCxt`\
[out] Kod [bağlamına karşılık gelen IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) nesnesini döndürür. `S_OK`döndürülürse, bu, olmayan olması `null` gerekir.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür. Hata ayıklama altyapısı, örneğin, kod bağlamının ilişkili bir kaynak konumuna sahip olması gibi bir `E_FAIL` `out` hata kodu `null` getirmalıdır.

## <a name="remarks"></a>Açıklamalar
 Genellikle, belge bağlamı bir kaynak dosyada konum olarak, kod bağlamı ise yürütme akışındaki bir kod yönergesi konumu olarak düşünebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
