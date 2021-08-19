---
description: Özellik değerinin bayt cinsinden boyutunu alır.
title: IDebugProperty2::GetSize | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetSize
helpviewer_keywords:
- IDebugProperty2::GetSize
ms.assetid: 0deb8ec5-d6fb-4622-bb14-0c46b9459cc6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6be8ee81d38be6bb642ba4178a2793fb5d482f0b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122071291"
---
# <a name="idebugproperty2getsize"></a>IDebugProperty2::GetSize
Özellik değerinin bayt cinsinden boyutunu alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetSize ( 
   DWORD* pdwSize
);
```

```csharp
int GetSize ( 
   out uint pdwSize
);
```

## <a name="parameters"></a>Parametreler
`pdwSize`\
[out] Özellik değerinin bayt cinsinden boyutunu döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde hata kodunu döndürür. Özelliğin `S_GETSIZE_NO_SIZE` boyutu yoksa döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
