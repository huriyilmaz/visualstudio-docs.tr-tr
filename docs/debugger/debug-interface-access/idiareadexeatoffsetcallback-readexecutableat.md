---
description: Yürütülebilir dosyadan belirtilen uzaklığından başlayarak belirtilen bayt sayısını okur.
title: IDiaReadExeAtOffsetCallback::ReadExecutableAt | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtOffsetCallback::ReadExecutableAt method
ms.assetid: 30b1cef0-b366-4712-8e89-d21f640964f8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 4cd63d860c4235b7b746cc7d14cad0a58f1a565d3d7fb2d81740a3a0a3b6ab6d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121454954"
---
# <a name="idiareadexeatoffsetcallbackreadexecutableat"></a>IDiaReadExeAtOffsetCallback::ReadExecutableAt
Yürütülebilir dosyadan belirtilen uzaklığından başlayarak belirtilen bayt sayısını okur.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT ReadExecutableAt ( 
   DWORDLONG fileOffset,
   DWORD     cbData,
   DWORD*    pcbData,
   BYTE      data[]
);
```

#### <a name="parameters"></a>Parametreler
 fileOffset

[in] Okumaya başlamak için yürütülebilir dosyada uzaklık.

 Cbdata

[in] Okunan bayt sayısı.

 veri verisi

[out] Okunan bayt sayısını döndürür.

 data[]

[in, out] Dosyadan okunan baytlarla doldurulmuş bir dizi.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, DIA destek kodu tarafından mutlak dosya uzaklığı kullanılarak yürütülebilir dosyadan veri baytlarını yüklemek için çağrılır. Bu yöntem, [IDiaDataSource::loadDataForExe yöntemini](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) desteklemek için çağrılır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
