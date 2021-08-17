---
description: Bu belge bağlamının kaynak kod aralığını alır.
title: IDebugDocumentContext2::GetSourceRange | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::GetSourceRange
helpviewer_keywords:
- IDebugDocumentContext2::GetSourceRange
ms.assetid: 5903c75e-5390-4d13-9314-1ee276255313
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0eeec0f04f45cda0c257299923f0da9224312974
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122096407"
---
# <a name="idebugdocumentcontext2getsourcerange"></a>IDebugDocumentContext2::GetSourceRange
Bu belge bağlamının kaynak kod aralığını alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetSourceRange( 
   TEXT_POSITION* pBegPosition,
   TEXT_POSITION* pEndPosition
);
```

```csharp
int GetSourceRange( 
   TEXT_POSITION[] pBegPosition,
   TEXT_POSITION[] pEndPosition
);
```

## <a name="parameters"></a>Parametreler
`pBegPosition`\
[in, out] Başlangıç [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) doldurulan bir yapıdır. Bu bilgi gerekli yoksa bu bağımsız değişkeni null değere ayarlayın.

`pEndPosition`\
[in, out] Bitiş [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) doldurulan bir yapıdır. Bu bilgi gerekli yoksa bu bağımsız değişkeni null değere ayarlayın.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Kaynak aralığı, geçerli deyimden koda katkıda bulunan önceki deyiminden hemen sonraya kadar olan kaynak kodu aralığının tamamıdır. Kaynak aralığı genellikle açıklamalar da dahil olmak üzere kaynak deyimlerini, disassembly penceresindeki kodla karıştırmak için kullanılır.

 Yalnızca bu belge bağlamındaki kod deyimleri için aralığı almak için [GetStatementRange yöntemini çağırmanız](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
