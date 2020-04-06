---
title: IDebugProperty2::GetSize | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetSize
helpviewer_keywords:
- IDebugProperty2::GetSize
ms.assetid: 0deb8ec5-d6fb-4622-bb14-0c46b9459cc6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3f57a742bae0217493d8869b257e4a17839e4e14
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721337"
---
# <a name="idebugproperty2getsize"></a>IDebugProperty2::GetSize
Özellik değerinin boyutlarını, baytlar halinde alır.

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
[çıkış] Özellik değerinin boyutunu baytolarak verir.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde hata kodu döndürür. Özelliğin boyutu yoksa döndürür. `S_GETSIZE_NO_SIZE`

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
