---
title: 'IDiaDataSource:: get_lastError | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::get_lastError method
ms.assetid: cf08850b-8b75-4e8c-90bd-bd0214756f99
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 48595dda70560f555533a1857f73db4d7bd20a86
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744969"
---
# <a name="idiadatasourceget_lasterror"></a>IDiaDataSource::get_lastError
Son yükleme hatası için dosya adını alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_lastError (
   BSTR* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 pRetVal

dışı Son yükleme hatasıyla ilişkili. pdb dosya adını içeren bir dize döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Yükleme işleminin neden olduğu son hata kodunu döndürür. @No__t_1 parametresi `NULL` `E_INVALIDARG` döndürür.

## <a name="example"></a>Örnek

```C++
BSTR    fileName;
HRESULT errorCode = pSource->get_lastError( &fileName );
```

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)