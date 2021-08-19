---
description: Bir dizin yoluyla bölüm katkılarını alır.
title: 'IDiaEnumSectionContribs:: Item | Microsoft Docs'
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
ms.openlocfilehash: c18f39898347313784e6201aedbc02018771e6f5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122036498"
---
# <a name="idiaenumsectioncontribsitem"></a>IDiaEnumSectionContribs::Item
Bir dizin yoluyla bölüm katkılarını alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT Item ( 
   DWORD                index,
   IDiaSectionContrib** section
);
```

#### <a name="parameters"></a>Parametreler
 dizin

'ndaki Alınacak [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md) nesnesinin dizini. Dizin, `count` `count` [ıdiaenumsectioncontribs:: get_Count](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-count.md) yöntemi tarafından döndürülen 0 ile-1 aralığındadır.

 section

dışı İstenen bölüm katkısını temsil eden bir [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaEnumSectionContribs::get_Count](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-count.md)
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)
