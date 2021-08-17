---
description: Belirtilen satır içi işlev adına karşılık gelen satır içi çerçeveler için simgelerin bir sabit adını döndürür.
title: IDiaSession::findAcceleratorInlineesByName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: e203e5c2-6563-43fa-be56-3063955043ab
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: a83574d5b36853a62206152cea74dd0a3d85f9a9f8c771e1769afd724b87ad36
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121391891"
---
# <a name="idiasessionfindacceleratorinlineesbyname"></a>IDiaSession::findAcceleratorInlineesByName
Belirtilen satır içi işlev adına karşılık gelen satır içi çerçeveler için simgelerin bir sabit adını döndürür.

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

[in] Aranacak satır içi işlev adı.

 `option`

[in] 'a karşılık gelen satır içi çerçeveler için arama yapmak için kullanılacak ad arama `name` seçenekleri. Daha fazla bilgi için [bkz. NameSearchOptions Enumeration](../../debugger/debug-interface-access/namesearchoptions.md).

 `ppResult`

[out] Sonuçla başlatılan `IDiaEnumSymbols` bir arabirim işaretçisinin işaretçisi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu işlev yalnızca Hızlandırıcı saplama işlevleri içinde satır içi aramalar. Yerel C++ yordam kayıtlarını yoksayıyor.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
