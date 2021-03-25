---
description: Bu sunucuyla ilişkili tüm hata ayıklama motorları için otomatik eklemeyi devre dışı bırakır.
title: 'IDebugCoreServer3: Isableoto Attach:D | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::DisableAutoAttach
helpviewer_keywords:
- IDebugCoreServer3::DisableAutoAttach
ms.assetid: 9d860a20-c154-4df4-ba15-636e0fcd42bf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 88f21dbed27b0ec525f127933cd9a5fc28ed5646
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077674"
---
# <a name="idebugcoreserver3disableautoattach"></a>IDebugCoreServer3::DisableAutoAttach
Bu sunucuyla ilişkili tüm hata ayıklama motorları için otomatik eklemeyi devre dışı bırakır.

## <a name="syntax"></a>Syntax

```cpp
HRESULT DisableAutoAttach(
   void
);
```

```csharp
int DisableAutoAttach();
```

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
