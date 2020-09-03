---
title: 'Idebuggenericfieldınstance:: GetTypeArguments | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetTypeArguments
- IDebugGenericFieldInstance::GetTypeArguments
ms.assetid: 6e7e0f95-181a-4805-adb3-c2407de0ab93
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c41a3f314f641ed4bff116959b6d70f0a5fb9dcb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80728186"
---
# <a name="idebuggenericfieldinstancegettypearguments"></a>IDebugGenericFieldInstance::GetTypeArguments
Bu örnek için tür parametresi bağımsız değişkenlerini alır.

## <a name="syntax"></a>Söz dizimi

```cpp
HRESULT GetTypeArguments(
   ULONG32       cArgs,
   IDebugField** ppArgs,
   ULONG32*      pcArgs
);
```

```csharp
int GetTypeArguments(
   uint              cArgs,
   out IDebugField[] ppArgs,
   ref uint          pcArgs
);
```

## <a name="parameters"></a>Parametreler
`cArgs`\
'ndaki Tür parametrelerinin sayısı.

`ppArgs`\
dışı Parametre türünde bir dizi döndürür.

`pcArgs`\
[in, out] Dizideki üye sayısı `ppArgs` .

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)
