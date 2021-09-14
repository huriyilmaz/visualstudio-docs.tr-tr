---
description: Belirli bir platform türü için yığın çerçevesi numaralayıcısını alma.
title: IDiaStackWalker::getEnumFrames2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalker2::getEnumFrames2 method
ms.assetid: 73196d3f-112c-4b3a-997b-7c6b815d4afc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 80fbd406a9ad2d3aa691e1fd2650222447d0e109
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635401"
---
# <a name="idiastackwalkergetenumframes2"></a>IDiaStackWalker::getEnumFrames2
Belirli bir platform türü için yığın çerçevesi numaralayıcısını alma.

## <a name="syntax"></a>Sözdizimi

```C++

      HRESULT getEnumFrames2( 
   enum  CV_CPU_TYPE_e    cpuid,
   IDiaStackWalkHelper*   pHelper,
   IDiaEnumStackFrames**  ppEnum
);
```

#### <a name="parameters"></a>Parametreler
 `cpuid`

[in] Platform türünü [CV_CPU_TYPE_e enumeration](../../debugger/debug-interface-access/cv-cpu-type-e.md) enumeration değerinden bir değer.

 `pHelper`

[in] Yardımcı [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) nesnesi.

 `ppEnum`

[out] [IDiaStackFrame nesnelerinin listesini içeren bir IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md) [nesnesi](../../debugger/debug-interface-access/idiastackframe.md) döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Yalnızca x86 platformu için bir yığın çerçevesi listesi almak için [IDiaStackWalker::getEnumFrames yöntemini](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md) arayın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)
- [CV_CPU_TYPE_e Numaralandırması](../../debugger/debug-interface-access/cv-cpu-type-e.md)
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
- [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)
