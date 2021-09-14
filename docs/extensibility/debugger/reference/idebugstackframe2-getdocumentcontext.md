---
description: Bu yığın çerçevesi için belge bağlamını alır.
title: IDebugStackFrame2::GetDocumentContext | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetDocumentContext
helpviewer_keywords:
- IDebugStackFrame2::GetDocumentContext
ms.assetid: 69e81439-1238-4f18-9028-6fd1c1ba5e4a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f1677f2e5c50092dd3a4255e48282401ce936bfe
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725130"
---
# <a name="idebugstackframe2getdocumentcontext"></a>IDebugStackFrame2::GetDocumentContext
Bu yığın çerçevesi için belge bağlamını alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetDocumentContext ( 
   IDebugDocumentContext2** ppCxt
);
```

```csharp
int GetDocumentContext ( 
   out IDebugDocumentContext2 ppCxt
);
```

## <a name="parameters"></a>Parametreler
`ppCxt`\
[out] Kaynak [belgede geçerli konumu temsil eden bir IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md) yöntemini çağırmadan ve ardından kod bağlamında [GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) yöntemini çağırmadan daha hızlıdır. Ancak, her hata ayıklama altyapısının (DE) bu yöntemi uygulayacakları garanti edilemez.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)
