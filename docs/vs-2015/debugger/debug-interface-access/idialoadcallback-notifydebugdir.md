---
title: 'Ialoadcallback:: NotifyDebugDir | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::NotifyDebugDir method
ms.assetid: bd04e2f6-0dbf-4742-a556-96f2cd99aa19
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2e8fe8ffe9d7d495e40c8c84b08aeaefb03e8d17
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152006"
---
# <a name="idialoadcallbacknotifydebugdir"></a>IDiaLoadCallback::NotifyDebugDir
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

. Exe dosyasında bir hata ayıklama dizini bulunduğunda çağırılır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
