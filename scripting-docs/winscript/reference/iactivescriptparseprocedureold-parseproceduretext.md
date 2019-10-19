---
title: Iactivescriptparseprocedureold::P arseProcedureText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptParseProcedureOld.ParseProcedureText
apilocation:
- jscript.dll
helpviewer_keywords:
- IActiveScriptParseProcedureOld::ParseProcedureText
ms.assetid: 21a21313-35ce-432d-b9a6-7999065f19ac
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 116cbc7fac0d53b55c9766945d56ecebd27b6785
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577444"
---
# <a name="iactivescriptparseprocedureoldparseproceduretext"></a>IActiveScriptParseProcedureOld::ParseProcedureText
Verilen kod yordamını ayrıştırır ve ad alanına anonim bir yordam ekler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT ParseProcedureText(  
   LPCOLESTR    pstrCode,  
   LPCOLESTR    pstrFormalParams,  
   LPCOLESTR    pstrItemName,  
   IUnknown*    punkContext,  
   LPCOLESTR    pstrDelimiter,  
   DWORD_PTR    dwSourceContextCookie,  
   ULONG        ulStartingLineNumber,  
   DWORD        dwFlags,  
   IDispatch**  ppdisp  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pstrCode`  
 'ndaki Değerlendirilecek yordam metni. Bu dizenin yorumu, komut dosyası diline bağlıdır.  
  
 `pstrFormalParams`  
 'ndaki Yordamın biçimsel parametre adları. Parametre adları, komut dosyası altyapısı için uygun sınırlayıcılarla ayrılmalıdır. Adlar parantez içine alınmalıdır.  
  
 `pstrItemName`  
 'ndaki Yordamın değerlendirildiği bağlamı sağlayan adlandırılmış öğenin adı. Bu parametre `NULL` ise, kod betik altyapısının genel bağlamında değerlendirilir.  
  
 `punkContext`  
 'ndaki Bağlam nesnesi. Bu nesne bir hata ayıklama ortamında kullanılmak üzere ayrılmıştır; burada, etkin bir çalışma zamanı bağlamını temsil etmek için bu tür bir bağlamın hata ayıklayıcı tarafından sağlanması olabilir. Bu parametre `NULL`, altyapı bağlamını tanımlamak için `pstrItemName` kullanır.  
  
 `pstrDelimiter`  
 'ndaki Yordam sonu sınırlayıcısı. @No__t_0 metin akışından ayrıştırıldığında, ana bilgisayar genellikle iki tek tırnak işareti (' ') gibi bir sınırlayıcı kullanır ve yordamın sonunu algılar. Bu parametre, ana bilgisayarın kullandığı sınırlayıcıyı belirtir ve betik altyapısının bazı koşullu ve basit ön işleme sağlamasına izin verir (örneğin, tek tırnak işaretini ['] sınırlayıcı olarak kullanılmak üzere iki tek tırnak işaretiyle değiştirme). Betik altyapısının bu bilgileri kullanması tam olarak nasıl (ve ne olursa) komut dosyası altyapısına bağlıdır. Konak yordamın sonuna işaret eden bir sınırlayıcı kullanmadığından bu parametreyi `NULL` olarak ayarlayın.  
  
 `dwSourceContextCookie`  
 'ndaki Hata ayıklama amacıyla kullanılan uygulama tanımlı değer.  
  
 `ulStartingLineNumber`  
 'ndaki Ayrıştırmanın başlayacağı satırı belirten sıfır tabanlı değer.  
  
 `dwFlags`  
 'ndaki Yordamla ilişkili bayraklar. Bu değerlerin bir birleşimi olabilir.  
  
|Sabit|Değer|Açıklama|  
|--------------|-----------|-------------|  
|SCRIPTPROC_ISEXPRESSION|0x00000020|@No__t_0 içindeki kodun, yordamın dönüş değerini temsil eden bir ifade olduğunu gösterir.|  
|SCRIPTPROC_IMPLICIT_THIS|0x00000100|@No__t_0 işaretçisinin yordamın kapsamına dahil edileceğini gösterir.|  
|SCRIPTPROC_IMPLICIT_PARENTS|0x00000200|@No__t_0 işaretçisinin üst öğelerinin yordamın kapsamına dahil edileceğini gösterir.|  
  
 `ppdisp`  
 dışı Bu yöntem tarafından Ayrıştırılan yordamın varsayılan yönteminin olduğu bir dağıtım sarmalayıcısı döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
|`E_INVALIDARG`|Bağımsız değişken geçersizdi.|  
|`E_POINTER`|Geçersiz bir işaretçi belirtildi.|  
|`E_NOTIMPL`|Bu yöntem desteklenmiyor. Betik altyapısı, ad alanına yordamların çalışma zamanı eklenmesini desteklemez.|  
|`E_UNEXPECTED`|Çağrı beklenmiyordu (örneğin, komut dosyası altyapısı başlatılmamış veya kapalı durumda).|  
|`OLESCRIPT_E_SYNTAX`|Yordamda belirtilmeyen bir sözdizimi hatası oluştu.|  
|`S_FALSE`|Betik altyapısı bir dağıtım nesnesini desteklemez; `ppdisp`parameter `NULL` olarak ayarlanır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu çağrı sırasında hiçbir betik kodu değerlendirilmedi; Bunun yerine, yordam, betik tarafından daha sonra çağrılabilecek `ppdisp` bir yönteme derlenir.  
  
 Bu arabirim, `IActiveScriptParseProcedure` arabiriminin yararına kullanım dışıdır. @No__t_0 yöntemi bu yönteme benzerdir, ancak yordam adının belirtilmesini sağlar. Her durumda `IActiveScriptParseProcedure::ParseProcedureText` kullanılmalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Iactivescriptparseprocedureold arabirimi](../../winscript/reference/iactivescriptparseprocedureold-interface.md)    
 [IActiveScriptParseProcedure::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure-parseproceduretext.md)