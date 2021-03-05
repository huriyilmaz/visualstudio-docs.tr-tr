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
ms.workload:
- multiple
ms.openlocfilehash: 1bf868f91d0eb8d1c80382632be40f348889ab12
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102147858"
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
