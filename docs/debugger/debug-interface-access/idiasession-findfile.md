---
description: Kaynak dosyaları compiland ve name'e göre alınır.
title: IDiaSession::findFile | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findFile method
ms.assetid: a215dc21-b316-40d7-9923-55bfa014976b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: eddff6e842bdf29bfe07d7219e5cca5861be16ed4634d26f7ccdb02bdbdb0ec9
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121391867"
---
# <a name="idiasessionfindfile"></a>IDiaSession::findFile
Kaynak dosyaları compiland ve name'e göre alınır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT findFile ( 
   IDiaSymbol*           pCompiland,
   LPCOLESTR             name,
   DWORD                 option,
   IDiaEnumSourceFiles** ppResult
);
```

#### <a name="parameters"></a>Parametreler
 `pCompiland`

[in] Arama için bağlam olarak kullanılacak derlemeyi temsil eden [bir IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) nesnesi. Tüm derlemelerde `NULL` kaynak dosyaları bulmak için bu parametreyi olarak ayarlayın.

 `name`

[in] Alınan kaynak dosyanın adını belirtir. Tüm kaynak dosyalarının `NULL` alınsı için bu parametreyi olarak ayarlayın.

 `option`

[in] Ad arama için uygulanan karşılaştırma seçeneklerini belirtir. [NameSearchOptions Enumeration enumeration](../../debugger/debug-interface-access/namesearchoptions.md) değerleri tek başına veya birlikte kullanılabilir.

 `ppResult`

[out] Alınan kaynak dosyaların listesini içeren bir [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="example"></a>Örnek

```C++
IDiaEnumSourceFiles* pEnum;
pSession->findFile( NULL, L"sourcefile.cpp", nsFNameExt, &pEnum );
```

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [NameSearchOptions Numaralandırması](../../debugger/debug-interface-access/namesearchoptions.md)
