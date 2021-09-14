---
description: Sembolleri çözümlemek için bir sembol sunucusuna erişime izin verilip verilmeyeceğini belirler.
title: 'Ialoadcallback:: RestrictSymbolServerAccess | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::RestrictSymbolServerAccess method
ms.assetid: db37ad9f-f75e-4f0c-83bf-21a6e66ba859
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: d5bed6cc91e06b5906bd34d4911919f90b6456be
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126629606"
---
# <a name="idialoadcallbackrestrictsymbolserveraccess"></a>IDiaLoadCallback::RestrictSymbolServerAccess
Sembolleri çözümlemek için bir sembol sunucusuna erişime izin verilip verilmeyeceğini belirler.

## <a name="syntax"></a>Syntax

```C++
HRESULT RestrictSymbolServerAccess();
```

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Dışındaki herhangi bir dönüş kodu `S_OK` sembolleri çözümlemek için sembol sunucusunun kullanılmasını engeller.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
