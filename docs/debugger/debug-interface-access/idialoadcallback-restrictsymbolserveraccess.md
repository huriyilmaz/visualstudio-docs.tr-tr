---
description: Sembolleri çözümlemek için bir sembol sunucusuna erişime izin verilip izin verilmeyeceklerini belirler.
title: IDiaLoadCallback::RestrictSymbolServerAccess | Microsoft Docs
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122044537"
---
# <a name="idialoadcallbackrestrictsymbolserveraccess"></a>IDiaLoadCallback::RestrictSymbolServerAccess
Sembolleri çözümlemek için bir sembol sunucusuna erişime izin verilip izin verilmeyeceklerini belirler.

## <a name="syntax"></a>Syntax

```C++
HRESULT RestrictSymbolServerAccess();
```

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Dışında herhangi bir dönüş `S_OK` kodu, sembolleri çözümlemek için bir sembol sunucusunun kullanımını önler.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
