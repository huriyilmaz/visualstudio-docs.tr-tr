---
title: IDebugArrayField::GetRank | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayField::GetRank
helpviewer_keywords:
- IDebugArrayField::GetRank method
ms.assetid: 2364b876-5be1-4bab-9b8f-3b6121da35c6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 692f2f13d861d9688ba349fbc80cb1ca426582c1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736302"
---
# <a name="idebugarrayfieldgetrank"></a>IDebugArrayField::GetRank
Dizinin sıralamasını veya boyut sayısını alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetRank( 
   DWORD* pdwRank
);
```

```csharp
int GetRank(
   out uint pdwRank
);
```

## <a name="parameters"></a>Parametreler
`pdwRank`\
[çıkış] Rütbeyi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, S_OK döndürür; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bir dizinin sıralaması boyut sayısına karşılık gelir. C++ ve C#'da, çok boyutlu diziler gerçekten dizilerdir ve bu nedenle sadece tek `GetRank` boyutlu bir dizi olarak kabul edilebilir (ve yöntem her zaman 1 döndürür). Diğer [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]taraftan, çok boyutlu diziler farklı şekilde işlenir ve bu tür bir dizinin sıralaması `GetRank` boyut sayısını yansıtır (ve yöntem her zaman boyut sayısını döndürür).

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)
