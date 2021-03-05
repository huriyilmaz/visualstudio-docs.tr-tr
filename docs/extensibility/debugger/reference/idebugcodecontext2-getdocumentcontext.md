---
description: Bu kod bağlamına karşılık gelen belge bağlamını alır.
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
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d99b67e76c8cc8719c77c88c8b93ca667c3a025a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164168"
---
# <a name="idebugcodecontext2getdocumentcontext"></a>IDebugCodeContext2::GetDocumentContext
Bu kod bağlamına karşılık gelen belge bağlamını alır. Belge bağlamı, kaynak dosyadaki, bu yönergeyi oluşturan kaynak koda karşılık gelen bir konumu temsil eder.

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
dışı Kod bağlamına karşılık gelen [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) nesnesini döndürür. `S_OK`Döndürülürse, altı olmamalıdır `null` .

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür. Hata ayıklama altyapısı, parametre gibi bir hata kodu döndürmelidir `E_FAIL` . Örneğin, `out` `null` kod bağlamı ilişkili kaynak konumu olmadığında.

## <a name="remarks"></a>Açıklamalar
 Genellikle, belge bağlamı kaynak dosyada bir konum olarak düşünülebilir, ancak kod bağlamı yürütme akışındaki kod yönergesinin bir konumudur.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
