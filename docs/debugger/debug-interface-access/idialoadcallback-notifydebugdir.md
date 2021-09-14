---
description: .exe dosyasında bir hata ayıklama dizini .exe çağrılır.
title: IDiaLoadCallback::NotifyDebugDir | Microsoft Docs
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126629637"
---
# <a name="idialoadcallbacknotifydebugdir"></a>IDiaLoadCallback::NotifyDebugDir
.exe dosyasında bir hata ayıklama dizini .exe çağrılır.

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

[in] `TRUE` hata ayıklama dizini yürütülebilir bir dosyadan (.dbg dosyası yerine) okunursa.

 `cbData`

[in] Hata ayıklama dizininde veri bayt sayısı.

 `data[]`

[in] Hata ayıklama diziniyle doldurulmuş bir dizi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür. Dönüş kodu genellikle yoksayılır.

## <a name="remarks"></a>Açıklamalar
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) yöntemi, yürütülebilir dosyayı işleme sırasında bir hata ayıklama dizini bulduğunda bu geri çağırmayı çağırır.

 Bu yöntem, istemcinin .pdb dosyasında bulunandan farklı hata ayıklama bilgilerini desteklemek için yürütülebilir dosya ve/veya hata ayıklama dosyasına ters mühendislik uygulama ihtiyacı ortadan kaldırır. Bu verilerle, istemci kullanılabilir hata ayıklama bilgileri türünü ve yürütülebilir dosyada mı yoksa .dbg dosyasında mı yer aladığını tanıyabilirsiniz.

 Çoğu istemcinin bu geri çağırmaya ihtiyacı yoktur çünkü yöntem sembollere hizmet vermek için gerektiğinde `IDiaDataSource::loadDataForExe` hem .pdb hem de .dbg dosyalarını saydam olarak açar.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
