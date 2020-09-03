---
title: 'IDiaDataSource:: openSession | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::openSession method
ms.assetid: a3319ed0-3979-483b-9852-c0af96852c48
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b49c90374975865edcac8a94c504e1fa991d711a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85468506"
---
# <a name="idiadatasourceopensession"></a>IDiaDataSource::openSession
Sembolleri sorgulamak için bir oturum açar.

## <a name="syntax"></a>Söz dizimi

```C++
HRESULT openSession ( 
   IDiaSession** ppSession
);
```

#### <a name="parameters"></a>Parametreler
ppSession

dışı Açık oturumu temsil eden bir [IDiaSession](../../debugger/debug-interface-access/idiasession.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür. Aşağıdaki tabloda bu yöntem için olası dönüş değerleri gösterilmektedir.

|Değer|Açıklama|
|-----------|-----------------|
|E_UNEXPECTED|[IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md) nesnesi daha önce bir sembol kaynağı ile başlatılmamış.|
|E_INVALIDARG|Geçersiz `ppSession` parametre.|
|E_OUTOFMEMORY|Oturumu açmak için yeterli bellek yok.|

## <a name="remarks"></a>Açıklamalar
Bu yöntem bir veri kaynağı için bir [IDiaSession](../../debugger/debug-interface-access/idiasession.md) nesnesi açar.

`IDiaSession` nesneler veri kaynağına sorguları uygular. Bir oturum, her hata ayıklama sembolleri kümesi için bir adres alanını yönetir. Veri kaynağı sembolleri tarafından tanımlanan. exe veya. dll dosyası birden çok adres aralığında etkin ise (örneğin, birden çok işlem yüklendiği için), her bir adres aralığı için bir oturum kullanılmalıdır.

## <a name="example"></a>Örnek

```C++
IDiaSession* pSession;
HRESULT hr = pSource->openSession( &pSession );
if (FAILED(hr))
{
   // report error
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
- [Genel Bakış](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [.Pdb Dosyasını Sorgulama](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)
