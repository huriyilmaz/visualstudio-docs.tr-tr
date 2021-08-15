---
description: Özgün hata ayıklama dizininde bir. pdb dosyası olup olmadığını belirler.
title: 'IDiaLoadCallback2:: Kısıttorginalpathaccess | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2::RestrictOriginalPathAccess method
ms.assetid: 31fde3af-2824-4b0f-8d0d-cee6046596f6
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 173f7762b212f5aaa876f87a78e72432d8829e84c63946eccea686e6abe777dc
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121405149"
---
# <a name="idialoadcallback2restrictoriginalpathaccess"></a>IDiaLoadCallback2::RestrictOriginalPathAccess
Özgün hata ayıklama dizininde bir. pdb dosyası olup olmadığını belirler.

## <a name="syntax"></a>Syntax

```C++
HRESULT RestrictOriginalPathAccess ();
```

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Dışında herhangi bir dönüş kodu `S_OK` , özgün hata ayıklama dizininde bir. pdb dosyası aramaya engel olur. Özgün hata ayıklama dizini, hata ayıklama açık olduğunda yürütülebilir dosyada derlenen sembol dosyasının yoludur. Bu yol, yürütülebilir dosyanın bulunduğu yol ile aynı değildir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
