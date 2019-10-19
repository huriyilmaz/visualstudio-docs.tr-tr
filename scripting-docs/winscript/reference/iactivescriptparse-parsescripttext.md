---
title: IActiveScriptParse::P arseScriptText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptParse.ParseScriptText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptParse_ParseScriptText
ms.assetid: 2d237d6c-cc65-415b-8808-72791304a136
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b4f35b398a7348f4e2bdbaaa9ab3e322bf69ddb6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72561615"
---
# <a name="iactivescriptparseparsescripttext"></a>IActiveScriptParse::ParseScriptText
Verilen kod kod oluşturma yöntemi ayrıştırır, ad alanına bildirimler ekliyor ve kodu uygun şekilde değerlendiriyor.  
  
## <a name="syntax"></a>Sözdizimi  
  
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
  
|||  
|-|-|  
|`pstrCode`|'ndaki Değerlendirilecek kod oluşturma yöntemi metninin adresi. Bu dizenin yorumu, komut dosyası diline bağlıdır.|  
|`pstrItemName`|'ndaki Kod oluşturma yöntemi değerlendirileceği bağlamı sağlayan öğe adının adresi. Bu parametre NULL ise, kod betik altyapısının genel bağlamında değerlendirilir.|  
|`punkContext`|'ndaki Bağlam nesnesinin adresi. Bu nesne bir hata ayıklama ortamında kullanılmak üzere ayrılmıştır; burada, etkin bir çalışma zamanı bağlamını temsil etmek için bu tür bir bağlamın hata ayıklayıcı tarafından sağlanması olabilir. Bu parametre NULL ise, altyapı bağlamını tanımlamak için `pstrItemName` kullanır.|  
|`pstrDelimiter`|'ndaki Son kod oluşturma yöntemi sınırlayıcısı adresi. @No__t_0 metin akışından ayrıştırıldığında, ana bilgisayar genellikle iki tek tırnak işareti (' ') gibi bir sınırlayıcı kullanır, bu da kod oluşturma yöntemi sonunu algılar. Bu parametre, ana bilgisayarın kullandığı sınırlayıcıyı belirtir ve betik altyapısının bazı koşullu temel bir ön işleme sağlamasına izin verir (örneğin, tek tırnak işaretini ['] sınırlayıcı olarak kullanılmak üzere iki tek tırnak işaretiyle değiştirme). Komut dosyası altyapısının bu bilgilerin kullanımını tam olarak nasıl (ve ne olursa) komut dosyası motoruna bağlıdır. Konak, kod oluşturma yöntemi sonunu işaretlemek için bir sınırlayıcı kullanmadığından bu parametreyi `NULL` olarak ayarlayın.|  
|`dwSourceContextCookie`|'ndaki Hata ayıklama amacıyla kullanılan tanımlama bilgisi.|  
|`ulStartingLineNumber`|'ndaki Ayrıştırmanın başlayacağı satırı belirten sıfır tabanlı değer.|  
|`dwFlags`|'ndaki Kod oluşturma yöntemi ile ilişkili bayraklar. Şu değerlerin bir birleşimi olabilir:|  
  
|Değer|Açıklama|  
|-----------|-------------|  
|SCRIPTTEXT_ISEXPRESSION|Bir hesaplama ifadesi ve deyim arasındaki ayrım önemli ancak betik dilinde belirsiz ise, bu bayrak, kod oluşturma yöntemi 'in bir deyim veya deyimler listesi yerine bir ifade olarak yorumlanacağı belirtir. Varsayılan olarak, kod oluşturma yöntemi metninin sözdiziminden doğru seçim belirlenemiyorsa, deyimler varsayılır.|  
|SCRIPTTEXT_ISPERSISTENT|Betik altyapısı kaydedilirse (örneğin, `IPersist*::Save` çağrısıyla) veya komut dosyası altyapısı başlatılmış duruma geri geçiş yöntemiyle sıfırlandığında, bu çağrı sırasında eklenen kodun kaydedilmesi gerektiğini gösterir.|  
|SCRIPTTEXT_ISVISIBLE|Betik metninin, betiğin ad alanında genel bir yöntem olarak görünür (ve bu nedenle Ada göre çağrılabilir) olacağını gösterir.|  
  
|||  
|-|-|  
|`pvarResult`|dışı Kod oluşturma yöntemi işlemenin sonuçlarını alan bir arabelleğin adresi `NULL` veya arayan hiçbir sonuç bekliyorsa (yani, SCRIPTTEXT_ISEXPRESSION değeri ayarlanmamışsa).|  
|`pexcepinfo`|dışı Özel durum bilgilerini alan yapının adresi. @No__t_0 DISP_E_EXCEPTION döndürürse bu yapı doldurulur.|  
  
## <a name="return-value"></a>Dönüş Değeri  
 Aşağıdaki değerlerden birini döndürür:  
  
|Dönüş Değeri|Açıklama|  
|------------------|-------------|  
|`S_OK`|Başarılı.|  
|`DISP_E_EXCEPTION`|Kod oluşturma yöntemi işlenirken bir özel durum oluştu. @No__t_0 parametresi özel durum hakkında bilgi içerir.|  
|`E_INVALIDARG`|Bağımsız değişken geçersizdi.|  
|`E_POINTER`|Geçersiz bir işaretçi belirtildi.|  
|`E_NOTIMPL`|Bu yöntem desteklenmiyor. Betik altyapısı, ifadelerin veya deyimlerin çalışma zamanı değerlendirmesini desteklemez.|  
|`E_UNEXPECTED`|Çağrı beklenmedi (örneğin, komut dosyası altyapısı başlatılmamış veya kapalı durumda veya SCRIPTTEXT_ISEXPRESSION bayrağı ayarlanmış ve betik altyapısı başlatılmış durumda).|  
|`OLESCRIPT_E_SYNTAX`|Kod oluşturma yöntemi içinde belirtilmeyen bir sözdizimi hatası oluştu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Betik altyapısı başlatılmış durumdaysa, bu çağrı sırasında gerçekte hiçbir kod değerlendirilmeyecektir; Bunun yerine, bu tür kod kuyruğa alınır ve komut dosyası altyapısı başlatılan durumuna geçiş yaparken (veya üzerinden) yürütülür. Başlatma durumunda yürütmeye izin verilmediğinden, bu yöntemi başlatılan durumunda SCRIPTTEXT_ISEXPRESSION bayrağıyla çağırmak hatadır.  
  
 Kod oluşturma yöntemi bir ifade, deyimler listesi veya betik dili tarafından izin verilen herhangi bir şey olabilir. Örneğin, bu yöntem, komut dosyası durumuna derlemek yerine, deyimlerin HTML sayfası oluşturulmakta olduğu şekilde yürütülmesine izin veren HTML \<SCRIPT > etiketinin değerlendirmesinde kullanılır.  
  
 Bu yönteme geçirilen kod, kodun geçerli ve tamamen bir kısmı olmalıdır. Örneğin, VBScript içinde bu yöntemi Sub Function (x) ile bir kez ve sonra `End Sub` ikinci kez çağırmak geçersizdir. Ayrıştırıcı ikinci çağrının alt yordamı tamamlamasını beklememelidir, ancak bunun yerine bir altyordam bildirimi başlatıldığından ancak tamamlanmadığından bir ayrıştırma hatası üretmemelidir.  
  
 Betik durumları hakkında daha fazla bilgi için [Windows komut dosyası altyapılarının](../../winscript/windows-script-engines.md)komut dosyası altyapısı durumları bölümüne bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)