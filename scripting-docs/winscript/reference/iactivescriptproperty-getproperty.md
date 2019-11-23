---
title: 'Iactivescriptproperty:: GetProperty | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProperty.GetProperty
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetProperty method, IActiveScriptProperty interface
ms.assetid: a43383db-b148-4d76-83bd-4f0e899b7cb1
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f1eeec6472a067d18a8b8962cfac70c25c0ff971
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571419"
---
# <a name="iactivescriptpropertygetproperty"></a>IActiveScriptProperty::GetProperty
Parametresi tarafından belirtilen özelliği alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetProperty(  
// The property value:  
    uint dwProperty,    
// Not used:  
    IntPtr pvarIndex,    
// The value of the property:   
    out object pvarValue,    
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `dwProperty`  
 Alınacak Özellik değeri.  
  
 `pvarIndex`  
 Kullanılmadı.  
  
 `pvarValue`  
 Özelliğin değeri.  
  
 `dwProperty` için izin verilen değerler aşağıdaki tabloda açıklanmıştır.  
  
|Sabit|Değer|Anlamı|  
|--------------|-----------|-------------|  
|SCRIPTPROP_INTEGERMODE|0x00003000|Betik altyapısını kayan nokta modu yerine tamsayı modunda bölmeye zorlar.|  
|SCRIPTPROP_STRINGCOMPAREINSTANCE|0x00003001|Betik altyapısının dize karşılaştırma işlevinin değiştirilmesine izin verir.|  
|SCRIPTPROP_ABBREVIATE_GLOBALNAME_RESOLUTION|0x70000002|Betik motoruna genel nesneye katkıda bulunmak için başka bir betik altyapısı bulunmadığını bildirir.|  
|SCRIPTPROP_INVOKEVERSIONING|0x00004000|[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] betik altyapısını desteklenecek bir dil özellikleri kümesi seçmesini zorlar. [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Scripting Engine tarafından desteklenen varsayılan dil özellikleri kümesi, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] betik altyapısının 5,7 sürümünde görünen dil özelliği kümesiyle eşdeğerdir.|  
  
## <a name="return-value"></a>Dönüş Değeri  
 Aşağıdaki değerlerden birini döndürür:  
  
|Dönüş Değeri|Anlamı|  
|------------------|-------------|  
|`S_OK`|Başarılı.|  
|`E_INVALIDARG`|Bağımsız değişken geçerli değil.|  
|`E_UNEXPECTED`|Çağrı beklenmiyordu (örneğin, komut dosyası altyapısı henüz yüklenmemiş veya başlatılmamış).|  
  
## <a name="remarks"></a>Açıklamalar  
 Ana bilgisayar, genel nesneye katkıda bulunmak için başka bir betik altyapısı bulunmadığını belirten bir betik altyapısını bilgilendirmek için SCRIPTPROP_ABBREVIATE_GLOBALNAME_RESOLUTION özelliğini kullanabilir. Örneğin, Internet Explorer [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] altyapısını, işlenen sayfanın yalnızca [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] betikler içerdiğini bildirebilir. Bu nedenle, yalnızca [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] motoru genel nesne penceresine yeni özellikler ekleyebilir ve aynı yapmak için bir Visual Basic Scripting Edition (VBScript) altyapısı yoktur. Motor bu bayrağı yok sayabilir veya genel nesneye eklenen yeni üyelerin yönetimini iyileştirmek için kullanabilir.  
  
 Konak, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] betik altyapısı başlatıldığında desteklenecek dil özellikleri kümesini seçmek için SCRIPTPROP_INVOKEVERSIONING özelliğini kullanabilir. Bu özellik 1 (SCRIPTLANGUAGEVERSION_5_7) olarak ayarlandıysa, kullanılabilir dil özellikleri [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] betik altyapısının sürüm 5,7 ' de gösterilenler ile aynıdır. 2 (SCRIPTLANGUAGEVERSION_5_8) olarak ayarlandıysa, sürüm 5,8 ' de eklenen özelliklere ek olarak, sürüm 5,7 ' de görünen özellikler de mevcuttur. Varsayılan olarak, bu özellik 0 (SCRIPTLANGUAGEVERSION_DEFAULT) olarak ayarlanır ve ana bilgisayar farklı bir varsayılan davranışı desteklemediği takdirde sürüm 5,7 ' de görünen dil özelliği kümesine eşdeğerdir. Örneğin, Internet Explorer 8, Internet Explorer 8 için belge modu "Internet Explorer 8 Standartları" modundayken varsayılan olarak sürüm 5,8 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] komut dosyası altyapısı tarafından desteklenen [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] dil özelliklerine sahiptir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Belge uyumluluğunu tanımlama](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/compatibility/cc288325(v=vs.85))   
 [Iactivescriptproperty](../../winscript/reference/iactivescriptproperty.md)   
 [Sürüm Bilgileri](../../javascript/reference/javascript-version-information.md)