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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: da499ee9bbdcdff95456a4e4d5f5dc63f2acfb2c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99967403"
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
