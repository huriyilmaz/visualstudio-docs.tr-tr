---
title: İDebugModülü2::ReloadSymbols_Deprecated | Microsoft Dokümanlar
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726925"
---
# <a name="idebugmodule2reloadsymbols_deprecated"></a>IDebugModule2::ReloadSymbols_Deprecated
Eski. KULLANMAYıN. Bu modül için sembolleri yeniden yükler.

## <a name="syntax"></a>Sözdizimi

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
[içinde] Sembol deposuna giden yol.

`pbstrDebugMessage`\
[çıkış] Modüller penceresinde modül adının sağında görüntülenen durum veya hata iletisi gibi bir bilgilendirme iletisi verir.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür. Hata ayıklama motoru `E_FAIL`her zaman geri dönmelidir.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem artık desteklenmiş. Bunun yerine [LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md) yöntemini uygulayın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)
