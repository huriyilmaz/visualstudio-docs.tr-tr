---
description: Bu olayın konumunu açıklayan belge bağlamını alır.
title: 'IDebugCanStopEvent2:: GetDocumentContext | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::GetDocumentContext
helpviewer_keywords:
- IDebugCanStopEvent2::GetDocumentContext
ms.assetid: 936a6c4e-30c5-4c7e-9ad5-910cc605a4b5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 44e1f2aa918547d8b3b0b1bea1940072fe2d8f84
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085088"
---
# <a name="idebugcanstopevent2getdocumentcontext"></a>IDebugCanStopEvent2::GetDocumentContext
Bu olayın konumunu açıklayan belge bağlamını alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetDocumentContext ( 
   IDebugDocumentContext2** ppDocCxt
);
```

```csharp
int GetDocumentContext ( 
   out IDebugDocumentContext2 ppDocCxt
);
```

## <a name="parameters"></a>Parametreler
`ppDocCxt`\
dışı Geçerli kod konumuna karşılık gelen kaynak dosya belgesindeki bir konumu temsil eden [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) arabirimini döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Genellikle, belge bağlamı kaynak dosyada bir konum olarak düşünülebilir.

 Kod yönergelerine yönelik kod bağlamını almak için [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md) yöntemini çağırın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)
