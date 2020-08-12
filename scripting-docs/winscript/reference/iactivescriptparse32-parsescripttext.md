---
title: IActiveScriptParse32::P arseScriptText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: f33e454c-69d8-4cab-9150-d1e7fd04786d
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 9fd497dcda7e40cf0dbe6409193019ddae84c80b
ms.sourcegitcommit: d281d2a04a5bc302650eebf369946d8f101e59dd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2020
ms.locfileid: "88144408"
---
# <a name="iactivescriptparse32parsescripttext"></a>IActiveScriptParse32::ParseScriptText
Verilen kod kod oluşturma yöntemi ayrıştırır, ad alanına bildirimler ekliyor ve kodu uygun şekilde değerlendiriyor.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp
HRESULT ParseScriptText(  
    LPCOLESTR pstrCode,              // address of scriptlet text  
    LPCOLESTR pstrItemName,          // address of item name  
    IUnknown *punkContext,           // address of debugging context  
    LPCOLESTR pstrDelimiter,         // address of end-of-scriptlet delimiter  
    DWORD_PTR dwSourceContextCookie, // cookie for debugging  
    ULONG ulStartingLineNumber,      // starting line of the script  
    DWORD dwFlags,                   // scriptlet flags  
    VARIANT *pvarResult,             // address of buffer for results  
    EXCEPINFO *pexcepinfo            // address of buffer for error data  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
  
| Parametre | Açıklama |  
|-|-|  
|`pstrCode`|'ndaki Değerlendirilecek kod oluşturma yöntemi metninin adresi. Bu dizenin yorumu, komut dosyası diline bağlıdır.|  
|`pstrItemName`|'ndaki Kod oluşturma yöntemi değerlendirileceği bağlamı sağlayan öğe adının adresi. Bu parametre NULL ise, kod betik altyapısının genel bağlamında değerlendirilir.|  
|`punkContext`|'ndaki Bağlam nesnesinin adresi. Bu nesne bir hata ayıklama ortamında kullanılmak üzere ayrılmıştır; burada, etkin bir çalışma zamanı bağlamını temsil etmek için bu tür bir bağlamın hata ayıklayıcı tarafından sağlanması olabilir. Bu parametre NULL ise, altyapı `pstrItemName` bağlamını tanımlamak için kullanır.|  
|`pstrDelimiter`|'ndaki Son kod oluşturma yöntemi sınırlayıcısı adresi. `pstrCode`Metin akışından ayrıştırıldığında, ana bilgisayar genellikle iki tek tırnak işareti (' ') gibi bir sınırlayıcı kullanır, bu da kod oluşturma yöntemi sonunu algılar. Bu parametre, ana bilgisayarın kullandığı sınırlayıcıyı belirtir ve betik altyapısının bazı koşullu temel bir ön işleme sağlamasına izin verir (örneğin, tek tırnak işaretini ['] sınırlayıcı olarak kullanılmak üzere iki tek tırnak işaretiyle değiştirme). Komut dosyası altyapısının bu bilgilerin kullanımını tam olarak nasıl (ve ne olursa) komut dosyası motoruna bağlıdır. `NULL`Ana bilgisayar kod oluşturma yöntemi sonunu işaretlemek için bir sınırlayıcı kullanmadığından bu parametreyi olarak ayarlayın.|  
|`dwSourceContextCookie`|'ndaki Hata ayıklama amacıyla kullanılan tanımlama bilgisi.|  
|`ulStartingLineNumber`|'ndaki Ayrıştırmanın başlayacağı satırı belirten sıfır tabanlı değer.|  
|`dwFlags`|'ndaki Kod oluşturma yöntemi ile ilişkili bayraklar. Şu değerlerin bir birleşimi olabilir:|  
  
