---
description: Bir dizin aracılığıyla bir kaynak dosyası alır.
title: 'IDiaEnumSourceFiles:: Item | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSourceFiles::Item method
ms.assetid: 3c19d7ed-0232-4b0e-9b10-f33ed9e0c93b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 798aa0aafc17e03ea56eecc7de46c273c3346396bca57990bc0c56e8f4eb67d8
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121392475"
---
# <a name="idiaenumsourcefilesitem"></a>IDiaEnumSourceFiles::Item
Bir dizin aracılığıyla bir kaynak dosyası alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT Item ( 
   DWORD            index,
   IDiaSourceFile** sourceFile
);
```

#### <a name="parameters"></a>Parametreler
 dizin

'ndaki Alınacak [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) nesnesinin dizini. Dizin 0 `count` -1 aralığında, burada `count` [IDiaEnumSourceFiles:: get_Count](../../debugger/debug-interface-access/idiaenumsourcefiles-get-count.md) yöntemi tarafından döndürülür.

 Kaynakdosya

dışı İstenen kaynak dosyayı temsil eden bir [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
