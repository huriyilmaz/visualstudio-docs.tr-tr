---
title: 'Ialoadcallback:: NotifyDebugDir | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::NotifyDebugDir method
ms.assetid: bd04e2f6-0dbf-4742-a556-96f2cd99aa19
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6618440cab9b9042ec371383f6c809ca1d0d11f7
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743085"
---
# <a name="idialoadcallbacknotifydebugdir"></a>IDiaLoadCallback::NotifyDebugDir
. Exe dosyasında bir hata ayıklama dizini bulunduğunda çağırılır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT NotifyDebugDir ( 
   BOOL  fExecutable,
   DWORD cbData,
   BYTE  data[]
);
```

#### <a name="parameters"></a>Parametreler
 `fExecutable`

[in] hata ayıklama dizini bir yürütülebilirden okunmasa (. dbg dosyası yerine) `TRUE`.

 `cbData`

'ndaki Hata ayıklama dizinindeki verilerin bayt sayısı.

 `data[]`

'ndaki Hata ayıklama diziniyle doldurulmuş bir dizi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; Aksi takdirde, bir hata kodu döndürür. Dönüş kodu genellikle yok sayılır.

## <a name="remarks"></a>Açıklamalar
 [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) yöntemi, yürütülebilir dosyayı işlerken bir hata ayıklama dizini bulduğunda bu geri aramayı çağırır.

 Bu yöntem,. pdb dosyasında bulunenden farklı hata ayıklama bilgilerini desteklemek için istemcinin yürütülebilir ve/veya hata ayıklama dosyasına ters mühendislik gerçekleştirmesine yönelik ihtiyacı ortadan kaldırır. Bu verilerle istemci, kullanılabilir hata ayıklama bilgileri türünü ve çalıştırılabilir dosyada veya. dbg dosyasında bulunup bulunamayacağını algılayabilir.

 @No__t_0 yöntemi, semboller için gerektiğinde hem. pdb hem de. dbg dosyaları saydam olarak açtığından, çoğu istemci bu geri aramaya ihtiyaç duymayacak.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)