---
description: Kaynak dosya tanımlayıcısına göre bir kaynak dosyası alır.
title: 'IDiaSession:: Findfilebyıd | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findFileById method
ms.assetid: 710efe04-78b5-4f3e-a1d8-f9b069063503
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 2e34d25ea59b20eebc986106123070dd1d23b9dd
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126629258"
---
# <a name="idiasessionfindfilebyid"></a>IDiaSession::findFileById
Kaynak dosya tanımlayıcısına göre bir kaynak dosyası alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT findFileById ( 
   DWORD            uniqueId,
   IDiaSourceFile** ppResult
);
```

#### <a name="parameters"></a>Parametreler
 `uniqueId`

'ndaki Kaynak dosya tanımlayıcısını belirtir.

 `ppResult`

dışı Alınan kaynak dosyayı temsil eden bir [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Kaynak dosya tanımlayıcısı, tüm kaynak dosyalarını benzersiz hale getirmek için DIA SDK dahili olarak kullanılan benzersiz bir değerdir. Bu yöntem genellikle DIA SDK için dahili olarak kullanılır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
