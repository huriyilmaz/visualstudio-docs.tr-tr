---
title: 'IDiaDataSource:: openSession | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 7dd6ab61db3e3bafd594298aa41d32bce64d4941
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744927"
---
# <a name="idiadatasourceopensession"></a>IDiaDataSource::openSession
Sembolleri sorgulamak için bir oturum açar.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT openSession ( 
   IDiaSession** ppSession
);
```

#### <a name="parameters"></a>Parametreler
ppSession

dışı Açık oturumu temsil eden bir [IDiaSession](../../debugger/debug-interface-access/idiasession.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
Başarılı olursa `S_OK` döndürür; Aksi takdirde, bir hata kodu döndürür. Aşağıdaki tabloda bu yöntem için olası dönüş değerleri gösterilmektedir.

|Değer|Açıklama|
|-----------|-----------------|
|E_UNEXPECTED|[IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md) nesnesi daha önce bir sembol kaynağı ile başlatılmamış.|
|E_INVALIDARG|Geçersiz `ppSession` parametresi.|
|E_OUTOFMEMORY|Oturumu açmak için yeterli bellek yok.|

## <a name="remarks"></a>Açıklamalar
Bu yöntem bir veri kaynağı için bir [IDiaSession](../../debugger/debug-interface-access/idiasession.md) nesnesi açar.

nesneleri `IDiaSession` veri kaynağına sorguları uygular. Bir oturum, her hata ayıklama sembolleri kümesi için bir adres alanını yönetir. Veri kaynağı sembolleri tarafından tanımlanan. exe veya. dll dosyası birden çok adres aralığında etkin ise (örneğin, birden çok işlem yüklendiği için), her bir adres aralığı için bir oturum kullanılmalıdır.

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
- [Genel bakış](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [.Pdb Dosyasını Sorgulama](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)
