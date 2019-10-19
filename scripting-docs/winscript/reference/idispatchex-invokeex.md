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
ms.openlocfilehash: 8a15acb3211c0d3dd19c0d262efb6cbd3327ab9a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575314"
---
# <a name="idispatchexinvokeex"></a>IDispatchEx::InvokeEx
@No__t_0 nesnesi tarafından kullanıma sunulan özelliklere ve yöntemlere erişim sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
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
 Üyeyi tanımlar. Dağıtım tanımlayıcısını almak için `GetDispID` veya `GetNextDispID` kullanır.  
  
 `lcid`  
 Bağımsız değişkenlerin yorumlanacağı yerel ayar bağlamı. @No__t_0, nesnenin bir yerel ayara özgü bağımsız değişkenlerini yorumlamasını sağlamak için `InvokeEx` geçirilir.  
  
 `wFlags`  
 @No__t_0 için geçerli değerler şunlardır:  
  
 DISPATCH_PROPERTYGET &#124; DISPATCH_METHOD &#124; DISPATCH_PROPERTYPUT &#124; DISPATCH_PROPERTYPUTREF &#124; DISPATCH_CONSTRUCT  
  
 @No__t_0 çağrısının bağlamını açıklayan bayraklar:  
  
|Değer|Açıklama|  
|-----------|-------------|  
|DISPATCH_METHOD|Üye bir yöntem olarak çağrılır. Bir özellik aynı ada sahipse, hem this hem de DISPATCH_PROPERTYGET bayrağı ayarlanabilir (`IDispatch` tarafından tanımlanır).|  
|DISPATCH_PROPERTYGET|Üye bir özellik veya veri üyesi olarak alınır (`IDispatch` tarafından tanımlanır).|  
|DISPATCH_PROPERTYPUT|Üye bir özellik veya veri üyesi olarak değiştirildi (`IDispatch` tarafından tanımlanır).|  
|DISPATCH_PROPERTYPUTREF|Üye, bir değer ataması yerine bir başvuru ataması tarafından değiştirilir. Bu bayrak yalnızca özellik bir nesnenin başvurusunu kabul ettiğinde geçerlidir (`IDispatch` tarafından tanımlanır).|  
|DISPATCH_CONSTRUCT|Üye bir Oluşturucu olarak kullanılıyor. (Bu, `IDispatchEx` tarafından tanımlanan yeni bir değerdir). @No__t_0 için geçerli değerler şunlardır:<br /><br /> DISPATCH_PROPERTYGET DISPATCH_METHOD DISPATCH_PROPERTYPUT DISPATCH_PROPERTYPUTREF DISPATCH_CONSTRUCT|  
  
 `pdp`  
 Bir dizi bağımsız değişkeni içeren bir yapıya yönelik işaretçi, adlandırılmış bağımsız değişkenler için bir dizi bağımsız değişken DISPID değeri ve dizilerdeki öğelerin sayısına ilişkin sayımlar. DISPPARAMS yapısının tam açıklaması için `IDispatch` belgelerine bakın.  
  
 `pVarRes`  
 Çağıran hiçbir sonuç beklemdiğinde sonucun depolanacağı konuma veya null değere işaretçi. DISPATCH_PROPERTYPUT veya DISPATCH_PROPERTYPUTREF belirtilmişse bu bağımsız değişken yoksayılır.  
  
 `pei`  
 Özel durum bilgisi içeren bir yapıya yönelik işaretçi. @No__t_0 döndürülürse bu yapı doldurulmalıdır. Null olabilir. @No__t_1 yapısının tam açıklaması için `IDispatch` belgelerine bakın.  
  
 `pspCaller`  
 Çağıran tarafından sağlanan ve nesnenin çağırandan hizmet almasına izin veren bir hizmet sağlayıcı nesnesine yönelik işaretçi. Null olabilir.  
  
 `IDispatchEx::InvokeEx`, `IDispatch::Invoke` aynı özelliklerin tümünü sağlar ve birkaç uzantı ekler:  
  
|||  
|-|-|  
|DISPATCH_CONSTRUCT|Öğenin bir Oluşturucu olarak kullanıldığını belirtir.|  
|`pspCaller`|@No__t_0, çağıran tarafından sunulan hizmetlere nesne erişimine izin verir. Belirli hizmetler, arayanın kendisi tarafından işlenebilir veya çağrı zincirinin daha fazla arayanlara daha fazla çağrı yapılabilir. Örneğin, bir tarayıcı içindeki bir betik altyapısı bir dış nesneye `InvokeEx` çağrısı yapıyorsa, nesne, betik altyapısı veya tarayıcıdan hizmet almak için `pspCaller` zincirini izleyebilir. (Çağrı zincirinin, kapsayıcı zinciri veya site zinciri olarak da bilinen oluşturma zinciri ile aynı olmadığı unutulmamalıdır. Oluşturma zinciri, `IObjectWithSite` gibi başka bir mekanizmaya uygun olabilir.)|  
|`this` işaretçisi|@No__t_0 DISPATCH_METHOD ayarlandığında, "This" değeri için "adlandırılmış parametre" olabilir. DISPID DISPID_THIS olur ve ilk adlandırılmış parametre olmalıdır.|  
  
 @No__t_1 kullanılmayan `riid` parametresi kaldırıldı.  
  
 @No__t_1 `puArgArr` parametresi kaldırıldı.  
  
 Aşağıdaki örnekler için `IDispatch::Invoke` belgelerine bakın:  
  
 "Bağımsız değişken olmadan Yöntem çağırma"  
  
 "Özellikleri alma ve ayarlama"  
  
 "Parametreleri geçirme"  
  
 "Dizinli Özellikler"  
  
 "Invoke sırasında özel durumları yükseltme"  
  
 "Hata döndürülüyor"  
  
## <a name="return-value"></a>Dönüş Değeri  
 Aşağıdaki değerlerden birini döndürür:  
  
|||  
|-|-|  
|`S_OK`|Başarılı.|  
|DISP_E_BADPARAMCOUNT|DISPPARAMS 'e sunulan öğelerin sayısı, yöntem veya özellik tarafından kabul edilen bağımsız değişken sayısından farklı.|  
|DISP_E_BADVARTYPE|@No__t_0 bağımsız değişkenlerden biri geçerli bir değişken türü değil.|  
|DISP_E_EXCEPTION|Uygulamanın bir özel durum oluşturması gerekir. Bu durumda, `pei` geçirilen yapı doldurulmalıdır.|  
|DISP_E_MEMBERNOTFOUND|İstenen üye yok veya `InvokeEx` çağrısı salt okunurdur bir özelliğin değerini ayarlamaya çalıştı.|  
|DISP_E_NONAMEDARGS|Bu `IDispatch` uygulanması adlandırılmış bağımsız değişkenleri desteklemez.|  
|DISP_E_OVERFLOW|@No__t_0 bağımsız değişkenlerden biri, belirtilen türe zorlanamadı.|  
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