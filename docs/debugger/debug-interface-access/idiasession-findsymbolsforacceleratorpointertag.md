---
description: Belirtilen etiket değerinin üst Hızlandırıcı saplama işlevinde karşılık gelen değişkeni için simgelerin bir sabit değerini döndürür.
title: IDiaSession::findSymbolsForAcceleratorPointerTag | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 95fd5e7a-c637-437e-b369-c864eef733c2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 9fc8d82f914b77799dc4fa2c3b744b654b0e34cf117580526fe8effc318a71d5
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121380121"
---
# <a name="idiasessionfindsymbolsforacceleratorpointertag"></a>IDiaSession::findSymbolsForAcceleratorPointerTag
Belirtilen etiket değerinin üst Hızlandırıcı saplama işlevinde karşılık gelen değişkeni için simgelerin bir sabit değerini döndürür.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT findSymbolsForAcceleratorPointerTag ( 
   IDiaSymbol*           parent,
   DWORD                 tagValue,
   IDiaEnumSymbols**     ppResult
);
```

#### <a name="parameters"></a>Parametreler
 `parent`

[in] Aranacak Hızlandırıcı saplama işlevine karşılık gelen bir IDiaSymbol.

 `tagValue`

[in] İşaretçi etiketi değeri.

 `ppResult`

[out] Sonuçla başlatılan `IDiaEnumSymbols` bir arabirim işaretçisinin işaretçisi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
