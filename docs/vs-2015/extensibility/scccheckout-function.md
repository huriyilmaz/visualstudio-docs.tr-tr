---
title: SccCheckout Işlevi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccCheckout
helpviewer_keywords:
- SccCheckout function
ms.assetid: 06e9ecd7-fc09-40c1-9dd1-2b56c622c80b
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f23290ebfadd1b6e3d34f808d5ea0ccccbb3c319
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200160"
---
# <a name="scccheckout-function"></a>SccCheckout İşlevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tam nitelikli dosya adlarının listesi verildiğinde, bu işlev bunları yerel sürücüye iade eder. Yorum, kullanıma alınan tüm dosyalar için geçerlidir. Açıklama bağımsız değişkeni bir dize olabilir `null` .  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
SCCRTN SccCheckout (  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LPCSTR    lpComment,  
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
 'ndaki Kullanıma almak için seçilen dosya sayısı.  
  
 lpDosyaAdı  
 'ndaki Kullanıma alınan dosyaların tam nitelikli yerel yol adları dizisi.  
  
 lpComment açıklaması  
 'ndaki Kullanıma alınan seçili dosyaların her birine uygulanacak yorum.  
  
 fOptions  
 'ndaki Komut bayrakları (bkz. [belirli komutlar tarafından kullanılan Bitflags](../extensibility/bitflags-used-by-specific-commands.md)).  
  
 pvOptions  
 'ndaki Kaynak denetimi eklentisi özel seçenekleri.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu işlevin kaynak denetimi eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|SCC_OK|Kullanıma alma başarılı oldu.|  
|SCC_E_FILENOTCONTROLLED|Seçili dosya kaynak kodu denetimi altında değil.|  
|SCC_E_ACCESSFAILURE|Büyük olasılıkla ağ veya çekişme sorunlarından dolayı kaynak denetim sistemine erişirken bir sorun oluştu. Yeniden deneme önerilir.|  
|SCC_E_NOTAUTHORIZED|Kullanıcının bu işlemi gerçekleştirmesine izin verilmiyor.|  
|SCC_E_NONSPECIFICERROR|Özel olmayan hata. Dosya kullanıma alınamadı.|  
|SCC_E_ALREADYCHECKEDOUT|Kullanıcının dosyası zaten kullanıma alındı.|  
|SCC_E_FILEISLOCKED|Dosya kilitli ve yeni sürümlerin oluşturulmasını yasaklıyor.|  
|SCC_E_FILEOUTEXCLUSIVE|Başka bir Kullanıcı bu dosyada özel kullanıma alma işlemi yapmış.|  
|SCC_I_OPERATIONCANCELED|İşlem tamamlanmadan önce iptal edildi.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kaynak denetimi eklentisi API Işlevleri](../extensibility/source-control-plug-in-api-functions.md)   
 [Özel Komutlar Tarafından Kullanılan Bit Bayrakları](../extensibility/bitflags-used-by-specific-commands.md)
