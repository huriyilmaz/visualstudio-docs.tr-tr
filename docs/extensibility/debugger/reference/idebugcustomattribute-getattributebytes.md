---
description: Öznitelik bilgilerini bayt blobu olarak alır.
title: IDebugCustomAttribute::GetAttributeBytes | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetAttributeBytes
helpviewer_keywords:
- IDebugCustomAttribute::GetAttributeBytes
ms.assetid: cf34583b-6530-4dcc-89f8-eb27e4e8d594
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bbb962a31061c24fc9b51e56b0b5c63c25f2a27a
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725244"
---
# <a name="idebugcustomattributegetattributebytes"></a>IDebugCustomAttribute::GetAttributeBytes
Öznitelik bilgilerini bayt blobu olarak alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetAttributeBytes( 
   BYTE*  ppBlob,
   DWORD* pdwLen
);
```

```csharp
int GetAttributeBytes(
   ref byte[] ppBlob,
   ref uint   pdwLen
);
```

## <a name="parameters"></a>Parametreler
`ppBlob`\
[in, out] Öznitelik baytları ile doldurulmuş bir dizi.

`pdwLen`\
[in, out] Dizide döndüren en fazla bayt sayısını `ppBlob` belirtir ve aslında diziye yazılan bayt sayısını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, S_OK; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Kullanılabilir `ppBlob` öznitelik baytlarının sayısını döndüren parametreyi null değere ayarlayın. Ardından bir dizi ayırarak parametresi için bu diziyi `ppBlob` iletir.

 Öznitelik baytları, özel özniteliğin ham verilerini temsil eder.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
