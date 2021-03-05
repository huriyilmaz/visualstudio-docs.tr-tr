---
description: Son yükleme hatası için dosya adını alır.
title: 'IDiaDataSource:: get_lastError | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::get_lastError method
ms.assetid: cf08850b-8b75-4e8c-90bd-bd0214756f99
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7edce9a2af6c849371360526d617d20738973cba
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158317"
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
 Yükleme işleminin neden olduğu son hata kodunu döndürür. `E_INVALIDARG`Parametresi ise döndürür `pRetVal` `NULL` .

## <a name="example"></a>Örnek

```C++
BSTR    fileName;
HRESULT errorCode = pSource->get_lastError( &fileName );
```

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
