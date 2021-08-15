---
description: Sembol arama yollarını bulmak için kayıt defteri sorgularının kullanılap kullanıla olmadığını belirler.
title: IDiaLoadCallback::RestrictRegistryAccess | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::RestrictRegistryAccess method
ms.assetid: de4760c3-a746-4bab-8065-1388fed31b67
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 4a61ab05230b1c2573e38b3de60b2c8d57bd08b1984dfa87f8853ad0ff13471d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121345023"
---
# <a name="idialoadcallbackrestrictregistryaccess"></a>IDiaLoadCallback::RestrictRegistryAccess
Sembol arama yollarını bulmak için kayıt defteri sorgularının kullanılap kullanıla olmadığını belirler.

## <a name="syntax"></a>Syntax

```C++
HRESULT RestrictRegistryAccess();
```

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Dışında herhangi bir dönüş `S_OK` kodu, sembol arama yolları için kayıt defterini sorgulamayı önler.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
