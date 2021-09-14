---
description: Belge konumunun verilen belgede içerildiğini belirler.
title: 'IDebugDocumentPosition2:: ıspositionındocument | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2::IsPositionInDocument
helpviewer_keywords:
- IDebugDocumentPosition2::IsPositionInDocument
ms.assetid: d5cf57cb-b93b-4e1d-bec9-185f4fe8668d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c72b0a3494018f8dc2bda518507d4b13da9cfe74
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634974"
---
# <a name="idebugdocumentposition2ispositionindocument"></a>IDebugDocumentPosition2::IsPositionInDocument
Belge konumunun verilen belgede içerildiğini belirler.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT IsPositionInDocument( 
   IDebugDocument2* pDoc
);
```

```csharp
int IsPositionInDocument( 
   IDebugDocument2 pDoc
);
```

## <a name="parameters"></a>Parametreler
`pDoc`\
'ndaki İçerilen belge adayını temsil eden [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) nesnesi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem öncelikle [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) arabirimlerinde kesme noktaları ayarlamak için kullanılır. Belgeler yüklendiğinde, belgenin bu konumu içerip içermediğini anlamak için kesme noktası konumu çağırılır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
