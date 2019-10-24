---
title: 'IDiaLoadCallback2:: RestrictSystemRootAccess | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2::RestrictSystemRootAccess method
ms.assetid: 39f22db8-632a-4ef0-babc-23f758e6d937
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0cf1a29019de2d3ffdfdb3cc7b9006e964495aa9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742969"
---
# <a name="idialoadcallback2restrictsystemrootaccess"></a>IDiaLoadCallback2::RestrictSystemRootAccess
Sistem kök dizininde. pdb dosyalarına yönelik arama yapılmasına izin verilip verilmeyeceğini belirler.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT RestrictSystemRootAccess();
```

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 @No__t_0 dışındaki herhangi bir dönüş kodu,. pdb dosyaları için sistem kökünün aranmasını önler.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)