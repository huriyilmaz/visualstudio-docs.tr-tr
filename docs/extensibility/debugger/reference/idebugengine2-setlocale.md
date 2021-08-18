---
description: Hata ayıklama altyapısının (DE) yerel ayar ayarlar.
title: IDebugEngine2::SetLocale | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::SetLocale
helpviewer_keywords:
- IDebugEngine2::SetLocale
ms.assetid: cd0d2cf1-2aac-43da-a830-4bb3d696c219
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c43a1a6952d39106db555a40bbe2d30ccee52d48
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122096381"
---
# <a name="idebugengine2setlocale"></a>IDebugEngine2::SetLocale
Hata ayıklama altyapısının (DE) yerel ayar ayarlar.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT SetLocale( 
   WORD wLangID
);
```

```csharp
int SetLocale( 
   ushort wLangID
);
```

## <a name="parameters"></a>Parametreler
`wLangID`\
[in] Dil yerel ayarı belirtir. Örneğin, İngilizce için 1033.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, DE tarafından döndürülen dizelerin düzgün yerelleştirilmiş olması için IDE'nin yerel ayar ayarlarını yayma için oturum hata ayıklama yöneticisi (SDM) tarafından çağrılır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
