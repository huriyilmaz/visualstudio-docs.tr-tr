---
description: .exe dosyasında bir hata ayıklama dizini bulunduğunda çağırılır.
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 48e87a968eea1ad35796a495d76584488bdac332
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122081544"
---
# <a name="idialoadcallbacknotifydebugdir"></a>IDiaLoadCallback::NotifyDebugDir
.exe dosyasında bir hata ayıklama dizini bulunduğunda çağırılır.

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
