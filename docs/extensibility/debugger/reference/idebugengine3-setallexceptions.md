---
description: Bu yöntem, tüm bekleyen özel durumların durumunu ayarlar.
title: 'IDebugEngine3:: SetAllExceptions | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetAllExceptions
helpviewer_keywords:
- IDebugEngine3::SetAllExceptions
ms.assetid: 8f03a6ac-a854-42f7-933c-a2df1b351975
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2662631a4c3b5ab4420fc5f14740138596435d77
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122111092"
---
# <a name="idebugengine3setallexceptions"></a>IDebugEngine3::SetAllExceptions
Bu yöntem, tüm bekleyen özel durumların durumunu ayarlar.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT SetAllExceptions(
   EXCEPTION_STATE dwState
);
```

```csharp
int SetAllExceptions(
   enum_EXCEPTION_STATE dwState
);
```

## <a name="parameters"></a>Parametreler
`dwState`\
'ndaki [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md) değerlerinden biri.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
- [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md)
