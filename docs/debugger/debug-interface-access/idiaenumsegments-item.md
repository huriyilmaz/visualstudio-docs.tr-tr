---
description: Bir segmenti dizin ile alma.
title: IDiaEnumSegments::Item | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments::Item method
ms.assetid: ee44dd55-39a0-4b7b-97ff-2e1226eeb2bd
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 454f79260201fcf9929f85d53aa5d9a4699c7b55
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122081640"
---
# <a name="idiaenumsegmentsitem"></a>IDiaEnumSegments::Item
Bir segmenti dizin ile alma.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT Item ( 
   DWORD         index,
   IDiaSegment** segment
);
```

#### <a name="parameters"></a>Parametreler
 dizin

[in] Alınan [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) nesnesinin dizini. Dizin 0 ile -1 aralığındadır `count` ve `count` burada [IDiaEnumSegments::get_Count](../../debugger/debug-interface-access/idiaenumsegments-get-count.md) yöntemi tarafından döndürülür.

 segment

[out] İstenen [segmenti temsil eden bir IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)
