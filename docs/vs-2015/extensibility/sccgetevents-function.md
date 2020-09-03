---
title: SccGetEvents Işlevi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccGetEvents
helpviewer_keywords:
- SccGetEvents function
ms.assetid: 32f8147d-6dcc-465e-b07b-42da5824f9b0
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d975570334aeab7c6709db92f3240a8e8d06b131
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200116"
---
# <a name="sccgetevents-function"></a>SccGetEvents İşlevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu işlev, bir sıraya alınmış durum olayını alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
SCCRTN SccGetEvents (  
   LPVOID pvContext,  
   LPSTR  lpFileName,  
   LPLONG lpStatus,  
   LPLONG pnEventsRemaining  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 pvContext  
 'ndaki Kaynak denetimi eklentisi bağlam yapısı.  
  
 lpFileName  
 [in, out] Kaynak denetimi eklentisinin döndürülen dosya adını (_MAX_PATH karaktere kadar) yerleştirme arabelleği.  
  
 lpStatus  
 [in, out] Durum kodunu döndürür (olası değerler için [dosya durum koduna](../extensibility/file-status-code-enumerator.md) bakın).  
  
 Pneventskaldı  
 [in, out] Bu çağrıdan sonra sırada kalan giriş sayısını döndürür. Bu sayı büyükse, çağıran tüm bilgileri bir kerede almak için [SccQueryInfo](../extensibility/sccqueryinfo-function.md) çağrısına karar verebilir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu işlevin kaynak denetimi eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|SCC_OK|Olayları başarılı bir şekilde alın.|  
|SCC_E_OPNOTSUPPORTED|Bu işlev desteklenmiyor.|  
|SCC_E_NONSPECIFICERROR|Özel olmayan hata.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu işlev, kaynak denetimi altındaki dosyalar için herhangi bir durum güncelleştirmesi olup olmadığını görmek için boşta işleme sırasında çağrılır. Kaynak denetimi eklentisi, bildiği tüm dosyaların durumunu korur ve eklenti tarafından bir durum değişikliği olduğunda, durum ve ilişkili dosya bir kuyrukta depolanır. `SccGetEvents`Çağrıldığında, sıranın üst öğesi alınır ve döndürülür. Bu işlev, yalnızca daha önce önbelleğe alınmış bilgileri döndürecek şekilde kısıtlıdır ve çok hızlı bir şekilde (disk okuma veya kaynak denetim sistemine durum sorma) sahip olmalıdır; Aksi takdirde IDE 'nin performansı azalmayı başlatabilir.  
  
 Raporlanacak durum güncelleştirmesi yoksa, kaynak denetimi eklentisi tarafından işaret edilen arabellekte boş bir dize depolar `lpFileName` . Aksi halde eklenti, durum bilgisinin değiştiği dosyanın tam yol adını depolar ve uygun durum kodunu ( [dosya durum kodunda](../extensibility/file-status-code-enumerator.md)ayrıntılanmış değerlerden biri) döndürür.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kaynak denetimi eklentisi API Işlevleri](../extensibility/source-control-plug-in-api-functions.md)   
 [Dosya Durumu Kodu](../extensibility/file-status-code-enumerator.md)
