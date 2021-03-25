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
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ab3d00df9883da93d0d8121433b962d365a408e3
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105066418"
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
