---
title: 'Ialoadcallback:: NotifyDebugDir | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 032e628512b7c601a6409f6f70ba0b0c3cabb37c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85466758"
---
# <a name="idialoadcallbacknotifydebugdir"></a>IDiaLoadCallback::NotifyDebugDir
. Exe dosyasında bir hata ayıklama dizini bulunduğunda çağırılır.

## <a name="syntax"></a>Söz dizimi

```C++
HRESULT NotifyDebugDir ( 
   BOOL  fExecutable,
   DWORD cbData,
   BYTE  data[]
);
```

#### <a name="parameters"></a>Parametreler
 `fExecutable`

[in] `TRUE` hata ayıklama dizini bir yürütülebilir dosyadan (. dbg dosyası yerine) okunmalıdır.

 `cbData`

'ndaki Hata ayıklama dizinindeki verilerin bayt sayısı.

 `data[]`

'ndaki Hata ayıklama diziniyle doldurulmuş bir dizi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür. Dönüş kodu genellikle yok sayılır.

## <a name="remarks"></a>Açıklamalar
 [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) yöntemi, yürütülebilir dosyayı işlerken bir hata ayıklama dizini bulduğunda bu geri aramayı çağırır.

 Bu yöntem,. pdb dosyasında bulunenden farklı hata ayıklama bilgilerini desteklemek için istemcinin yürütülebilir ve/veya hata ayıklama dosyasına ters mühendislik gerçekleştirmesine yönelik ihtiyacı ortadan kaldırır. Bu verilerle istemci, kullanılabilir hata ayıklama bilgileri türünü ve çalıştırılabilir dosyada veya. dbg dosyasında bulunup bulunamayacağını algılayabilir.

 Bu geri aramaya gerek kalmaz çünkü `IDiaDataSource::loadDataForExe` Yöntem, sembolleri sağlamak için gerektiğinde. pdb ve. dbg dosyaları saydam bir şekilde açar.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)