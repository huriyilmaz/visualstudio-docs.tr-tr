---
description: Belgedeki hata ayıklama paketi tarafından etkin hale getirilen konumu açıklayan belge bağlamını alır.
title: 'IDebugActivateDocumentEvent2:: GetDocumentContext | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugActivateDocumentEvent2::GetDocumentContext
helpviewer_keywords:
- GetDocumentContext method
- IDebugActivateDocumentEvent2::GetDocumentContext method
ms.assetid: e7472069-7337-4ef4-8f8a-8c027a2e22f4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 79344833eb5f8e46b4725828980e334b4049c01e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105078168"
---
# <a name="idebugactivatedocumentevent2getdocumentcontext"></a>IDebugActivateDocumentEvent2::GetDocumentContext
Belgedeki hata ayıklama paketi tarafından etkin hale getirilen konumu açıklayan belge bağlamını alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetDocumentContext ( 
   IDebugDocumentContext2** ppDocContext
);
```

```csharp
int GetDocumentContext ( 
   out IDebugDocumentContext2 ppDocContext
);
```

## <a name="parameters"></a>Parametreler
`ppDocContext`\
dışı Kaynak dosya belgesindeki bir konumu temsil eden bir [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) nesnesi döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu konum, örneğin giriş işaretini göstermek için kullanılabilir.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
