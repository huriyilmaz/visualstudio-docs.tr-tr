---
title: 'IDiaSymbol:: get_classParent | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_classParent method
ms.assetid: 99db875a-caae-4d60-ae70-64bc8a9f6fba
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e01b36dd4e4a668431d95a39a7ad14cfea475358
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64815227"
---
# <a name="idiasymbolget_classparent"></a>IDiaSymbol::get_classParent
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Simgenin sınıf üst öğesine bir başvuru alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT get_classParent (   
   IDiaSymbol** pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pRetVal`  
 dışı Simgenin üst öğesini temsil eden bir [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) nesnesi döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.  
  
> [!NOTE]
> Dönüş değeri, `S_FALSE` özelliğin simge için kullanılamadığı anlamına gelir.  
  
## <a name="requirements"></a>Gereksinimler  
  
|Gereksinim|Description|  
|-----------------|-----------------|  
|Üst bilgi|dia2. h|  
|Sürüm:|DIA SDK v 7.0|  
  
## <a name="remarks"></a>Açıklamalar  
 Sınıf üst öğeleri olabilecek simgelerin türleri [sembol türlerinin sınıf hiyerarşisinde](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)belgelenmiştir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Simge Türlerinin Sınıf Hiyerarşisi](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)
