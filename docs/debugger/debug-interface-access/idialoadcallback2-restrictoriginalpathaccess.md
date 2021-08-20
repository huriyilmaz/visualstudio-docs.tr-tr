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
ms.openlocfilehash: ed1c3cb17a8f1e3e43f0798bce4c18bd0457370d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122066562"
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
