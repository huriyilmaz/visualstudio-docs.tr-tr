---
description: DIA sembol konumlandırma yordamının geri çağırmaları alır, böylece bir kullanıcı arabiriminin konum denemesinin ilerlemesini raporlemelerini sağlar.
title: Ialoadcallback | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback interface
ms.assetid: 2f18c64c-2cf0-43fc-a447-21e82702ca2a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 9b5ef4523aa2b8acd098f8a9e46d5aa0009f9b37
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122139198"
---
# <a name="idialoadcallback"></a>IDiaLoadCallback
DIA sembol konumlandırma yordamının geri çağırmaları alır, böylece bir kullanıcı arabiriminin konum denemesinin ilerlemesini raporlemelerini sağlar.

## <a name="syntax"></a>Syntax

```
IDiaLoadCallback : IUnknown
```

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Aşağıdaki yöntemler bu arabirim tarafından sunulur:

|Yöntem|Açıklama|
|------------|-----------------|
|[IDiaLoadCallback::NotifyDebugDir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md)|.exe dosyasında bir hata ayıklama dizini bulunduğunda çağırılır.|
|[IDiaLoadCallback::NotifyOpenDBG](../../debugger/debug-interface-access/idialoadcallback-notifyopendbg.md)|Bir aday. dbg dosyası açıldığında çağırılır.|
|[IDiaLoadCallback::NotifyOpenPDB](../../debugger/debug-interface-access/idialoadcallback-notifyopenpdb.md)|Bir aday. pdb dosyası açıldığında çağırılır.|
|[IDiaLoadCallback::RestrictRegistryAccess](../../debugger/debug-interface-access/idialoadcallback-restrictregistryaccess.md)|Simge arama yollarını bulmak için kayıt defteri sorgularının kullanılabileceğini belirler.|
|[IDiaLoadCallback::RestrictSymbolServerAccess](../../debugger/debug-interface-access/idialoadcallback-restrictsymbolserveraccess.md)|Sembolleri çözümlemek için bir sembol sunucusuna erişime izin verilip verilmeyeceğini belirler.|

## <a name="remarks"></a>Açıklamalar
 İstemci uygulaması bu arabirimi uygular ve [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) metoduna yapılan çağrıda buna bir başvuru sağlar.

 Bir yükleme işlemine eklenebilir ek kısıtlamalar için, [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md) arabirimine bakın.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: dia2. h

 Kitaplık: diaguid. lib

 DLL: msdia80.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Arabirimler (Arabirim Erişimi SDK'sında Hata Ayıklama)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)
- [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
