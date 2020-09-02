---
title: SccQueryChanges Işlevi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccQueryChanges
helpviewer_keywords:
- SccQueryChanges function
ms.assetid: 4cd58eb3-6952-49b1-9620-8682e3eaa604
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: baa6059a1668be5507994921cb96ac3ed1cfd5fe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200008"
---
# <a name="sccquerychanges-function"></a>SccQueryChanges İşlevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu işlev, bir geri çağırma işlevi aracılığıyla her bir dosya için ad değişiklikleri hakkında bilgi sağlayan belirli bir dosya listesini numaralandırır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
SCCRTN SccQueryChanges(  
   LPVOID           pContext,  
   LONG             nFiles,  
   LPCSTR*          lpFileNames,  
   QUERYCHANGESFUNC pfnCallback,  
   LPVOID           pvCallerData  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 pContext  
 'ndaki Kaynak denetimi eklentisi bağlam işaretçisi.  
  
 Nkarşıya  
 'ndaki Dizideki dosya sayısı `lpFileNames` .  
  
 lpDosyaAdı  
 'ndaki Hakkında bilgi almak için dosya adları dizisi.  
  
 pfnCallback  
 'ndaki Listedeki her dosya adı için çağrı yapılacak geri çağırma işlevi (Ayrıntılar için bkz. [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md) ).  
  
 pvCallerData  
 'ndaki Geri çağırma işlevine değiştirilmeden geçirilecek değer.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu işlevin kaynak denetimi eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|SCC_OK|Sorgu işlemi başarıyla tamamlandı.|  
|SCC_E_PROJNOTOPEN|Proje kaynak denetiminde açılmadı.|  
|SCC_E_ACCESSFAILURE|Büyük olasılıkla ağ veya çekişme sorunlarından dolayı kaynak denetim sistemine erişirken bir sorun oluştu.|  
|SCC_E_NONSPECIFICERROR|Belirtilmeyen veya genel bir hata oluştu.|  
  
## <a name="remarks"></a>Açıklamalar  
 İçin sorgulanmakta olan değişiklikler ad alanı: özel olarak, bir dosyayı yeniden adlandırma, ekleme ve kaldırma.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kaynak denetimi eklentisi API Işlevleri](../extensibility/source-control-plug-in-api-functions.md)   
 [QUERYCHANGESFUNC IşLEVI](../extensibility/querychangesfunc.md)   
 [Hata Kodları](../extensibility/error-codes.md)
