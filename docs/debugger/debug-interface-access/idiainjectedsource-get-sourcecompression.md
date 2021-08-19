---
description: Kullanılan kaynak sıkıştırma göstergesini alın.
title: IDiaInjectedSource::get_sourceCompression | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_sourceCompression method
ms.assetid: 854b142f-23a9-466c-bf7f-98e581d5abcd
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: e227b830f516077a2b168e0ecb7e3cbec09f7ea1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122161749"
---
# <a name="idiainjectedsourceget_sourcecompression"></a>IDiaInjectedSource::get_sourceCompression
Kullanılan kaynak sıkıştırma göstergesini alın.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_sourceCompression ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

[out] Kullanılan kaynak sıkıştırma göstergesini döndürür. Sıfır değeri, kaynak sıkıştırma kullanılmadı ifadesini gösterir.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür. Bu `S_FALSE` özellik desteklenmiyorsa döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem tarafından döndürülen değer, kullanılan derleyiciye özeldir. Örneğin, bir derleyici Run-Length Encoding veya Huffman stili sıkıştırma kullanabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)
