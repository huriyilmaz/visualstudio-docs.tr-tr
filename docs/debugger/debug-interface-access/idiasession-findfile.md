---
title: 'IDiaSession:: findFile | Microsoft Docs'
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
ms.workload:
- multiple
ms.openlocfilehash: d6358f1968b9ca2da04e5e0fff62b5a5f2acbb3f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99855216"
---
# <a name="idiasessionfindfile"></a>IDiaSession::findFile
Kaynak dosyalarını compiland ve adına göre alır.

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

'ndaki Arama için bağlam olarak kullanılacak compiland 'yi temsil eden bir [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) nesnesi. `NULL`Tüm uygulamalarda kaynak dosyaları bulmak için bu parametreyi olarak ayarlayın.

 `name`

'ndaki Alınacak kaynak dosyanın adını belirtir. Bu parametreyi, alınacak `NULL` tüm kaynak dosyaları için olarak ayarlayın.

 `option`

'ndaki Ad aramaya uygulanan karşılaştırma seçeneklerini belirtir. [NameSearchOptions numaralandırma](../../debugger/debug-interface-access/namesearchoptions.md) numaralandırmasındaki değerler tek başına veya birlikte kullanılabilir.

 `ppResult`

dışı Alınan kaynak dosyalarının listesini içeren bir [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

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