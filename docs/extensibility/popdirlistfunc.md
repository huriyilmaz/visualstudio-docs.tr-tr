---
title: POPDIRLISTFUNC | Microsoft Docs
description: Kaynak denetimi altında bulunacak Dizin güncelleştirme dizinlerine geçirilen POPDIRLISTFUNC callback işlevi hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- POPLISTFUNC
helpviewer_keywords:
- POPDIRLISTFUNC callback function
ms.assetid: 0ee90fd2-5467-4154-ab4c-7eb02ac3a14c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0f8cde3e6835a7d3262bbb89fed13e0dbc8e540e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090258"
---
# <a name="popdirlistfunc"></a>POPDIRLISTFUNC
Bu, bir dizin koleksiyonunu ve (isteğe bağlı olarak) dosya adlarını güncelleştirmek için, kaynak denetimi altında olduğunu öğrenmek üzere [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) işlevine verilen bir geri çağırma işlevidir.

 `POPDIRLISTFUNC`Geri çağırma yalnızca kaynak denetimi altındaki dizinler ve dosya adları (işleve verilen listede) için çağrılmalıdır `SccPopulateDirList` .

## <a name="signature"></a>İmza

```cpp
typedef BOOL (*POPDIRLISTFUNC)(
   LPVOID pvCallerData,
   BOOL bFolder,
   LPCSTR lpDirectoryOrFileName
);
```

## <a name="parameters"></a>Parametreler
 pvCallerData

'ndaki [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)için Kullanıcı değeri verildi.

 bFolder

[in] `TRUE` içindeki ad `lpDirectoryOrFileName` bir dizin ise, ad bir dosya adıdır.

 lpDirectoryOrFileName

'ndaki Kaynak kodu denetimi altında bir dizin veya dosya adının tam yerel yolu.

## <a name="return-value"></a>Döndürülen değer
 IDE, uygun bir hata kodu döndürür:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|İşleme devam edin.|
|SCC_I_OPERATIONCANCELED|İşlemeyi durdur.|
|SCC_E_xxx|Uygun kaynak denetimi hatası işlemeyi durdurmalıdır.|

## <a name="remarks"></a>Açıklamalar
 `fOptions` `SccPopulateDirList` İşlevin parametresi `SCC_PDL_INCLUDEFILES` bayrağını içeriyorsa, liste büyük olasılıkla dosya adlarının yanı sıra dizin adlarını da içerir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDE tarafından uygulanan geri çağırma işlevleri](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)
- [Hata kodları](../extensibility/error-codes.md)
