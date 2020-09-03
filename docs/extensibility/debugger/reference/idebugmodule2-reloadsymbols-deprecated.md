---
title: 'IDebugModule2:: ReloadSymbols_Deprecated | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule2::ReloadSymbols
helpviewer_keywords:
- IDebugModule2::ReloadSymbols method
ms.assetid: 0f9f0133-7d58-4cd9-a6ca-1141e095749d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e776434e17d90cd2c61c926bbf0100a44ecc524b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80726925"
---
# <a name="idebugmodule2reloadsymbols_deprecated"></a>IDebugModule2::ReloadSymbols_Deprecated
Dışı. KULLANMAYıN. Bu modülün sembollerini yeniden yükler.

## <a name="syntax"></a>Söz dizimi

```cpp
HRESULT ReloadSymbols( 
   LPCOLESTR pszUrlToSymbols,
   BSTR*     pbstrDebugMessage
);
```

```csharp
int ReloadSymbols( 
   string     pszUrlToSymbols,
   out string pbstrDebugMessage
);
```

## <a name="parameters"></a>Parametreler
`pszUrlToSymbols`\
'ndaki Sembol deposunun yolu.

`pbstrDebugMessage`\
dışı Modüller penceresinde modül adının sağında görüntülenen durum veya hata iletisi gibi bir bilgi iletisi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür. Bir hata ayıklama altyapısı her zaman döndürmelidir `E_FAIL` .

## <a name="remarks"></a>Açıklamalar
 Bu yöntem artık desteklenmiyor. Bunun yerine [LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md) metodunu uygulayın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)
