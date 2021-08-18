---
description: Bir istemci uygulamanın, göreli bir sanal adresle belirtilen bir yürütülebilir dosya bayt vermesini sağlar.
title: Idiareadexeatrboş Allback | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtRVACallback interface
ms.assetid: b2892513-3952-4f99-9b98-60cb9b1fdc91
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 41711344f3047667b722d929b361eb4ac0c3b21e9abdb199b53425dcde1c180e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121344895"
---
# <a name="idiareadexeatrvacallback"></a>IDiaReadExeAtRVACallback
Bir istemci uygulamanın, göreli bir sanal adresle belirtilen bir yürütülebilir dosya bayt vermesini sağlar.

## <a name="syntax"></a>Syntax

```
IDiaReadExeAtRVACallback : IUnknown
```

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDiaReadExeAtRVACallback` .

|Yöntem|Açıklama|
|------------|-----------------|
|[IDiaReadExeAtRVACallback::ReadExecutableAtRVA](../../debugger/debug-interface-access/idiareadexeatrvacallback-readexecutableatrva.md)|Yürütülebilir dosyadan belirtilen göreli sanal adresten (RVA) başlayarak belirtilen bayt sayısını okur.|

## <a name="remarks"></a>Açıklamalar
 İstemci uygulaması, çalıştırılabilir dosyanın dosyasına bir göreli sanal adres kullanarak yürütülebilir dosyanın baytlarını sağlamak için bu arabirimi uygular. Mutlak bir dosya boşluğu kullanmak için, [ıareaareadexeatoffsetcallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md) arabirimini uygulayın.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu yöntem, istemci uygulaması tarafından uygulanır ve dosyayı okumak için alternatif bir yöntem olarak [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) metoduna geçirilir.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: dia2. h

 Kitaplık: diaguid. lib

 DLL: msdia80.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Arabirimler (Arabirim Erişimi SDK'sında Hata Ayıklama)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)
