---
title: IDebugDocumentText2::GetSize | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentText2::GetSize
helpviewer_keywords:
- IDebugDocumentText2::GetSize
ms.assetid: bf515a8f-dcee-4004-8f81-543d547ceaae
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: edc4a209537ca4bd54d3f6d9343d1496ab7c0e90
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731586"
---
# <a name="idebugdocumenttext2getsize"></a>IDebugDocumentText2::GetSize
Belgedeki bu konumdaki metnin boyutunu alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetSize( 
   ULONG* pcNumLines,
   ULONG* pcNumChars
);
```

```csharp
int GetSize( 
   ref uint pcNumLines,
   ref uint pcNumChars
);
```

## <a name="parameters"></a>Parametreler
`pcNumLines`\
[çıkış] Metin satırlarının sayısını döndürür.

`pcNumChars`\
[çıkış] Metnin karakter sayısını verir.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar

 [Yalnızca C++ ] Belirli bir değer istenmiyorsa, parametre için bir NULL geçirin.

 [Yalnızca C# ] Her iki parametre belirtilmelidir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)
