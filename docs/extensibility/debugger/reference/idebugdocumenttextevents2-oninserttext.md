---
description: Hata ayıklama paketine metin eklenmiş olduğunu bildirir.
title: 'IDebugDocumentTextEvents2:: Onınserttext | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentTextEvents2::OnInsertText
helpviewer_keywords:
- IDebugDocumentTextEvents2::onInsertText
ms.assetid: 6040181f-7288-4a42-953c-d23f74200431
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 185320b887cec6f0616e16bea96e5f701b660434
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167340"
---
# <a name="idebugdocumenttextevents2oninserttext"></a>IDebugDocumentTextEvents2::onInsertText
Hata ayıklama paketine metin eklenmiş olduğunu bildirir.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT onInsert( 
   TEXT_POSITION pos,
   DWORD         dwNumToInsert
);
```

```csharp
int onInsert( 
   enum_TEXT_POSITION pos,
   uint               dwNumToInsert
);
```

## <a name="parameters"></a>Parametreler
`pos`\
'ndaki Metnin nereye eklendiğini belirten [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) yapısı.

`dwNumToInsert`\
'ndaki Eklenen metnin karakter sayısını belirtir.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
