---
title: 'IDiaSourceFile:: get_compilands | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_compilands method
ms.assetid: 57deb50a-9c22-43ea-a80c-eab205997bc4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 89b3d85ab967185fb264491f57d6e6b59afad105
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85465302"
---
# <a name="idiasourcefileget_compilands"></a>IDiaSourceFile::get_compilands
Bu dosyaya başvuran satır numaralarına sahip olan compitika türlerini alır.

## <a name="syntax"></a>Söz dizimi

```C++
HRESULT get_compilands ( 
   IDiaEnumSymbols** ppRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `ppRetVal`

dışı Bu dosyaya başvuran satır numaralarına sahip tüm compslikler listesini içeren bir [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)