|Değer|Anlamı|  
|-----------|-------------|  
|SCRIPTTEXT_ISEXPRESSION|Bir hesaplama ifadesi ve deyim arasındaki ayrım önemli ancak betik dilinde belirsiz ise, bu bayrak, kod oluşturma yöntemi 'in bir deyim veya deyimler listesi yerine bir ifade olarak yorumlanacağı belirtir. Varsayılan olarak, kod oluşturma yöntemi metninin sözdiziminden doğru seçim belirlenemiyorsa, deyimler varsayılır.|  
|SCRIPTTEXT_ISPERSISTENT|Betik altyapısı kaydedilirse (örneğin, çağrısı yoluyla `IPersist*::Save` ) veya komut dosyası altyapısı başlatılmış duruma geri geçiş yöntemiyle sıfırlandığında, bu çağrı sırasında eklenen kodun kaydedilmesi gerektiğini belirtir.|  
|SCRIPTTEXT_ISVISIBLE|Betik metninin, betiğin ad alanında genel bir yöntem olarak görünür (ve bu nedenle Ada göre çağrılabilir) olacağını gösterir.|  
  
| Parametre | Açıklama |  
|-|-|  
|`pvarResult`|dışı Kod oluşturma yöntemi işlemenin sonuçlarını alan bir arabelleğin adresi veya `NULL` arayan hiçbir sonuç beklemdiğinde (yani, SCRIPTTEXT_ISEXPRESSION değeri ayarlı değildir).|  
|`pexcepinfo`|dışı Özel durum bilgilerini alan yapının adresi. DISP_E_EXCEPTION döndürürse bu yapı doldurulur `IActiveScriptParse::ParseScriptText` .|  
  
## <a name="return-value"></a>Dönüş Değeri  
 Aşağıdaki değerlerden birini döndürür:  
  
|Dönüş Değeri|Anlamı|  
|------------------|-------------|  
|`S_OK`|Başarılı.|  
|`DISP_E_EXCEPTION`|Kod oluşturma yöntemi işlenirken bir özel durum oluştu. `pexcepinfo`Parametresi, özel durum hakkında bilgi içerir.|  
|`E_INVALIDARG`|Bağımsız değişken geçersizdi.|  
|`E_POINTER`|Geçersiz bir işaretçi belirtildi.|  
|`E_NOTIMPL`|Bu yöntem desteklenmiyor. Betik altyapısı, ifadelerin veya deyimlerin çalışma zamanı değerlendirmesini desteklemez.|  
|`E_UNEXPECTED`|Çağrı beklenmedi (örneğin, komut dosyası altyapısı başlatılmamış veya kapalı durumda veya SCRIPTTEXT_ISEXPRESSION bayrağı ayarlanmış ve betik altyapısı başlatılmış durumda).|  
|`OLESCRIPT_E_SYNTAX`|Kod oluşturma yöntemi içinde belirtilmeyen bir sözdizimi hatası oluştu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Betik altyapısı başlatılmış durumdaysa, bu çağrı sırasında gerçekte hiçbir kod değerlendirilmeyecektir; Bunun yerine, bu tür kod kuyruğa alınır ve komut dosyası altyapısı başlatılan durumuna geçiş yaparken (veya üzerinden) yürütülür. Başlatma durumunda yürütmeye izin verilmediğinden, bu yöntemi başlatılan durumda SCRIPTTEXT_ISEXPRESSION bayrağıyla çağırmak hatadır.  
  
 Kod oluşturma yöntemi bir ifade, deyimler listesi veya betik dili tarafından izin verilen herhangi bir şey olabilir. Örneğin, bu yöntem HTML etiketinin değerlendirilmesinde kullanılır, bu, \<SCRIPT> deyimleri yalnızca komut dosyası durumuna derlemek yerıne HTML sayfası oluşturulmakta olan şekilde yürütülmesine izin verir.  
  
 Bu yönteme geçirilen kod, kodun geçerli ve tamamen bir kısmı olmalıdır. Örneğin, VBScript içinde bu yöntemi Sub Function (x) ve sonrasında ikinci kez çağırmak geçersizdir `End Sub` . Ayrıştırıcı ikinci çağrının alt yordamı tamamlamasını beklememelidir, ancak bunun yerine bir altyordam bildirimi başlatıldığından ancak tamamlanmadığından bir ayrıştırma hatası üretmemelidir.  
  
 Betik durumları hakkında daha fazla bilgi için [Windows komut dosyası altyapılarının](../../winscript/windows-script-engines.md)komut dosyası altyapısı durumları bölümüne bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IActiveScriptParse32](../../winscript/reference/iactivescriptparse32.md)