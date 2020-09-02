---
title: 'IDiaPropertyStorage:: ReadMultiple | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadMultiple
ms.assetid: 6ccc9397-ce41-4f72-b261-72ac252cd4a5
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 40cd84e00f2e6abea285368a6206c7400abf8877
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538089"
---
# <a name="idiapropertystoragereadmultiple"></a>IDiaPropertyStorage::ReadMultiple
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Geçerli özellik kümesinden belirtilen özellikleri okur.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT ReadMultiple(   
   ULONG          cpspec,  
   PROPSPEC const rgpspec,  
   PROPVARIANT    rgvar  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `cpspec`  
 'ndaki Dizide belirtilen özellik sayısı `rgpspec` . Sıfır ise, yöntem hiçbir özellik döndürmez, ancak `S_OK` başarı kodu olarak döner.  
  
 `rgpspec`  
 'ndaki Okunacak özellikler dizisi. Özellikler, bir özellik KIMLIĞIYLE ya da isteğe bağlı bir dize adı ile belirtilebilir. Dizide belirli bir sırada özellikleri belirtmek gerekli değildir. Dizi yinelenen özellikler içerebilir ve basit özellikler için dönüşte yinelenen özellik değerlerine neden olur. Basit olmayan özellikler, bu dosyaları ikinci kez açma girişiminde erişim engellendi olarak döndürmelidir. Dizi, özellik kimliklerinin ve dize kimliklerinin bir karışımını içerebilir. Bu dizi en az `cpspec` sayıda özellik değerine sahip olmalıdır.  
  
 `rgvar`  
 [in, out] `PROPVARIANT` Her bir özellik için değerlerle doldurulacak bir dizi yapı (Microsoft. VisualStudio. OLE. Interop ad alanında). Dizi en az `cpspec` öğe boyutunda olmalıdır. Çağıranın dizideki değerleri başlatması gerekmez.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` . `S_FALSE`Bir veya daha fazla özellik bulunmazsa döndürür. Aksi takdirde bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir özellik bulunmazsa dizideki karşılık gelen giriş `rgvar` `VARIANT` , türü ile bir içerir `VT_EMPTY` .  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)
