---
description: Bir yürütülebilir dosyadan belirtilen uzaklığa başlayarak belirtilen sayıda bayt okur.
title: 'IDiaReadExeAtOffsetCallback:: ReadExecutableAt | Microsoft Docs'
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
ms.openlocfilehash: 71948d51865e82f3dd0fa2fe7bb29fd200b59f30
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122129058"
---
# <a name="idiareadexeatoffsetcallbackreadexecutableat"></a>IDiaReadExeAtOffsetCallback::ReadExecutableAt
Bir yürütülebilir dosyadan belirtilen uzaklığa başlayarak belirtilen sayıda bayt okur.

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
 Dosya kayması

'ndaki Okumaya başlamak için çalıştırılabilir dosyadaki fark.

 cbData

'ndaki Okunacak bayt sayısı.

 pcbData

dışı Okunan bayt sayısını döndürür.

 veri []

[in, out] Dosyadan okunan bayt ile doldurulmuş bir dizi.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, tam bir dosya boşluğu kullanılarak yürütülebilir dosyadan veri baytları yüklemek için ÇYA destek kodu tarafından çağırılır. Bu yöntem, [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) metodunu desteklemek için çağrılır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
