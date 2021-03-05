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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d2bf9b3e4bbb988621e3b65e855b07322fba1795
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152097"
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
