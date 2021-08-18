---
description: Kaynak dosya tanımlayıcısına göre bir kaynak dosyası verir.
title: IDiaSession::findFileById | Microsoft Docs
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122066403"
---
# <a name="idiasessionfindfilebyid"></a>IDiaSession::findFileById
Kaynak dosya tanımlayıcısına göre bir kaynak dosyası verir.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT findFileById ( 
   DWORD            uniqueId,
   IDiaSourceFile** ppResult
);
```

#### <a name="parameters"></a>Parametreler
 `uniqueId`

[in] Kaynak dosya tanımlayıcısını belirtir.

 `ppResult`

[out] Alınan kaynak dosyayı temsil eden bir [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Kaynak dosya tanımlayıcısı, tüm kaynak dosyaları benzersiz yapmak için DIA SDK içinde kullanılan benzersiz bir değerdir. Bu yöntem genellikle uygulamanın içinde DIA SDK.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
