---
title: POPDIRLISTFUNC | Microsoft Docs
description: Kaynak denetimi altında olanları bulmak için dizinleri güncelleştirmeye geçirilen POPDIRLISTFUNC geri çağırma işlevini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- POPLISTFUNC
helpviewer_keywords:
- POPDIRLISTFUNC callback function
ms.assetid: 0ee90fd2-5467-4154-ab4c-7eb02ac3a14c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: af9e4c350801b7ee14c577194d4df384d7bb42a7
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122158508"
---
# <a name="popdirlistfunc"></a>POPDIRLISTFUNC
Bu, bir dizin koleksiyonunu ve (isteğe bağlı olarak) dosya adlarını güncelleştiren [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) işlevine verilen ve kaynak denetimi altında olan dosyaları bulmak için verilen bir geri çağırma işlevidir.

 Geri çağırma yalnızca kaynak denetimi altında olan dizinler ve dosya adları `POPDIRLISTFUNC` (işleve verilen `SccPopulateDirList` listede) için çağrılmalıdır.

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

[in] [SccPopulateDirList'e verilen kullanıcı değeri.](../extensibility/sccpopulatedirlist-function.md)

 bFolder

[in] `TRUE` içinde ad bir `lpDirectoryOrFileName` dizin ise, aksi takdirde ad bir dosya adıdır.

 lpDirectoryOrFileName

[in] Kaynak kodu denetimi altında olan bir dizin veya dosya adının tam yerel yolu.

## <a name="return-value"></a>Döndürülen değer
 IDE uygun bir hata kodu döndürür:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|İşlemeye devam.|
|SCC_I_OPERATIONCANCELED|İşlemeyi durdurun.|
|SCC_E_xxx|Uygun kaynak denetimi hataları işlemeyi durdurmalıdır.|

## <a name="remarks"></a>Açıklamalar
 İşlevin `fOptions` parametresi `SccPopulateDirList` bayrağını `SCC_PDL_INCLUDEFILES` içeriyorsa, liste hem dosya adlarını hem de dizin adlarını içerir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDE tarafından uygulanan geri çağırma işlevleri](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)
- [Hata kodları](../extensibility/error-codes.md)
