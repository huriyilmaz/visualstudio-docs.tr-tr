---
title: 'IDiaSession:: findAcceleratorInlineesByName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: e203e5c2-6563-43fa-be56-3063955043ab
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 007477d3f0de3767b0c5ef0af977f969505884ed
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742306"
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

'ndaki @No__t_0 karşılık gelen satır içi çerçeveler aranırken kullanılacak ad arama seçenekleri. Daha fazla bilgi için bkz. [NameSearchOptions numaralandırması](../../debugger/debug-interface-access/namesearchoptions.md).

 `ppResult`

dışı Sonuçla başlatılan `IDiaEnumSymbols` arabirimi işaretçisine yönelik bir işaretçi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu işlev, yalnızca Hızlandırıcı saplama işlevleri içindeki ınlinees 'yi arar. Yerel C++ yordam kayıtlarını yoksayar.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)