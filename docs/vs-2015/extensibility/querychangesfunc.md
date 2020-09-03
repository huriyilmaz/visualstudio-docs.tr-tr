---
title: QUERYCHANGESFUNC | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- QUERYCHANGESFUNC
helpviewer_keywords:
- QUERYCHANGESFUNC callback function
- QUERYCHANGESDATA structure
ms.assetid: 9d383e2c-eee1-4996-973a-0652d4c5951c
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 42f901fa31b3b682c7e19c98f5707adb3b4fb3f3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193843"
---
# <a name="querychangesfunc"></a>QUERYCHANGESFUNC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu, bir dosya adı koleksiyonunu numaralandırmak ve her bir dosyanın durumunu belirleyebilmek için [SccQueryChanges](../extensibility/sccquerychanges-function.md) işlemi tarafından kullanılan bir geri çağırma işlevidir.  
  
 `SccQueryChanges`İşleve bir dosya listesi ve `QUERYCHANGESFUNC` geri çağırma işaretçisi verilmiştir. Kaynak denetimi eklentisi verilen listeyi numaralandırır ve listedeki her dosya için durum (Bu geri çağırma aracılığıyla) sağlar.  
  
## <a name="signature"></a>İmza  
  
```cpp#  
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
  
## <a name="return-value"></a>Dönüş Değeri  
 IDE, uygun bir hata kodu döndürür:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|SCC_OK|İşleme devam edin.|  
|SCC_I_OPERATIONCANCELED|İşlemeyi durdur.|  
|SCC_E_xxx|Uygun bir SCC hatası işlemeyi durdurmalıdır.|  
  
## <a name="querychangesdata-structure"></a><a name="LinkQUERYCHANGESDATA"></a> QUERYCHANGESDATA yapısı  
 Her dosya için geçirilen yapı aşağıdaki gibi görünür:  
  
```cpp#  
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
  
 dwSize  
 Bu yapının boyutu (bayt).  
  
 lpFileName  
 Bu öğenin özgün dosya adı.  
  
 dwChangeType  
 Dosyanın durumunu belirten kod:  
  
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
  
 lpLatestName  
 Bu öğe için geçerli dosya adı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDE tarafından uygulanan geri çağırma Işlevleri](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccQueryChanges](../extensibility/sccquerychanges-function.md)   
 [Hata Kodları](../extensibility/error-codes.md)
