---
title: 'IDebugProcess2:: CanDetach | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::CanDetach
helpviewer_keywords:
- IDebugProcess2::CanDetach
ms.assetid: 2830f7c3-69fb-474a-97b8-5b869e38d546
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2bfb7b7b586f9c8b86e75d453389525c61a63bc4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80724178"
---
# <a name="idebugprocess2candetach"></a>IDebugProcess2::CanDetach
Oturum hata ayıklama yöneticisinin (SDM) işlemi ayırabileceğini belirler.

## <a name="syntax"></a>Syntax

```cpp
HRESULT CanDetach(
   void
);
```

```csharp
int CanDetach();
```

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK.` `S_FALSE` hata ayıklayıcı işlemden ayıramaması halinde döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [CanDetach](../../../extensibility/debugger/reference/idebugprogram2-candetach.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
