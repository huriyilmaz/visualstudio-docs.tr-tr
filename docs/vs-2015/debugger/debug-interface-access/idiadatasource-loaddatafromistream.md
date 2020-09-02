---
title: 'IDiaDataSource:: Loaddatafromistread | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadDataFromIStream method
ms.assetid: 8fe33eea-1457-4b8c-ae19-f1ede5578483
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 35644f06ae929e4168d5dc44d6fc488de020a637
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62547461"
---
# <a name="idiadatasourceloaddatafromistream"></a>IDiaDataSource::loadDataFromIStream
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bellek içi veri akışı aracılığıyla erişilen bir program veritabanı (. pdb) dosyasında depolanan hata ayıklama verilerini hazırlar.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT loadDataFromIStream (   
   IStream* pIStream  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 pIStream  
 'ndaki <xref:IStream> Kullanılacak veri akışını temsil eden nesne.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür. Aşağıdaki tabloda bu yöntem için olası dönüş değerleri gösterilmektedir.  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|E_PDB_FORMAT|Eski biçimdeki bir dosyaya erişme girişiminde bulunuldu.|  
|E_INVALIDARG|Geçersiz parametre.|  
|E_UNEXPECTED|Veri kaynağı zaten hazırlandı.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, bir yürütülebilir dosya için hata ayıklama verilerinin bir nesne aracılığıyla bellekten elde etmesine olanak tanır <xref:IStream> .  
  
 Bir. pdb dosyasını doğrulama olmadan yüklemek için [IDiaDataSource:: loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) metodunu kullanın.  
  
 . Pdb dosyasını belirli ölçütlere karşı doğrulamak için [IDiaDataSource:: loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) metodunu kullanın.  
  
 Veri yükleme işlemine (bir geri çağırma mekanizması aracılığıyla) erişim kazanmak için [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) metodunu kullanın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaDataSource:: loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)   
 [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)
