---
description: İstemci uygulamasının dosya konumuyla belirtilen bir yürütülebilir dosya bayt sağlaması için izin sağlar.
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
ms.workload:
- multiple
ms.openlocfilehash: 9ba2791319dcebb6187ed00c8a273680796e514a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102157365"
---
# <a name="idiareadexeatoffsetcallback"></a>IDiaReadExeAtOffsetCallback
İstemci uygulamasının dosya konumuyla belirtilen bir yürütülebilir dosya bayt sağlaması için izin sağlar.

## <a name="syntax"></a>Syntax

```
IDiaReadExeAtOffsetCallback : IUnknown
```

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDiaReadExeAtOffsetCallback` .

|Yöntem|Açıklama|
|------------|-----------------|
|[IDiaReadExeAtOffsetCallback::ReadExecutableAt](../../debugger/debug-interface-access/idiareadexeatoffsetcallback-readexecutableat.md)|Bir yürütülebilir dosyadan belirtilen uzaklığa başlayarak belirtilen sayıda bayt okur.|

## <a name="remarks"></a>Açıklamalar
 İstemci uygulaması, yürütülebilir dosyanın dosya içine mutlak bir konum kullanarak çalıştırılabilir bayt sağlamak için bu arabirimi uygular. Göreli bir sanal adres kullanmak için [ıdiareadexeatrboş allback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) arabirimini uygulayın.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu yöntem, istemci uygulaması tarafından uygulanır ve dosyayı okumak için alternatif bir yöntem olarak [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) metoduna geçirilir.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: dia2. h

 Kitaplık: diaguid. lib

 DLL: msdia80.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Arabirimler (Arabirim Erişimi SDK'sında Hata Ayıklama)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)
