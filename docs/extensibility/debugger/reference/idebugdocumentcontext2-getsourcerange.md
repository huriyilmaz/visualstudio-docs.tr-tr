---
title: 'IDebugDocumentContext2:: GetSourceRange | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::GetSourceRange
helpviewer_keywords:
- IDebugDocumentContext2::GetSourceRange
ms.assetid: 5903c75e-5390-4d13-9314-1ee276255313
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 58318ebde2446a32cc515d09b7a1d848222b554b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99947014"
---
# <a name="idebugdocumentcontext2getsourcerange"></a>IDebugDocumentContext2::GetSourceRange
Bu belge bağlamının kaynak kodu aralığını alır.

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
[in, out] Başlangıç konumuyla doldurulmuş bir [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) yapısı. Bu bilgi gerekmiyorsa bu bağımsız değişkeni null bir değer olarak ayarlayın.

`pEndPosition`\
[in, out] Bitiş konumuyla doldurulmuş bir [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) yapısı. Bu bilgi gerekmiyorsa bu bağımsız değişkeni null bir değer olarak ayarlayın.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Kaynak aralığı, geçerli deyimden hemen hemen sonra koda katkıda bulunan önceki deyimden hemen sonra olmak üzere, kaynak kodu aralığıdır. Kaynak aralığı genellikle, açıklamalar dahil olmak üzere kaynak deyimlerini, ayrıştırma penceresindeki kodla birlikte karıştırmak için kullanılır.

 Yalnızca bu belge bağlamı içinde yer alan kod deyimlerinin aralığını almak için [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) yöntemini çağırın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
