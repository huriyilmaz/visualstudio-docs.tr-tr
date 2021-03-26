---
title: QUERYCHANGESFUNC | Microsoft Docs
description: QUERYCHANGESFUNC geri çağırma işlevi, bir dosya adı koleksiyonunu listelemek ve her bir dosyanın durumunu öğrenmek için kullanılır.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- QUERYCHANGESFUNC
helpviewer_keywords:
- QUERYCHANGESFUNC callback function
- QUERYCHANGESDATA structure
ms.assetid: 9d383e2c-eee1-4996-973a-0652d4c5951c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cc797d68f6df6d9aab93554ba95955a7d9f45eea
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105068628"
---
# <a name="querychangesfunc"></a>QUERYCHANGESFUNC
Bu, bir dosya adı koleksiyonunu numaralandırmak ve her bir dosyanın durumunu belirleyebilmek için [SccQueryChanges](../extensibility/sccquerychanges-function.md) işlemi tarafından kullanılan bir geri çağırma işlevidir.

 `SccQueryChanges`İşleve bir dosya listesi ve `QUERYCHANGESFUNC` geri çağırma işaretçisi verilmiştir. Kaynak denetimi eklentisi verilen listeyi numaralandırır ve listedeki her dosya için durum (Bu geri çağırma aracılığıyla) sağlar.

## <a name="signature"></a>İmza

```cpp
typedef BOOL (*QUERYCHANGESFUNC)(
   LPVOID pvCallerData,
   QUERYCHANGESDATA * pChangesData
);
```

## <a name="parameters"></a>Parametreler
 pvCallerData

'ndaki `pvCallerData` Çağıran tarafından geçirilen parametre (IDE) tarafından [sorgu değişiklikleri](../extensibility/sccquerychanges-function.md)için. Kaynak denetimi eklentisinin bu değerin içeriğiyle ilgili bir varsayımsız olmaması gerekir.

 pChangesData

'ndaki Dosyadaki değişiklikleri açıklayan bir [QUERYCHANGESDATA yapısı](#LinkQUERYCHANGESDATA) yapısına yönelik işaretçi.

## <a name="return-value"></a>Döndürülen değer
 IDE, uygun bir hata kodu döndürür:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|İşleme devam edin.|
|SCC_I_OPERATIONCANCELED|İşlemeyi durdur.|
|SCC_E_xxx|Uygun bir SCC hatası işlemeyi durdurmalıdır.|

## <a name="querychangesdata-structure"></a><a name="LinkQUERYCHANGESDATA"></a> QUERYCHANGESDATA yapısı
 Her dosya için geçirilen yapı aşağıdaki gibi görünür:

```cpp
struct QUERYCHANGESDATA_A
{
    DWORD  dwSize;
    LPCSTR lpFileName;
    DWORD  dwChangeType;
    LPCSTR lpLatestName;
};

typedef struct QUERYCHANGESDATA_A QUERYCHANGESDATA;

struct QUERYCHANGESDATA_W
{
    DWORD   dwSize;
    LPCWSTR lpFileName;
    DWORD   dwChangeType;
    LPCWSTR lpLatestName;
};
```

 Bu yapının dwSize boyutu (bayt).

 lpFileName bu öğe için özgün dosya adı.

 dosyanın durumunu gösteren dwChangeType kodu:

|Kod|Description|
|----------|-----------------|
|`SCC_CHANGE_UNKNOWN`|Nelerin değiştiğini söylemez.|
|`SCC_CHANGE_UNCHANGED`|Bu dosya için ad değişikliği yok.|
|`SCC_CHANGE_DIFFERENT`|Dosya farklı bir kimliğe sahip, ancak veritabanında aynı ad var.|
|`SCC_CHANGE_NONEXISTENT`|Dosya, veritabanında ya da yerel olarak mevcut değil.|
|`SCC_CHANGE_DATABASE_DELETED`|Dosya veritabanında silindi.|
|`SCC_CHANGE_LOCAL_DELETED`|Dosya yerel olarak silindi, ancak dosya veritabanında hala var. Bu saptanamıyor, döndürün `SCC_CHANGE_DATABASE_ADDED` .|
|`SCC_CHANGE_DATABASE_ADDED`|Dosya veritabanına eklendi, ancak yerel olarak mevcut değil.|
|`SCC_CHANGE_LOCAL_ADDED`|Dosya veritabanında yok ve yeni bir yerel dosya.|
|`SCC_CHANGE_RENAMED_TO`|Dosya yeniden adlandırıldı veya veritabanına olarak taşındı `lpLatestName` .|
|`SCC_CHANGE_RENAMED_FROM`|Dosya yeniden adlandırıldı veya veritabanına taşındı `lpLatestName` ; Bu, izlemeye çok pahalıdır, gibi farklı bir bayrak döndürün `SCC_CHANGE_DATABASE_ADDED` .|

 lpLatestName bu öğe için geçerli dosya adını.

## <a name="see-also"></a>Ayrıca bkz.
- [IDE tarafından uygulanan geri çağırma işlevleri](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccQueryChanges](../extensibility/sccquerychanges-function.md)
- [Hata kodları](../extensibility/error-codes.md)
