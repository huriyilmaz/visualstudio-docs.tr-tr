---
description: Geçerli tablo numaralayıcı ile aynı numaralama durumunu içeren bir numaralayıcı oluşturur.
title: IDiaEnumTables::Clone | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::Clone method
ms.assetid: beb21109-b12c-44d8-8c1f-a332216b3713
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 19922dcb8c8f280ce57dd32d02bd8dcf6737698b
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126629954"
---
# <a name="idiaenumtablesclone"></a>IDiaEnumTables::Clone
Geçerli numaralayıcıyla aynı numaralama durumunu içeren bir numaralayıcı oluşturur.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT Clone ( 
   IDiaEnumTables** ppenum
);
```

#### <a name="parameters"></a>Parametreler
 `ppenum`

[out] Numaralayıcının bir kopyasını içeren bir [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md) nesnesi döndürür. Tablolar çoğaltılmış değil, yalnızca numaralayıcı.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)
