---
title: QUERYCHANGESFUNC | Microsoft Docs
description: QUERYCHANGESFUNC geri çağırma işlevi, bir dosya adı koleksiyonunun numaralarını belirlemek ve her bir dosyanın durumunu belirlemek için kullanılır.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: b061fbfb6644f77348574020c0a5cb614691ae6b
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899140"
---
# <a name="querychangesfunc"></a>QUERYCHANGESFUNC
Bu, [SccQueryChanges](../extensibility/sccquerychanges-function.md) işlemi tarafından bir dosya adı koleksiyonunun numaralarını belirlemek ve her bir dosyanın durumunu belirlemek için kullanılan bir geri çağırma işlevidir.

 İşleve `SccQueryChanges` dosya listesi ve geri çağırma `QUERYCHANGESFUNC` işaretçisi verilir. Kaynak denetimi eklentisi, verilen listede numaralar ve listede yer alan her dosya için durum (bu geri çağırma yoluyla) sağlar.

## <a name="signature"></a>İmza

```cpp
typedef BOOL (*QUERYCHANGESFUNC)(
   LPVOID pvCallerData,
   QUERYCHANGESDATA * pChangesData
);
```

## <a name="parameters"></a>Parametreler
 pvCallerData

[in] Çağıran `pvCallerData` (IDE) tarafından [SccQueryChanges'e geçirilen parametre.](../extensibility/sccquerychanges-function.md) Kaynak denetimi eklentisi, bu değerin içeriğiyle ilgili varsayımda bulunamaz.

 pChangesData

[in] Bir [dosyada yapılan değişiklikleri açıklayan QUERYCHANGESDATA](#LinkQUERYCHANGESDATA) Yapısı yapısına işaretçi.

## <a name="return-value"></a>Döndürülen değer
 IDE uygun bir hata kodu döndürür:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|İşlemeye devam.|
|SCC_I_OPERATIONCANCELED|İşlemeyi durdurun.|
|SCC_E_xxx|Uygun SCC hatalarını işlemeyi durdurmanız gerekir.|

## <a name="querychangesdata-structure"></a><a name="LinkQUERYCHANGESDATA"></a> QUERYCHANGESDATA Yapısı
 Her dosya için geçirilen yapı aşağıdaki gibi olur:

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

 Bu yapının dwSize Boyutu (bayt cinsinden).

 lpFileName Bu öğenin özgün dosya adı.

 Dosyanın durumunu gösteren dwChangeType Kodu:

|Kod|Açıklama|
|----------|-----------------|
|`SCC_CHANGE_UNKNOWN`|Nelerin değiştiğini söylemek olamaz.|
|`SCC_CHANGE_UNCHANGED`|Bu dosya için ad değişikliği yok.|
|`SCC_CHANGE_DIFFERENT`|Farklı bir kimliğe sahip dosya, ancak veritabanında aynı ad var.|
|`SCC_CHANGE_NONEXISTENT`|Dosya veritabanında veya yerel olarak yok.|
|`SCC_CHANGE_DATABASE_DELETED`|Veritabanında silinen dosya.|
|`SCC_CHANGE_LOCAL_DELETED`|Dosya yerel olarak silindi ama dosya veritabanında hala var. Bu belirlene belirlenirse, `SCC_CHANGE_DATABASE_ADDED` dönüş.|
|`SCC_CHANGE_DATABASE_ADDED`|Veritabanına eklenen ancak yerel olarak mevcut olmayan dosya.|
|`SCC_CHANGE_LOCAL_ADDED`|Dosya veritabanında yok ve yeni bir yerel dosya.|
|`SCC_CHANGE_RENAMED_TO`|Dosya yeniden adlandırıldı veya veritabanına olarak `lpLatestName` taşındı.|
|`SCC_CHANGE_RENAMED_FROM`|Dosya yeniden adlandırıldı veya veritabanından taşındı; bu izlemesi çok pahalı `lpLatestName` olursa, gibi farklı bir bayrak geri `SCC_CHANGE_DATABASE_ADDED` döner.|

 lpLatestName Bu öğenin geçerli dosya adı.

## <a name="see-also"></a>Ayrıca bkz.
- [IDE tarafından uygulanan geri çağırma işlevleri](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccQueryChanges](../extensibility/sccquerychanges-function.md)
- [Hata kodları](../extensibility/error-codes.md)
