---
title: POPDIRLISTFUNC | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- POPLISTFUNC
helpviewer_keywords:
- POPDIRLISTFUNC callback function
ms.assetid: 0ee90fd2-5467-4154-ab4c-7eb02ac3a14c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 52a0c16af0e142bda8527c5244a22e0830ced9e0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702073"
---
# <a name="popdirlistfunc"></a>POPDIRLISTFUNC
Bu, kaynak denetimi altında olan dizinler ve (isteğe bağlı) dosya adları koleksiyonunu güncelleştirmek için [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) işlevine verilen bir geri arama işlevidir.

 Geri `POPDIRLISTFUNC` arama yalnızca kaynak denetimi altında olan bu dizinler ve `SccPopulateDirList` dosya adları (işleve verilen listede) için çağrılmalıdır.

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

[içinde] [SccPopulateDirList'e](../extensibility/sccpopulatedirlist-function.md)verilen kullanıcı değeri.

 bKlasör

[içinde] `TRUE` adı bir `lpDirectoryOrFileName` dizin ise; aksi takdirde ad bir dosya adıdır.

 lpDirectoryOrFileName

[içinde] Kaynak kodu denetimi altında olan bir dizin veya dosya adına tam yerel yol.

## <a name="return-value"></a>Döndürülen değer
 IDE uygun bir hata kodu döndürür:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|İşleme devam edin.|
|SCC_I_OPERATIONCANCELED|İşlemi durdurun.|
|SCC_E_xxx|Uygun kaynak denetimi hatası işlemeyi durdurmalıdır.|

## <a name="remarks"></a>Açıklamalar
 İşlevin `fOptions` parametresi bayrağı `SCC_PDL_INCLUDEFILES` içeriyorsa, liste büyük olasılıkla dosya adlarının yanı sıra dizin adları da içerir. `SccPopulateDirList`

## <a name="see-also"></a>Ayrıca bkz.
- [IDE tarafından uygulanan geri arama işlevleri](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)
- [Hata kodları](../extensibility/error-codes.md)
