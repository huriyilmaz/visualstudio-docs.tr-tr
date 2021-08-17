---
description: Başvuru türünü ayarlar.
title: 'IDebugReference2:: SetReferenceType | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::SetReferenceType
helpviewer_keywords:
- IDebugReference2::SetReferenceType
ms.assetid: 5854a172-ea82-481c-97d9-c7fc16923d44
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 94aacf23397c2599acd44b8197d2d2af0f157ea1d61ba13becedb44ad03d002d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121338546"
---
# <a name="idebugreference2setreferencetype"></a>IDebugReference2::SetReferenceType
Başvuru türünü ayarlar. Daha sonraki kullanımlar için ayrılmıştır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT SetReferenceType ( 
   REFERENCE_TYPE dwRefType
);
```

```csharp
int SetReferenceType ( 
   enum_REFERENCE_TYPE dwRefType
);
```

## <a name="parameters"></a>Parametreler
`dwRefType`\
'ndaki [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md) numaralandırmasından başvuru türünü belirten bir değer.

## <a name="return-value"></a>Dönüş Değeri
 Her zaman `E_NOTIMPL` döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md)
