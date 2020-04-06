---
title: IDebugCustomAttribute::GetAttributeBytes | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetAttributeBytes
helpviewer_keywords:
- IDebugCustomAttribute::GetAttributeBytes
ms.assetid: cf34583b-6530-4dcc-89f8-eb27e4e8d594
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 621ebf3949a273e06053ced67209aa052c25bce0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732800"
---
# <a name="idebugcustomattributegetattributebytes"></a>IDebugCustomAttribute::GetAttributeBytes
Öznitelik bilgilerini bayt damlası olarak alır.

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
[içinde, dışarı] Öznitelik baytlarıyla doldurulmuş bir dizi.

`pdwLen`\
[içinde, dışarı] `ppBlob` Dizide döndürülecek maksimum bayt sayısını belirtir ve diziye gerçekten yazılmış bayt sayısını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, S_OK döndürür; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Kullanılabilir `ppBlob` öznitelik bayt sayısını döndürmek için parametreyi null değerine ayarlayın. Ardından bir dizi ayırın ve bu `ppBlob` diziyi parametre için geçirin.

 Öznitelik baytlar, özel özniteliğin ham verilerini temsil eder.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
