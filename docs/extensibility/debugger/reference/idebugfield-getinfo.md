---
description: Bu yöntem, alanla ilgili görüntülenebilen bilgileri alır.
title: 'IDebugField:: GetInfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetInfo
helpviewer_keywords:
- IDebugField::GetInfo method
ms.assetid: 7d508200-89ce-400f-a8ea-f28e7610cb2b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: deebf0c8dafe64c8eb78ba5a1af0b8f96c70a18a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077063"
---
# <a name="idebugfieldgetinfo"></a>IDebugField::GetInfo
Bu yöntem, alanla ilgili görüntülenebilen bilgileri alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetInfo( 
   FIELD_INFO_FIELDS dwFields,
   FIELD_INFO* pFieldInfo
);
```

```csharp
int GetInfo(
   enum_FIELD_INFO_FIELDS dwFields,
   FIELD_INFO[] pFieldInfo
);
```

## <a name="parameters"></a>Parametreler
`dwFields`\
'ndaki Görüntülenecek bilgileri seçen [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md) sabitlerin birleşimi. Alan bir sembolü temsil ediyorsa, bu genellikle sembol adı ve türüdür.

`pFieldInfo`\
dışı Sağlanan [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) yapısındaki bilgileri döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)
