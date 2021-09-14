---
description: DIA sembol bulma yordamından geri çağırmalar alır, böylece konum girişiminin ilerlemesini rapor etmek için kullanıcı arabirimini etkinleştirebilirsiniz.
title: IDiaLoadCallback | Microsoft Docs
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126629613"
---
# <a name="idialoadcallback"></a>IDiaLoadCallback
DIA sembol bulma yordamından geri çağırmalar alır, böylece konum girişiminin ilerlemesini rapor etmek için kullanıcı arabirimini etkinleştirebilirsiniz.

## <a name="syntax"></a>Syntax

```
IDiaLoadCallback : IUnknown
```

## <a name="methods-in-vtable-order"></a>VTable Sırasına Göre Yöntemler
 Aşağıdaki yöntemler bu arabirim tarafından ortaya çıkar:

|Yöntem|Açıklama|
|------------|-----------------|
|[IDiaLoadCallback::NotifyDebugDir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md)|.exe dosyasında bir hata ayıklama dizini .exe çağrılır.|
|[IDiaLoadCallback::NotifyOpenDBG](../../debugger/debug-interface-access/idialoadcallback-notifyopendbg.md)|Bir aday .dbg dosyası açıldığında çağrılır.|
|[IDiaLoadCallback::NotifyOpenPDB](../../debugger/debug-interface-access/idialoadcallback-notifyopenpdb.md)|Bir aday .pdb dosyası açıldığında çağrılır.|
|[IDiaLoadCallback::RestrictRegistryAccess](../../debugger/debug-interface-access/idialoadcallback-restrictregistryaccess.md)|Sembol arama yollarını bulmak için kayıt defteri sorgularının kullanılap kullanıla olmadığını belirler.|
|[IDiaLoadCallback::RestrictSymbolServerAccess](../../debugger/debug-interface-access/idialoadcallback-restrictsymbolserveraccess.md)|Sembolleri çözümlemek için bir sembol sunucusuna erişime izin verilip izin verilmeyeceklerini belirler.|

## <a name="remarks"></a>Açıklamalar
 İstemci uygulaması bu arabirimi kullanır ve [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) yöntemi çağrısında buna bir başvuru sağlar.

 Bir yükleme işlemi üzerinde uygulanan ek kısıtlamalar için bkz. [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md) arabirimi.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: Dia2.h

 Kitaplık: diaguids.lib

 DLL: msdia80.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Arabirimler (Arabirim Erişimi SDK'sında Hata Ayıklama)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)
- [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
