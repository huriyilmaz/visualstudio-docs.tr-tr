---
title: 'IDebugCodeContext2:: GetDocumentContext | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2::GetDocumentContext
helpviewer_keywords:
- IDebugCodeContext2::GetDocumentContext
ms.assetid: d552cc92-963f-43c1-949f-ae6b63a427b8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 46510ce794ea30fdd365a77007b962a1eafd5d31
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80734348"
---
# <a name="idebugcodecontext2getdocumentcontext"></a>IDebugCodeContext2::GetDocumentContext
Bu kod bağlamına karşılık gelen belge bağlamını alır. Belge bağlamı, kaynak dosyadaki, bu yönergeyi oluşturan kaynak koda karşılık gelen bir konumu temsil eder.

## <a name="syntax"></a>Söz dizimi

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
dışı Kod bağlamına karşılık gelen [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) nesnesini döndürür. `S_OK`Döndürülürse, altı olmamalıdır `null` .

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür. Hata ayıklama altyapısı, parametre gibi bir hata kodu döndürmelidir `E_FAIL` . Örneğin, `out` `null` kod bağlamı ilişkili kaynak konumu olmadığında.

## <a name="remarks"></a>Açıklamalar
 Genellikle, belge bağlamı kaynak dosyada bir konum olarak düşünülebilir, ancak kod bağlamı yürütme akışındaki kod yönergesinin bir konumudur.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
