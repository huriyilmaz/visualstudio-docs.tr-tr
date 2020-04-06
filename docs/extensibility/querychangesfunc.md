---
title: QUERYCHANGESFUNC | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- QUERYCHANGESFUNC
helpviewer_keywords:
- QUERYCHANGESFUNC callback function
- QUERYCHANGESDATA structure
ms.assetid: 9d383e2c-eee1-4996-973a-0652d4c5951c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 30864cae95672f4026084a94c5474d165b124cba
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701642"
---
# <a name="querychangesfunc"></a>QUERYCHANGESFUNC
Bu, dosya adlarının bir koleksiyonunu sayısallandırmak ve her dosyanın durumunu belirlemek için [SccQueryChanges](../extensibility/sccquerychanges-function.md) işlemi tarafından kullanılan bir geri arama işlevidir.

 İşlev, `SccQueryChanges` dosyaların bir listesini ve `QUERYCHANGESFUNC` geri arama için bir işaretçi verilir. Kaynak denetimi eklentisi verilen liste üzerinde sayısallar ve listedeki her dosya için durum (bu geri arama yoluyla) sağlar.

## <a name="signature"></a>İmza

```cpp
typedef BOOL (*QUERYCHANGESFUNC)(
   LPVOID pvCallerData,
   QUERYCHANGESDATA * pChangesData
);
```

## <a name="parameters"></a>Parametreler
 pvCallerData

[içinde] Arayan `pvCallerData` (IDE) tarafından [SccQueryChanges'a](../extensibility/sccquerychanges-function.md)geçirilen parametre. Kaynak denetimi eklentisi bu değerin içeriği hakkında hiçbir varsayımda bulunmamalıdır.

 pChangesData

[içinde] Bir dosyadaki değişiklikleri açıklayan bir [QUERYCHANGESDATA Yapısı](#LinkQUERYCHANGESDATA) için işaretçi.

## <a name="return-value"></a>Döndürülen değer
 IDE uygun bir hata kodu döndürür:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|İşleme devam edin.|
|SCC_I_OPERATIONCANCELED|İşlemi durdurun.|
|SCC_E_xxx|Uygun herhangi bir SCC hatası işlemeyi durdurmalıdır.|

## <a name="querychangesdata-structure"></a><a name="LinkQUERYCHANGESDATA"></a>QUERYCHANGESDATA Yapısı
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

 dwSize Bu yapının boyutu (bayt olarak).

 lpFileName Bu öğenin özgün dosya adı.

 dosyanın durumunu belirten dwChangeType Kodu:

|Kod|Açıklama|
|----------|-----------------|
|`SCC_CHANGE_UNKNOWN`|Neyin değiştiğini söyleyemem.|
|`SCC_CHANGE_UNCHANGED`|Bu dosya için ad değişikliği yok.|
|`SCC_CHANGE_DIFFERENT`|Dosya farklı bir kimliğe sahip, ancak aynı ad veritabanında var.|
|`SCC_CHANGE_NONEXISTENT`|Dosya veritabanında veya yerel olarak yok.|
|`SCC_CHANGE_DATABASE_DELETED`|Dosya veritabanında silindi.|
|`SCC_CHANGE_LOCAL_DELETED`|Dosya yerel olarak silindi, ancak dosya veritabanında hala var. Bu belirlenemiyorsa, `SCC_CHANGE_DATABASE_ADDED`geri dönün.|
|`SCC_CHANGE_DATABASE_ADDED`|Dosya veritabanına eklendi, ancak yerel olarak yok.|
|`SCC_CHANGE_LOCAL_ADDED`|Dosya veritabanında yok ve yeni bir yerel dosyadır.|
|`SCC_CHANGE_RENAMED_TO`|Dosya nın adı yeniden adlandırıldı `lpLatestName`veya veritabanında ' olarak taşındı.|
|`SCC_CHANGE_RENAMED_FROM`|Dosya yeniden adlandırıldı veya veritabanında `lpLatestName`taşındı; bu izlemek için çok pahalı ise, farklı `SCC_CHANGE_DATABASE_ADDED`bir bayrak döndürün, gibi.|

 lpLatestName Bu öğenin geçerli dosya adı.

## <a name="see-also"></a>Ayrıca bkz.
- [IDE tarafından uygulanan geri arama işlevleri](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccQueryChanges](../extensibility/sccquerychanges-function.md)
- [Hata kodları](../extensibility/error-codes.md)
