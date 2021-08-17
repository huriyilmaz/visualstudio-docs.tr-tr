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
ms.openlocfilehash: df38c3d18f18f7c1c2bda021a8827fe76305c4c2cdd6fd2fce3e76269acf7c5d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121391859"
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
