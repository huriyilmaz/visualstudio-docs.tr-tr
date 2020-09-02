---
title: 'IDiaSymbol:: get_backEndBuild | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_backEndBuild method
ms.assetid: 423af497-9294-438e-92b4-456c6f56dc56
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1bd7a0bc75907d60a3ac3cbb8a571908631777e3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64831740"
---
# <a name="idiasymbolget_backendbuild"></a>IDiaSymbol::get_backEndBuild
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Derleyicinin arka uç derleme numarasını alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT get_backEndBuild (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pRetVal`  
 dışı Arka uç derleme numarasını döndürür. Bkz. açıklamalar.  
  
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
