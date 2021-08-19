---
description: Programa veya program düğümüne, bu programda hata ayıklamak için hangi hata ayıklama altyapısını (DE) kullanabileceğini söyler.
title: IDebugProgramEngines2::SetEngine | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2::SetEngine
helpviewer_keywords:
- IDebugProgramEngines2::SetEngine
ms.assetid: c05857ee-89cf-455e-8f1e-300cce4a2eab
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 04df0fe2c61b28eeb44ded883df4b0053633da0d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122126433"
---
# <a name="idebugprogramengines2setengine"></a>IDebugProgramEngines2::SetEngine
Programa veya program düğümüne, bu programda hata ayıklamak için hangi hata ayıklama altyapısını (DE) kullanabileceğini söyler.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT SetEngine( 
   REFGUID guidEngine
);
```

```csharp
int SetEngine( 
   ref Guid guidEngine
);
```

## <a name="parameters"></a>Parametreler
`guidEngine`\
[in] DE'nin GUID'si.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)
