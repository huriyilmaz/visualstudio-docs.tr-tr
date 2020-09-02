---
title: LocationType | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- LocationType enumeration
ms.assetid: d3e1eedc-bfd3-4c91-881b-d69565138d0f
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 28bcaa626797313f6ea68a17da33ef9ea192a856
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68154198"
---
# <a name="locationtype"></a>LocationType
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bir sembolde bulunan konum bilgilerinin türünü gösterir.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum LocationType {   
   LocIsNull,  
   LocIsStatic,  
   LocIsTLS,  
   LocIsRegRel,  
   LocIsThisRel,  
   LocIsEnregistered,  
   LocIsBitField,  
   LocIsSlot,  
   LocIsIlRel,  
   LocInMetaData,  
   LocIsConstant,  
   LocTypeMax  
};  
```  
  
## <a name="elements"></a>Öğeler  
 `LocIsNull`  
 Konum bilgileri kullanılamıyor.  
  
 `LocIsStatic`  
 Konum statiktir.  
  
 `LocIsTLS`  
 Konum, iş parçacığı yerel depolama alanında.  
  
 `LocIsRegRel`  
 Konum, kayıt göreli.  
  
 `LocIsThisRel`  
 Konum `this` -göreli.  
  
 `LocIsEnregistered`  
 Konum bir yazmaç içinde.  
  
 `LocIsBitField`  
 Konum bir bit alanıdır.  
  
 `LocIsSlot`  
 Konum bir Microsoft ara dil (MSIL) yuvadır.  
  
 `LocIsIlRel`  
 Konum MSIL ile ilişkilidir.  
  
 `LocInMetaData`  
 Konum meta verilerde.  
  
 `LocIsConstant`  
 Konum sabit bir değerde.  
  
 `LocTypeMax`  
 Bu Numaralandırmadaki konum türlerinin sayısı.  
  
## <a name="remarks"></a>Açıklamalar  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) arabirimi için kullanılabilen özellikler simgenin görüntü dosyası içindeki konumuna bağlıdır. Daha fazla bilgi için bkz. [sembol konumları](../../debugger/debug-interface-access/symbol-locations.md).  
  
 Bu Numaralandırmadaki değerler [IDiaSymbol:: get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md) metoduna yapılan bir çağrı tarafından döndürülür.  
  
## <a name="requirements"></a>Gereksinimler  
 Üst bilgi: cvconst. h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Numaralandırmalar ve yapılar](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol:: get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)   
 [Simge Konumları](../../debugger/debug-interface-access/symbol-locations.md)
