---
title: 'IActiveScriptParse32:: AddScriptlet | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fcf11eb2-8e71-4cca-afda-a91791c243ff
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: b48d89ce2c49bd971fe298d2b4773aad8b65e8c3
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72561702"
---
# <a name="iactivescriptparse32addscriptlet"></a>IActiveScriptParse32::AddScriptlet
Betiğe bir kod oluşturma yöntemi kodu ekler. Bu yöntem, betiğin kalıcı durumunun konak belgesiyle intertwined olduğu ve ana bilgisayarın bir `IPersist*` arabirimi yerine betiği geri yüklemeden sorumlu olduğu ortamlarda kullanılır. Birincil örnekler, HTML belgesinde katıştırılmış kodun betiklerinin iç olaylara eklenmesine izin veren HTML komut dosyası dillerinin (örneğin, ONCLICK = "Button1. Text = ' Exit '").  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT AddScriptlet(  
    LPCOLESTR pstrDefaultName,       // address of default name of scriptlet  
    LPCOLESTR pstrCode,              // address of scriptlet text  
    LPCOLESTR pstrItemName,          // address of item name  
    LPCOLESTR pstrSubItemName,       // address of subitem name  
    LPCOLESTR pstrEventName,         // address of event name  
    LPCOLESTR pstrDelimiter,         // address of end-of-scriptlet delimiter  
    DWORD_PTR dwSourceContextCookie, // application-defined value for debugging  
    ULONG ulStartingLineNumber,      // starting line of the script  
    DWORD dwFlags,                   // scriptlet flags  
    BSTR *pbstrName,                 // address of actual name of scriptlet  
    EXCEPINFO *pexcepinfo            // address of exception information  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pstrDefaultName`  
 'ndaki Kod oluşturma yöntemi ile ilişkilendirilecek varsayılan adın adresi. Kod oluşturma yöntemi, adlandırma bilgileri içermiyorsa (yukarıdaki ONCLICK örneğinde olduğu gibi), bu ad kod oluşturma yöntemi tanımlamak için kullanılacaktır. Bu parametre `NULL` ise, komut dosyası altyapısı gerekirse benzersiz bir ad üreten.  
  
 `pstrCode`  
 'ndaki Eklenecek kod oluşturma yöntemi metninin adresi. Bu dizenin yorumu, komut dosyası diline bağlıdır.  
  
 `pstrItemName`  
 'ndaki Bu kod oluşturma yöntemi ile ilişkili öğe adını içeren bir arabelleğin adresi. Bu parametre, `pstrSubItemName` ek olarak, kod oluşturma yöntemi olay işleyicisi olan nesneyi tanımlar.  
  
 `pstrSubItemName`  
 'ndaki Bu kod oluşturma yöntemi ilişkili olan adlandırılmış öğenin `subobject` adını içeren bir arabelleğin adresi; Bu adın adlandırılmış öğenin tür bilgilerinde bulunması gerekir. Bu parametre, kod oluşturma yöntemi `subitem` yerine adlandırılmış öğeyle ilişkilendirilirse NULL olur. Bu parametre, `pstrItemName` ek olarak, kod oluşturma yöntemi olay işleyicisi olduğu belirli nesneyi tanımlar.  
  
 `pstrEventName`  
 'ndaki Kod oluşturma yöntemi olay işleyicisi olduğu olayın adını içeren bir arabelleğin adresi.  
  
 `pstrDelimiter`  
 'ndaki Son kod oluşturma yöntemi sınırlayıcısı adresi. @No__t_0 parametresi metin akışından ayrıştırıldığında, ana bilgisayar genellikle iki tek tırnak işareti (' ') gibi bir sınırlayıcı kullanır, bu da kod oluşturma yöntemi sonunu algılar. Bu parametre, ana bilgisayarın kullandığı sınırlayıcıyı belirtir ve betik altyapısının bazı koşullu temel bir ön işleme sağlamasına izin verir (örneğin, tek tırnak işaretini ['] sınırlayıcı olarak kullanılmak üzere iki tek tırnak işaretiyle değiştirme). Komut dosyası altyapısının bu bilgilerin kullanımını tam olarak nasıl (ve ne olursa) komut dosyası motoruna bağlıdır. Konak, kod oluşturma yöntemi sonunu işaretlemek için bir sınırlayıcı kullanmadığından bu parametreyi NULL olarak ayarlayın.  
  
 `dwSourceContextCookie`  
 'ndaki Hata ayıklama amacıyla kullanılan uygulama tanımlı değer.  
  
 `ulStartingLineNumber`  
 'ndaki Ayrıştırmanın başlayacağı satırı belirten sıfır tabanlı değer.  
  
 `dwFlags`  
 'ndaki Kod oluşturma yöntemi ile ilişkili bayraklar. Aşağıdaki değerlerin bir birleşimi olabilir:  
  
|Dönüş Değeri|Açıklama|  
|------------------|-------------|  
|SCRIPTTEXT_ISVISIBLE|Betik metninin, betiğin ad alanında genel bir yöntem olarak görünür (ve bu nedenle Ada göre çağrılabilir) olacağını gösterir.|  
|SCRIPTTEXT_ISPERSISTENT|Betik altyapısı kaydedilirse (örneğin, `IPersist*::Save` çağrısıyla) veya komut dosyası altyapısı başlatılmış duruma geri geçiş yöntemiyle sıfırlandığında, bu çağrı sırasında eklenen kodun kaydedilmesi gerektiğini gösterir. Bu durum hakkında daha fazla bilgi için bkz. betik altyapısı durumları.|  
  
 `pbstrName`,  
 dışı Kod oluşturma yöntemi tanımlamak için kullanılan gerçek ad. Bu, tercih sırasına göre yapılır: kod oluşturma yöntemi metninde açıkça belirtilen bir ad, `pstrDefaultName` olarak girilen varsayılan ad veya betik altyapısı tarafından bir benzersiz ad.  
  
 `pexcepinfo`,  
 dışı Özel durum bilgisi içeren bir yapının adresi. DISP_E_EXCEPTION döndürülürse bu yapı doldurulmalıdır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Aşağıdaki değerlerden birini döndürür:  
  
|Dönüş Değeri|Açıklama|  
|------------------|-------------|  
|`S_OK`|Başarılı.|  
|`DISP_E_EXCEPTION`|Kod oluşturma yöntemi ayrıştırılırken bir özel durum oluştu. @No__t_0 parametresi özel durum hakkında bilgi içerir.|  
|`E_INVALIDARG`|Bağımsız değişken geçersizdi.|  
|`E_NOTIMPL`|Bu yöntem desteklenmez; betik altyapısı, olay sıkıştırma betiklerinin eklenmesini desteklemez.|  
|`E_POINTER`|Geçersiz bir işaretçi belirtildi.|  
|`E_UNEXPECTED`|Çağrı beklenmiyordu (örneğin, komut dosyası altyapısı henüz yüklenmemiş veya başlatılmamış) ve bu nedenle başarısız oldu.|  
|`OLESCRIPT_E_INVALIDNAME`|Sağlanan varsayılan ad bu komut dosyası dilinde geçersiz.|  
|`OLESCRIPT_E_SYNTAX`|Kod oluşturma yöntemi içinde belirtilmeyen bir sözdizimi hatası oluştu.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IActiveScriptParse32](../../winscript/reference/iactivescriptparse32.md)