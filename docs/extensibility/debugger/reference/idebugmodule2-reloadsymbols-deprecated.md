---
description: Dışı. Bu modülün sembollerini yeniden yükler.
title: 'IDebugModule2:: ReloadSymbols_Deprecated | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule2::ReloadSymbols
helpviewer_keywords:
- IDebugModule2::ReloadSymbols method
ms.assetid: 0f9f0133-7d58-4cd9-a6ca-1141e095749d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5cf3e19bc9417813581b1f513c60e3d550a6dd6d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122051033"
---
# <a name="idebugmodule2reloadsymbols_deprecated"></a>IDebugModule2::ReloadSymbols_Deprecated
Dışı. KULLANMAYıN. Bu modülün sembollerini yeniden yükler.

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
