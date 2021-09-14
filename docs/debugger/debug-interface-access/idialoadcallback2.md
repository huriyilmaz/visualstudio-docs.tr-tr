---
description: DIA sembol bulma yordamından geri çağırmalar alır ve bulma işlemi üzerinde kısıtlamalara olanak sağlar.
title: IDiaLoadCallback2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2 interface
ms.assetid: 9a44277d-cbed-4811-9bad-5a2aa0f09323
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: adf24a1790e40e9ebdd885e6eaec73e152013b5f
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126629576"
---
# <a name="idialoadcallback2"></a>IDiaLoadCallback2
DIA sembol bulma yordamından geri çağırmalar alır ve bulma işlemi üzerinde kısıtlamalara olanak sağlar.

## <a name="syntax"></a>Syntax

```
IDiaLoadCallback2 : IDiaLoadCallback
```

## <a name="methods-in-vtable-order"></a>VTable Sırasına Göre Yöntemler
 [Bu arabirim, IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md) arabiriminde yöntemlere ek olarak aşağıdaki yöntemleri de sunar:

|Yöntem|Açıklama|
|------------|-----------------|
|[IDiaLoadCallback2::RestrictOriginalPathAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictoriginalpathaccess.md)|Özgün hata ayıklama dizininde bir .pdb dosyası olup olmadığını belirler.|
|[IDiaLoadCallback2::RestrictReferencePathAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictreferencepathaccess.md)|Dosyanın bulunduğu yolda bir .pdb dosyası aramasına izin verilip .exe belirler.|
|[IDiaLoadCallback2::RestrictDBGAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictdbgaccess.md)|.dbg dosyalarından hata ayıklama bilgilerine izin verip verilmeyeceklerini belirler.|
|[IDiaLoadCallback2::RestrictSystemRootAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictsystemrootaccess.md)|Sistem kök dizininde .pdb dosyaları aramasına izin verili olup olmadığını belirler.|

## <a name="remarks"></a>Açıklamalar
 İstemci uygulaması bu arabirimi kullanır ve [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) yöntemi çağrısında buna bir başvuru sağlar. [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md) arabiriminde tüm yöntemleri de uygulamayı unutmayın.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: Dia2.h

 Kitaplık: diaguids.lib

 DLL: msdia80.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Arabirimler (Arabirim Erişimi SDK'sında Hata Ayıklama)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)
- [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)
- [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)
