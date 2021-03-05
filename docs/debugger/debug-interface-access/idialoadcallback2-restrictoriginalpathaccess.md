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
ms.workload:
- multiple
ms.openlocfilehash: 7af6794b57dfe5efe8d2e85f8e74febcede5ef23
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102157429"
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
