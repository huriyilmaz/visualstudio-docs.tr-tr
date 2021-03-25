---
description: Bu yöntem, bu alanı eşitlik için belirtilen alanla karşılaştırır.
title: 'IDebugField:: eşittir | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::Equal
helpviewer_keywords:
- IDebugField::Equal method
ms.assetid: 75369fe6-ddd3-497d-80d1-2488e6100e9f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 58673703fa0e585095c9a82fe2c7a4bc3e14827c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077115"
---
# <a name="idebugfieldequal"></a>IDebugField::Equal
Bu yöntem, bu alanı eşitlik için belirtilen alanla karşılaştırır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Equal( 
   IDebugField* pField
);
```

```csharp
int Equal(
   IDebugField pField
);
```

## <a name="parameters"></a>Parametreler
`pField`\
'ndaki Bu ile Karşılaştırılacak alan.

## <a name="return-value"></a>Dönüş Değeri
 Alanlar aynıysa, döndürür `S_OK` . Alanlar farklıysa, `S_FALSE.` Aksi takdirde bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
