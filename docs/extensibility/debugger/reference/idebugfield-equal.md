---
description: Bu yöntem, eşitlik için bu alanı belirtilen alanla karşılaştırıldığında.
title: IDebugField::Equal | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f9625aa138330f8504dd90371808a62f8c50ee9c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122138464"
---
# <a name="idebugfieldequal"></a>IDebugField::Equal
Bu yöntem, eşitlik için bu alanı belirtilen alanla karşılaştırıldığında.

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
[in] Bu alanla karşılaştıran alan.

## <a name="return-value"></a>Dönüş Değeri
 Alanlar aynı ise `S_OK` döndürür. Alanlar farklı ise Aksi takdirde `S_FALSE.` döndürür ve bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
