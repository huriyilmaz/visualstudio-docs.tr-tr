---
description: Belirtilen ileti dizesini hata ayıklayıcının çıkış penceresine gönderir.
title: IDebugIDECallback::D isplayMessage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugIDECallback::DisplayMessage
ms.assetid: c19b48ee-b370-4fce-91fe-f82bf1e63179
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ab7223d065df0bb77c2782ef7f66d14843a23f62
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102172551"
---
# <a name="idebugidecallbackdisplaymessage"></a>IDebugIDECallback::DisplayMessage
Belirtilen ileti dizesini hata ayıklayıcının çıkış penceresine gönderir.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT DisplayMessage (
   LPCOLESTR szMessage
);
```

```csharp
int DisplayMessage (
   string szMessage
);
```

## <a name="parameters"></a>Parametreler
`szMessage`\
'ndaki Hata ayıklayıcının çıkış penceresinde görüntülenecek ileti dizesi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugIDECallback](../../../extensibility/debugger/reference/idebugidecallback.md)
