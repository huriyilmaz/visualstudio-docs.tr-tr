---
title: IDebugDocumentPosition2::IsPositionInDocument | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2::IsPositionInDocument
helpviewer_keywords:
- IDebugDocumentPosition2::IsPositionInDocument
ms.assetid: d5cf57cb-b93b-4e1d-bec9-185f4fe8668d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4d92dddda8fd9831f5d66b602cd48fdbbc3dbcf1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731650"
---
# <a name="idebugdocumentposition2ispositionindocument"></a>IDebugDocumentPosition2::IsPositionInDocument
Belge konumunun verilen belgede bulununp içermeyileceğini belirler.

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
[içinde] İçeren belge adayını temsil eden [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) nesnesi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem öncelikle [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) arabirimlerinde kesme noktaları ayarı kullanılır. Belgeler yüklendikçe, belgenin bu konumu bulunıp içermeden belirlenip belirtilen kesme noktası konumu çağrılır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
