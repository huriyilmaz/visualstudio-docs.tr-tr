---
title: 'Ialoadcallback:: RestrictSymbolServerAccess | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::RestrictSymbolServerAccess method
ms.assetid: db37ad9f-f75e-4f0c-83bf-21a6e66ba859
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 87d590af5162d3efd2ef2c9702a3fe9f45250993
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743028"
---
# <a name="idialoadcallbackrestrictsymbolserveraccess"></a>IDiaLoadCallback::RestrictSymbolServerAccess
Sembolleri çözümlemek için bir sembol sunucusuna erişime izin verilip verilmeyeceğini belirler.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT RestrictSymbolServerAccess();
```

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 @No__t_0 dışındaki herhangi bir dönüş kodu sembolleri çözümlemek için sembol sunucusunun kullanılmasını önler.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)