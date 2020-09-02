---
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
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8a45a31c02376f95c3cd6b0c4a4adf0434fabe92
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80729018"
---
# <a name="idebugfieldequal"></a>IDebugField::Equal
Bu yöntem, bu alanı eşitlik için belirtilen alanla karşılaştırır.

## <a name="syntax"></a>Söz dizimi

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
