---
description: bir istemci uygulamasının dosya konumu tarafından belirtilen yürütülebilir dosya baytlarını temin unu sağlar.
title: IDiaReadExeAtOffsetCallback | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtOffsetCallback interface
ms.assetid: 3c961641-3ce3-4bc3-bd6e-a802fa3bec49
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 9d8ca962425742304a215512abd10b7aed755feb
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122134300"
---
# <a name="idiareadexeatoffsetcallback"></a>IDiaReadExeAtOffsetCallback
bir istemci uygulamasının dosya konumu tarafından belirtilen yürütülebilir dosya baytlarını temin unu sağlar.

## <a name="syntax"></a>Syntax

```
IDiaReadExeAtOffsetCallback : IUnknown
```

## <a name="methods-in-vtable-order"></a>Vtable Sırasına Göre Yöntemler
 Aşağıdaki tabloda yöntemlerini `IDiaReadExeAtOffsetCallback` gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[IDiaReadExeAtOffsetCallback::ReadExecutableAt](../../debugger/debug-interface-access/idiareadexeatoffsetcallback-readexecutableat.md)|Yürütülebilir dosyadan belirtilen uzaklığından başlayarak belirtilen bayt sayısını okur.|

## <a name="remarks"></a>Açıklamalar
 İstemci uygulaması, yürütülebilir dosyanın dosyasına mutlak bir uzaklık kullanarak yürütülebilir dosyanın baytlarını sağlamak için bu arabirimi uygulamaya almaktadır. Göreli bir sanal adres kullanmak için [IDiaReadExeAtRVACallback arabirimini](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) kullanın.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu yöntem istemci uygulaması tarafından uygulanır ve dosyayı okumak için alternatif bir yöntem olarak [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) yöntemine geçirildi.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: Dia2.h

 Kitaplık: diaguids.lib

 DLL: msdia80.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Arabirimler (Arabirim Erişimi SDK'sında Hata Ayıklama)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)
