---
description: Belirtilen satır içi işlev adına karşılık gelen satır içi çerçeveler için simgelerin bir listesini döndürür.
title: 'IDiaSession:: findAcceleratorInlineesByName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: e203e5c2-6563-43fa-be56-3063955043ab
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fb2a6c67dc9f16d3a4ef98d36772681d3ab2638e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102159029"
---
# <a name="idiasessionfindacceleratorinlineesbyname"></a>IDiaSession::findAcceleratorInlineesByName
Belirtilen satır içi işlev adına karşılık gelen satır içi çerçeveler için simgelerin bir listesini döndürür.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT findAcceleratorInlineeLinesByName ( 
   LPCOLESTR             name,
   DWORD                 option,
   IDiaEnumSymbols**     ppResult
);
```

#### <a name="parameters"></a>Parametreler
 `name`

'ndaki Aranacak ınlinee işlev adı.

 `option`

'ndaki Öğesine karşılık gelen satır içi çerçeveler aranırken kullanılacak ad arama seçenekleri `name` . Daha fazla bilgi için bkz. [NameSearchOptions numaralandırması](../../debugger/debug-interface-access/namesearchoptions.md).

 `ppResult`

dışı `IDiaEnumSymbols` Sonuçla başlatılan arabirim işaretçisine yönelik bir işaretçi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu işlev, yalnızca Hızlandırıcı saplama işlevleri içindeki ınlinees 'yi arar. Yerel C++ yordam kayıtlarını yoksayar.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
