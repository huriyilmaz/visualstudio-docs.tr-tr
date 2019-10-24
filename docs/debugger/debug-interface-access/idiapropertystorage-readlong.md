---
title: 'IDiaPropertyStorage:: ReadLONG | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadLONG
ms.assetid: 32054cbc-db55-4513-a1b4-de80e77aac8a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: af9d65c571c5e0a281b968d922c9b5170bd1c561
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742897"
---
# <a name="idiapropertystoragereadlong"></a>IDiaPropertyStorage::ReadLONG
Bir özellik kümesindeki `LONG` değerleri okur.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT ReadDLONG ( 
   PROPID id,
   LONG*  pValue
);
```

#### <a name="parameters"></a>Parametreler
 `id`

'ndaki Okunacak özelliğin tanımlayıcısı (`PROPID` `ULONG` olarak WTypes. h içinde tanımlanmıştır).

 `pValue`

dışı Özellik değerini döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; Aksi takdirde bir hata kodu döndürür. Özellik `LONG` türünde değilse `E_INVALIDARG` döndürür.

## <a name="remarks"></a>Açıklamalar
 @No__t_0, Windows tarafından 32 bitlik işaretli bir tamsayı olarak tanımlanır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)