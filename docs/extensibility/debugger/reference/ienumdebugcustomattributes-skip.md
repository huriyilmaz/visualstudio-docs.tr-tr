---
description: Bir numaralama dizisinde belirtilen sayıda özel özniteliği atlar.
title: IEnumDebugCustomAttributes::Skip | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCustomAttributes::Skip
helpviewer_keywords:
- IEnumDebugCustomAttributes::Skip
ms.assetid: 54c72e23-cd4c-4746-935c-abea8057dd1b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 666929bded84a6f47bcffcac1b45993292c192fc
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122070565"
---
# <a name="ienumdebugcustomattributesskip"></a>IEnumDebugCustomAttributes::Skip
Bir numaralama dizisinde belirtilen sayıda özel özniteliği atlar.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Skip ( 
   ULONG celt
);
```

```csharp
int Skip(
   uint celt
);
```

## <a name="parameters"></a>Parametreler
`celt`\
[in] Atlana öğe sayısı.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür. kalan `S_FALSE` `celt` öğe sayısından büyükse döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Kalan öğe sayısından büyük bir değer belirtirse, en sona ayarlanır `celt` ve `S_FALSE` döndürülür.

## <a name="see-also"></a>Ayrıca bkz.
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
