---
title: IActiveScriptParseProcedure32::P arseProcedureText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: ede37171-2f1e-4467-a358-17bd4a4f1869
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 52333d13731b5c31329ee812be403c09cf43d63b
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835738"
---
# <a name="iactivescriptparseprocedure32parseproceduretext"></a>IActiveScriptParseProcedure32::ParseProcedureText
Verilen kod yordamını ayrıştırır ve yordamı ad alanına ekler.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp
HRESULT ParseProcedureText(  
    LPCOLESTR pstrCode,              // address of procedure text  
    LPCOLESTR pstrFormalParams,      // address of formal parameter names  
    LPCOLESTR pstrProcedureName,     // address of procedure name  
    LPCOLESTR pstrItemName,          // address of item name  
    IUnknown *punkContext,           // address of debugging context  
    LPCOLESTR pstrDelimiter,         // address of end-of-procedure delimiter  
    DWORD_PTR dwSourceContextCookie, // application-defined value for debugging  
    ULONG ulStartingLineNumber,      // starting line of the script  
    DWORD dwFlags,                   // procedure flags  
    IDispatch **ppdisp               // receives IDispatch pointer  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pstrCode`  
 'ndaki Değerlendirilecek yordam metninin adresi. Bu dizenin yorumu, komut dosyası diline bağlıdır.  
  
 `pstrFormalParams`  
 'ndaki Yordamın biçimsel parametre adlarının adresi. Parametre adları, komut dosyası altyapısı için uygun sınırlayıcılarla ayrılmalıdır. Adlar parantez içine alınmalıdır.  
  
 `pstrProcedureName`  
 'ndaki Ayrıştırılacak yordam adının adresi.  
  
 `pstrItemName`  
 'ndaki Yordamın değerlendirildiği bağlamı veren öğe adının adresi. Bu parametre ise `NULL` kod, komut dosyası altyapısının genel bağlamında değerlendirilir.  
  
 `punkContext`  
 'ndaki Bağlam nesnesinin adresi. Bu nesne bir hata ayıklama ortamında kullanılmak üzere ayrılmıştır; burada, etkin bir çalışma zamanı bağlamını temsil etmek için bu tür bir bağlamın hata ayıklayıcı tarafından sağlanması olabilir. Bu parametre ise `NULL` , altyapı `pstrItemName` bağlamını tanımlamak için kullanır.  
  
 `pstrDelimiter`  
 'ndaki Yordamın sonu sınırlayıcısından oluşan adres. `pstrCode`Metin akışından ayrıştırıldığında, ana bilgisayar genellikle iki tek tırnak işareti (' ') gibi bir sınırlayıcı kullanır ve yordamın sonunu algılar. Bu parametre, ana bilgisayarın kullandığı sınırlayıcıyı belirtir ve betik altyapısının bazı koşullu temel bir ön işleme sağlamasına izin verir (örneğin, tek tırnak işaretini ['] sınırlayıcı olarak kullanılmak üzere iki tek tırnak işaretiyle değiştirme). Komut dosyası altyapısının bu bilgilerin kullanımını tam olarak nasıl (ve ne olursa) komut dosyası motoruna bağlıdır. `NULL`Ana bilgisayar yordamın sonunu işaretlemek için bir sınırlayıcı kullanmadığından bu parametreyi olarak ayarlayın.  
  
 `dwSourceContextCookie`  
 'ndaki Hata ayıklama amacıyla kullanılan uygulama tanımlı değer.  
  
 `ulStartingLineNumber`  
 'ndaki Ayrıştırmanın başlayacağı satırı belirten sıfır tabanlı değer.  
  
 `dwFlags`  
 'ndaki Yordamla ilişkili bayraklar. Şu değerlerin bir birleşimi olabilir:  
  
|Değer|Anlamı|  
|-----------|-------------|  
|SCRIPTPROC_ISEXPRESSION|İçindeki kodun, `pstrCode` yordamın dönüş değerini temsil eden bir ifade olduğunu gösterir. Varsayılan olarak, kod bir ifade, deyimler listesi veya komut dosyası dili tarafından yordamda izin verilen herhangi bir şeyi içerebilir.|  
|SCRIPTPROC_IMPLICIT_THIS|`this`İşaretçinin yordamın kapsamına dahil edildiğini belirtir.|  
|SCRIPTPROC_IMPLICIT_PARENTS|İşaretçinin üst öğelerinin `this` yordamın kapsamına dahil edileceğini gösterir.|  
  
 `ppdisp`  
 dışı Betiğin genel yöntemlerini ve özelliklerini içeren nesnenin işaretçisinin adresi. Betik altyapısı böyle bir nesneyi desteklemiyorsa, `NULL` döndürülür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Aşağıdaki değerlerden birini döndürür:  
  
|Dönüş Değeri|Anlamı|  
|------------------|-------------|  
|`S_OK`|Başarılı.|  
|`E_INVALIDARG`|Bağımsız değişken geçersizdi.|  
|`E_POINTER`|Geçersiz bir işaretçi belirtildi.|  
|`E_NOTIMPL`|Bu yöntem desteklenmiyor. Betik altyapısı, ad alanına yordamların çalışma zamanı eklenmesini desteklemez.|  
|`E_UNEXPECTED`|Çağrı beklenmiyordu (örneğin, komut dosyası altyapısı başlatılmamış veya kapalı durumda).|  
|`OLESCRIPT_E_SYNTAX`|Yordamda belirtilmeyen bir sözdizimi hatası oluştu.|  
|`S_FALSE`|Betik altyapısı bir dağıtım nesnesini desteklemez; `ppdisp`parametresi olarak ayarlanır `NULL` .|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu çağrı sırasında hiçbir betik kodu değerlendirilmedi; Bunun yerine, yordam betik tarafından daha sonra çağrılabilecek betik durumuna derlenir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IActiveScriptParseProcedure32](../../winscript/reference/iactivescriptparseprocedure32.md)