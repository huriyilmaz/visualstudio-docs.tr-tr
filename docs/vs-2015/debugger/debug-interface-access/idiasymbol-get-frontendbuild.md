---
title: 'IDiaSymbol:: get_frontEndBuild | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_frontEndBuild method
ms.assetid: f7dab1c6-112b-4966-baa5-afc976949c76
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 98840ff6dc55e1841e68ca846dca5987a20f3862
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64837630"
---
# <a name="idiasymbolget_frontendbuild"></a>IDiaSymbol::get_frontEndBuild
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ön uç derleme numarasını alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT get_frontEndBuild (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pRetVal`  
 dışı Ön uç derleme numarasını döndürür. Bkz. açıklamalar.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.  
  
> [!NOTE]
> Dönüş değeri, `S_FALSE` özelliğin simge için kullanılamadığı anlamına gelir.  
  
## <a name="remarks"></a>Açıklamalar  
 Derleyici genellikle iki birincil öğeden oluşur: kaynak kodu bir ara forma ayrıştırmayı işleyen ön uç (Ayrıştırıcı) ve ara formu derlemeye dönüştüren bir arka uç (kod Oluşturucu). Ön uç için arka uçtan farklı bir sürüme sahip olması seyrek değildir.  
  
 Ön uç veya arka uç sürüm numarası üç bölümden oluşur: \<major> . \<minor> . \<build> , burada \<major> ana sürüm numarasıdır, \<minor> ikincil sürüm numarasıdır ve \<build> yapı numarasıdır. Örneğin, 13.10.3077.  
  
## <a name="requirements"></a>Gereksinimler  
  
|Gereksinim|Description|  
|-----------------|-----------------|  
|Üst bilgi|dia2. h|  
|Sürüm:|DIA SDK v 7.0|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
