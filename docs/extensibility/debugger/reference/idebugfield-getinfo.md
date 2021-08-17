---
description: Bu yöntem alanı hakkında değiştirilebilir bilgiler alır.
title: IDebugField::GetInfo | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: aa7d97c86c91a220b21c20a650a685d4c7b2fb73
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122138451"
---
# <a name="idebugfieldgetinfo"></a>IDebugField::GetInfo
Bu yöntem alanı hakkında değiştirilebilir bilgiler alır.

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
[in] Görüntülenecek [bilgileri FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md) sabitlerinin birleşimi. Alan bir simgeyi temsil ediyorsa, bu genellikle sembol adı ve türüdür.

`pFieldInfo`\
[out] Sağlanan veri yapısında [bilgileri FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)
