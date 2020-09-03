---
title: SccCheckin Işlevi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccCheckin
helpviewer_keywords:
- SccCheckin function
ms.assetid: e3f26ac2-6163-42e1-a764-22cfea5a3bc6
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d8a5a91a0300f256b66970403a3431edf0fe757e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68189538"
---
# <a name="scccheckin-function"></a>SccCheckin İşlevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu işlev, önceden kullanıma alınmış dosyaları kaynak denetim sistemine iade eder, değişiklikleri depolayarak ve yeni bir sürüm oluşturuyor. Bu işlev bir sayı ve iade edilecek dosyaların bir adı dizisiyle çağrılır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
SCCRTN SccCheckin (  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPSTR*    lpFileNames,  
   LPCSTR    lpComment,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 pvContext  
 'ndaki Kaynak denetimi eklentisi bağlam yapısı.  
  
 lendiği  
 'ndaki SCC eklentisinin sağladığı tüm iletişim kutuları için üst öğe olarak kullanabileceği IDE penceresi için bir işleyici.  
  
 Nkarşıya  
 'ndaki İade edilecek seçili dosya sayısı.  
  
 lpDosyaAdı  
 'ndaki İade edilecek dosyaların tam nitelikli yerel yol adları dizisi.  
  
 lpComment açıklaması  
 'ndaki İşaretlenmiş seçili dosyaların her birine uygulanacak yorum. Bu, `NULL` kaynak denetimi eklentisinin bir açıklama sorması durumunda olur.  
  
 fOptions  
 'ndaki Komut bayrakları, 0 ya da `SCC_KEEP_CHECKEDOUT` .  
  
 pvOptions  
 'ndaki SCC eklentisine özgü seçenekler.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu işlevin kaynak denetimi eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|SCC_OK|Dosyalar başarıyla iade edildi.|  
|SCC_E_FILENOTCONTROLLED|Seçili dosya kaynak kodu denetimi altında değil.|  
|SCC_E_ACCESSFAILURE|Büyük olasılıkla ağ veya çekişme sorunlarından dolayı kaynak denetim sistemine erişirken bir sorun oluştu. Yeniden deneme önerilir.|  
|SCC_E_NONSPECIFICERROR|Özel olmayan hata. Dosya iade edilmedi.|  
|SCC_E_NOTCHECKEDOUT|Kullanıcı dosyayı kullanıma almadı, bu nedenle iade edilemiyor.|  
|SCC_E_CHECKINCONFLICT|İade etme gerçekleştirilemedi çünkü:<br /><br /> -Başka bir kullanıcı iade etti ve `bAutoReconcile` yanlış.<br /><br /> -veya-<br /><br /> -Otomatik birleştirme yapılamaz (örneğin, dosyalar ikili olduğunda).|  
|SCC_E_VERIFYMERGE|Dosya otomatik olarak birleştirildi, ancak bekleyen Kullanıcı doğrulamasında iade edilmedi.|  
|SCC_E_FIXMERGE|Dosya otomatik olarak birleştirildi, ancak el ile çözümlenmesi gereken bir birleştirme çakışması nedeniyle iade edilmedi.|  
|SCC_E_NOTAUTHORIZED|Kullanıcının bu işlemi gerçekleştirmesine izin verilmiyor.|  
|SCC_I_OPERATIONCANCELED|İşlem tamamlanmadan önce iptal edildi.|  
|SCC_I_RELOADFILE|Bir dosya veya projenin yeniden yüklenmesi gerekiyor.|  
|SCC_E_FILENOTEXIST|Yerel dosya bulunamadı.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yorum, denetlenen tüm dosyalar için geçerlidir. Yorum bağımsız değişkeni bir dize olabilir `null` , bu durumda kaynak denetimi eklentisi kullanıcıdan her dosya için bir açıklama dizesi isteyebilir.  
  
 `fOptions`Bağımsız değişkenine `SCC_KEEP_CHECKEDOUT` kullanıcının içinde dosyayı denetleme amacını belirten bir bayrak değeri verilebilir ve yeniden kullanıma alabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kaynak Denetimi Eklentisi API İşlevleri](../extensibility/source-control-plug-in-api-functions.md)
