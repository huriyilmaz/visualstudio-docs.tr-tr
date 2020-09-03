---
title: SccUncheckout Işlevi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccUncheckout
helpviewer_keywords:
- SccUncheckout function
ms.assetid: 6d498b70-29c7-44b7-ae1c-7e99e488bb09
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3ae5ecd7568a10936479f72f92e9914132f2dcdf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68190858"
---
# <a name="sccuncheckout-function"></a>SccUncheckout İşlevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu işlev önceki bir kullanıma alma işlemini geri alır ve böylece seçilen dosya veya dosyaların içeriğini kullanıma almadan önceki duruma geri yükler. Kullanıma alma işleminden bu yana dosyada yapılan tüm değişiklikler kayboldu.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
SCCRTN SccUncheckout (  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 pvContext  
 'ndaki Kaynak denetimi eklentisi bağlam yapısı.  
  
 lendiği  
 'ndaki Kaynak denetimi eklentisinin, sağladığı tüm iletişim kutuları için üst öğe olarak kullanabileceği IDE penceresi için bir işleyici.  
  
 Nkarşıya  
 'ndaki Dizide belirtilen dosya sayısı `lpFileNames` .  
  
 lpDosyaAdı  
 'ndaki Bir kullanıma alma işlemini geri almak için gereken dosyaların tam nitelikli yerel yol adları dizisi.  
  
 fOptions  
 'ndaki Komut bayrakları (kullanılmıyor).  
  
 pvOptions  
 'ndaki Kaynak denetimi eklentisi özel seçenekleri.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu işlevin kaynak denetimi eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|SCC_OK|Kullanıma alma başarıyla geri alındı.|  
|SCC_E_FILENOTCONTROLLED|Seçili dosya kaynak kodu denetimi altında değil.|  
|SCC_E_ACCESSFAILURE|Büyük olasılıkla ağ veya çekişme sorunlarından dolayı kaynak denetim sistemine erişirken bir sorun oluştu. Yeniden deneme önerilir.|  
|SCC_E_NONSPECIFICERROR|Özel olmayan hata. Kullanıma alma başarıyla geri alınamıyor.|  
|SCC_E_NOTCHECKEDOUT|Kullanıcının dosyası kullanıma alınmamış.|  
|SCC_E_NOTAUTHORIZED|Kullanıcının bu işlemi gerçekleştirmesine izin verilmiyor.|  
|SCC_E_PROJNOTOPEN|Proje, kaynak denetiminden açılmamış.|  
|SCC_I_OPERATIONCANCELED|İşlem tamamlanmadan önce iptal edildi.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu işlemden sonra, `SCC_STATUS_CHECKEDOUT` ve `SCC_STATUS_MODIFIED` bayrakları geri alma işleminin gerçekleştirildiği dosyalar için temizlenir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kaynak Denetimi Eklentisi API İşlevleri](../extensibility/source-control-plug-in-api-functions.md)
