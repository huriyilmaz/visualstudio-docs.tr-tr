---
description: Bölüm katkılarını bir dizin ile alın.
title: IDiaEnumSectionContribs::Item | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSectionContribs::Item method
ms.assetid: 63a28f23-0ca0-44a7-b11b-ca0206d642a0
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 6571032ba973e4d3c34b07494ed7c5eec2ec910e4f2663d93876c54dbbefc60e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121380393"
---
# <a name="idiaenumsectioncontribsitem"></a>IDiaEnumSectionContribs::Item
Bölüm katkılarını bir dizin ile alın.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT Item ( 
   DWORD                index,
   IDiaSectionContrib** section
);
```

#### <a name="parameters"></a>Parametreler
 dizin

[in] [Alınan IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md) nesnesinin dizini. Dizin 0 ile `count` -1 `count` aralığındadır; burada [IDiaEnumSectionContribs::get_Count yöntemi tarafından](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-count.md) döndürülür.

 section

[out] İstenen bölüm [katkısını temsil eden bir IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaEnumSectionContribs::get_Count](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-count.md)
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)
