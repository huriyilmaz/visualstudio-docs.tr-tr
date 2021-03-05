---
description: Özellik değerinin bayt cinsinden boyutunu alır.
title: 'IDebugProperty2:: GetSize | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetSize
helpviewer_keywords:
- IDebugProperty2::GetSize
ms.assetid: 0deb8ec5-d6fb-4622-bb14-0c46b9459cc6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fd6342efd1d9bcb2d2ac063438ee741df3c61325
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166820"
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
dışı Özellik değerinin bayt cinsinden boyutunu döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde hata kodu döndürür. `S_GETSIZE_NO_SIZE`Özelliğin boyutu yoksa döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
