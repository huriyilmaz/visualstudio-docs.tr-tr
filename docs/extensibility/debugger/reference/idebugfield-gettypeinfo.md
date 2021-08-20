---
description: Bu yöntem sembol veya tür hakkında türden bağımsız bilgiler alır.
title: IDebugField::GetTypeInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetTypeInfo
helpviewer_keywords:
- IDebugField::GetTypeInfo method
ms.assetid: bb5acfa3-04c3-4088-be84-9ff8926cd16f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8403a6eca0be5089d448c938720981b59862b404
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122138373"
---
# <a name="idebugfieldgettypeinfo"></a>IDebugField::GetTypeInfo
Bu yöntem sembol veya tür hakkında türden bağımsız bilgiler alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetTypeInfo( 
   TYPE_INFO* pTypeInfo
);
```

```csharp
int GetTypeInfo(
   TYPE_INFO[] pTypeInfo
);
```

## <a name="parameters"></a>Parametreler
`pTypeInfo`\
[out] Sağlanan veri türü yapısında [tür TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Türünden bağımsız bilgiler AppDomain, modül ve sembolünü içeren sınıfı içerebilir.

## <a name="see-also"></a>Ayrıca bkz.
- [GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
