---
description: Geçerli kare veri numaralayıcı ile aynı numaralama durumunu içeren bir numaralayıcı oluşturur.
title: IDiaEnumFrameData::Clone | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::Clone Method
ms.assetid: 28a17300-1626-422f-a17a-3a4d3872c37c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 1f22ad93668c617f687824c8825955fc63f537d9
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630345"
---
# <a name="idiaenumframedataclone"></a>IDiaEnumFrameData::Clone
Geçerli numaralayıcıyla aynı numaralama durumunu içeren bir numaralayıcı oluşturur.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT Clone( 
   IDiaEnumFrameData** ppenum
);
```

#### <a name="parameters"></a>Parametreler
 ppenum

[out] Numaralayıcının bir kopyasını içeren bir [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md) nesnesi döndürür. Çerçeve verileri çoğaltılmış değil, yalnızca numaralayıcı.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)
