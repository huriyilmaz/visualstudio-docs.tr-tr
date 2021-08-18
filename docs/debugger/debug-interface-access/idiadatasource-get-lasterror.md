---
description: Son yükleme hatasının dosya adını alır.
title: IDiaDataSource::get_lastError | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 1a15333df3c4c994f752ff7bd93978a7b7e34ffb
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122036578"
---
# <a name="idiadatasourceget_lasterror"></a>IDiaDataSource::get_lastError
Son yükleme hatasının dosya adını alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_lastError (
   BSTR* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 pRetVal

[out] Son yükleme hatasıyla ilişkili .pdb dosya adını içeren bir dize döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Yükleme işlemi nedeniyle oluşan son hata kodunu döndürür. parametresi `E_INVALIDARG` ise `pRetVal` `NULL` döndürür.

## <a name="example"></a>Örnek

```C++
BSTR    fileName;
HRESULT errorCode = pSource->get_lastError( &fileName );
```

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
