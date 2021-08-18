---
description: Hata ayıklama paketine metnin belgede değiştirildiğini bildirir.
title: 'IDebugDocumentTextEvents2:: onReplaceText | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentTextEvents2::OnReplaceText
helpviewer_keywords:
- IDebugDocumentTextEvents2::onReplaceText
ms.assetid: cb39f025-66d8-4dc0-bef6-1bdc8e07db92
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 85b731f97331c9c8c865158c3e3fa1e3fca8668a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122119249"
---
# <a name="idebugdocumenttextevents2onreplacetext"></a>IDebugDocumentTextEvents2::onReplaceText
Hata ayıklama paketine metnin belgede değiştirildiğini bildirir.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT onReplaceText( 
   TEXT_POSITION pos,
   DWORD         dwNumToReplace
);
```

```csharp
int onReplaceText( 
   enum_TEXT_POSITION pos,
   uint               dwNumToReplace
);
```

## <a name="parameters"></a>Parametreler
`pos`\
'ndaki [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) , metnin nerede değiştirildiğini gösterir.

`dwNumToReplace`\
'ndaki Metnin değiştirildiği karakter sayısını belirtir.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
