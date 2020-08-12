---
title: 'IDispatchEx:: InvokeEx | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.InvokeEx
apilocation:
- scrobj.dll
helpviewer_keywords:
- InvokeEx method
ms.assetid: d90783e6-4b89-4423-8a56-a9c8b4b2c813
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 673b3f1e64caa79dc2b21641209423d93fe0f834
ms.sourcegitcommit: d281d2a04a5bc302650eebf369946d8f101e59dd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2020
ms.locfileid: "88144421"
---
# <a name="idispatchexinvokeex"></a>IDispatchEx::InvokeEx
Bir nesne tarafından kullanıma sunulan özelliklere ve yöntemlere erişim sağlar `IDispatchEx` .  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp
HRESULT InvokeEx(  
   DISPID id,  
   LCID lcid,  
   WORD wFlags,  
   DISPARAMS *pdp,  
   VARIANT *pVarRes,   
   EXCEPINFO *pei,   
   IServiceProvider *pspCaller   
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `id`  
 Üyeyi tanımlar. `GetDispID` `GetNextDispID` Dağıtım tanımlayıcısını almak için veya kullanır.  
  
 `lcid`  
 Bağımsız değişkenlerin yorumlanacağı yerel ayar bağlamı. , `lcid` `InvokeEx` Nesnenin bir yerel ayara özgü bağımsız değişkenlerini yorumlamasını sağlamak için öğesine geçirilir.  
  
 `wFlags`  
 İçin geçerli değerler `wFlags` şunlardır:  
  
 DISPATCH_PROPERTYGET &#124; DISPATCH_METHOD &#124; DISPATCH_PROPERTYPUT &#124; DISPATCH_PROPERTYPUTREF &#124; DISPATCH_CONSTRUCT  
  
 Çağrının bağlamını açıklayan bayraklar `InvokeEx` :  
  
|Değer|Anlamı|  
|-----------|-------------|  
|DISPATCH_METHOD|Üye bir yöntem olarak çağrılır. Bir özellik aynı ada sahipse, hem bu hem de DISPATCH_PROPERTYGET bayrağı ayarlanabilir (tarafından tanımlanır `IDispatch` ).|  
|DISPATCH_PROPERTYGET|Üye bir özellik veya veri üyesi (tarafından tanımlanır) olarak alınır `IDispatch` .|  
|DISPATCH_PROPERTYPUT|Üye bir özellik veya veri üyesi olarak değiştirildi (tarafından tanımlanır `IDispatch` ).|  
|DISPATCH_PROPERTYPUTREF|Üye, bir değer ataması yerine bir başvuru ataması tarafından değiştirilir. Bu bayrak yalnızca özellik bir nesnenin başvurusunu kabul ettiğinde geçerlidir (tarafından tanımlanır `IDispatch` ).|  
|DISPATCH_CONSTRUCT|Üye bir Oluşturucu olarak kullanılıyor. (Bu, tarafından tanımlanan yeni bir değerdir `IDispatchEx` ). İçin geçerli değerler `wFlags` şunlardır:<br /><br /> DISPATCH_PROPERTYGET DISPATCH_METHOD DISPATCH_PROPERTYPUT DISPATCH_PROPERTYPUTREF DISPATCH_CONSTRUCT|  
  
 `pdp`  
 Bir dizi bağımsız değişkeni içeren bir yapıya yönelik işaretçi, adlandırılmış bağımsız değişkenler için bir dizi bağımsız değişken DISPID değeri ve dizilerdeki öğelerin sayısına ilişkin sayımlar. `IDispatch`DISPPARAMS yapısının tam açıklaması için belgelere bakın.  
  
 `pVarRes`  
 Çağıran hiçbir sonuç beklemdiğinde sonucun depolanacağı konuma veya null değere işaretçi. DISPATCH_PROPERTYPUT veya DISPATCH_PROPERTYPUTREF belirtilmişse bu bağımsız değişken yoksayılır.  
  
 `pei`  
 Özel durum bilgisi içeren bir yapıya yönelik işaretçi. Döndürülürse, bu yapı doldurulmalıdır `DISP_E_EXCEPTION` . Null olabilir. `IDispatch`Yapının tam açıklaması için belgelere bakın `EXCEPINFO` .  
  
 `pspCaller`  
 Çağıran tarafından sağlanan ve nesnenin çağırandan hizmet almasına izin veren bir hizmet sağlayıcı nesnesine yönelik işaretçi. Null olabilir.  
  
 `IDispatchEx::InvokeEx` , ile aynı özelliklerin tümünü sağlar `IDispatch::Invoke` ve birkaç uzantı ekler:  
  
|Değer|Anlamı|
|-|-|  
|DISPATCH_CONSTRUCT|Öğenin bir Oluşturucu olarak kullanıldığını belirtir.|  
|`pspCaller`|, `pspCaller` Çağıran tarafından sunulan hizmetlere nesne erişimine izin verir. Belirli hizmetler, arayanın kendisi tarafından işlenebilir veya çağrı zincirinin daha fazla arayanlara daha fazla çağrı yapılabilir. Örneğin, bir tarayıcı içindeki bir betik altyapısı bir `InvokeEx` dış nesneye çağrı yapıyorsa, nesne, `pspCaller` betik altyapısı veya tarayıcıdan hizmet almak için zinciri izleyebilir. (Çağrı zincirinin, kapsayıcı zinciri veya site zinciri olarak da bilinen oluşturma zinciri ile aynı olmadığı unutulmamalıdır. Oluşturma zinciri, gibi başka bir mekanizmaya uygun olabilir `IObjectWithSite` .)|  
|`this` çağrısı|İçinde DISPATCH_METHOD ayarlandığında `wFlags` , "This" değeri için "adlandırılmış parametre" olabilir. DISPID DISPID_THIS olur ve ilk adlandırılmış parametre olmalıdır.|  
  
 `riid`' De kullanılmayan parametre `IDispatch::Invoke` kaldırıldı.  
  
 `puArgArr`İçindeki parametresi `IDispatch::Invoke` kaldırıldı.  
  
 `IDispatch::Invoke`Aşağıdaki örnekler için belgelere bakın:  
  
 "Bağımsız değişken olmadan Yöntem çağırma"  
  
 "Özellikleri alma ve ayarlama"  
  
 "Parametreleri geçirme"  
  
 "Dizinli Özellikler"  
  
 "Invoke sırasında özel durumları yükseltme"  
  
 "Hata döndürülüyor"  
  
## <a name="return-value"></a>Dönüş Değeri  
 Aşağıdaki değerlerden birini döndürür:  
  
|Değer|Anlamı|  
|-|-|  
|`S_OK`|Başarılı.|  
|DISP_E_BADPARAMCOUNT|DISPPARAMS 'e sunulan öğelerin sayısı, yöntem veya özellik tarafından kabul edilen bağımsız değişken sayısından farklı.|  
|DISP_E_BADVARTYPE|İçindeki bağımsız değişkenlerden biri `rgvarg` geçerli bir değişken türü değil.|  
|DISP_E_EXCEPTION|Uygulamanın bir özel durum oluşturması gerekir. Bu durumda, geçirilen yapı `pei` doldurulmalıdır.|  
|DISP_E_MEMBERNOTFOUND|İstenen üye yok veya `InvokeEx` salt okunurdur bir özelliğin değerini ayarlamaya çalıştı.|  
|DISP_E_NONAMEDARGS|Bu uygulamasının `IDispatch` adlandırılmış bağımsız değişkenlerini desteklemez.|  
|DISP_E_OVERFLOW|İçindeki bağımsız değişkenlerden biri `rgvarg` , belirtilen türe zorlanamadı.|  
|DISP_E_PARAMNOTFOUND|DISPID 'ler parametresinden biri yöntemdeki bir parametreye karşılık gelmiyor.|  
|DISP_E_TYPEMISMATCH|Bağımsız değişkenlerden biri veya birkaçı zorlanamadı.|  
|DISP_E_UNKNOWNLCID|Çağrılan üye, LCıD değişkenine göre dize bağımsız değişkenlerini Yorumlar ve LCıD tanınmıyor. Bağımsız değişkenleri yorumlamak için LCıD gerekli değilse, bu hata döndürülmemelidir.|  
|DISP_E_PARAMNOTOPTIONAL|Gerekli bir parametre atlandı.|  
  
## <a name="example"></a>Örnek  
  
```cpp
VARIANT var;  
   BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;  
   DISPPARAMS dispparamsNoArgs = {NULL, NULL, 0, 0};  
  
   // Assign to pdex and bstrName  
   if (SUCCEEDED(pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid)))  
   {  
      pdex->InvokeEx(dispid, LOCALE_USER_DEFAULT,  
         DISPATCH_PROPERTYGET, &dispparamsNoArgs,   
         &var, NULL, NULL);  
   }  
```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IDispatchEx arabirimi](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx:: Getdıspıd](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)