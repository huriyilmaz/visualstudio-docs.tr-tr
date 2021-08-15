---
description: Bir dizeden başvurunun değerini ayarlar.
title: 'IDebugReference2:: SetValueAsString | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::SetValueAsString
helpviewer_keywords:
- IDebugReference2::SetValueAsString
ms.assetid: 9a508ced-fd54-44f5-bb42-ec15c80384d7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ad19f6e2f27f09128986c5b99d743061921b95eb7824ad816396860535eaecb1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121338520"
---
# <a name="idebugreference2setvalueasstring"></a>IDebugReference2::SetValueAsString
Bir dizeden başvurunun değerini ayarlar. Daha sonraki kullanımlar için ayrılmıştır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT SetValueAsString ( 
   LPCOLESTR pszValue,
   DWORD     dwRadix,
   DWORD     dwTimeout
);
```

```csharp
int SetValueAsString ( 
   string pszValue,
   uint   dwRadix,
   uint   dwTimeout
);
```

## <a name="parameters"></a>Parametreler
`pszValue`\
'ndaki Değer bir dize olarak.

`dwRadix`\
'ndaki Herhangi bir sayısal bilgiyi biçimlendirmede kullanılacak taban tabanı.

`dwTimeout`\
'ndaki Bu yöntemden dönmeden önce beklenecek en uzun süre (milisaniye cinsinden). `INFINITE`Sonsuza kadar beklemek için kullanın.

## <a name="return-value"></a>Dönüş Değeri
 Her zaman `E_NOTIMPL` döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
