---
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 784e17ddf6202419618b7ff3b8836f0f46021989
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85466688"
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