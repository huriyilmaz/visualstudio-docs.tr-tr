---
description: Geçerli numaralayıcıyla aynı numaralama durumunu içeren bir numaralayıcı oluşturur.
title: IDiaEnumSegments::Clone | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments::Clone method
ms.assetid: 93deaac6-72ab-4408-ba14-66174a618757
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: ecef9448b03df8238259bd8a9c5df8011e40c946
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122081656"
---
# <a name="idiaenumsegmentsclone"></a>IDiaEnumSegments::Clone
Geçerli numaralayıcıyla aynı numaralama durumunu içeren bir numaralayıcı oluşturur.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT Clone ( 
   IDiaEnumSegments** ppenum
);
```

#### <a name="parameters"></a>Parametreler
 ppenum

[out] Numaralayıcının bir kopyasını içeren bir [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md) nesnesi döndürür. Segmentler çoğaltılmış değil, yalnızca numaralayıcı.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)
