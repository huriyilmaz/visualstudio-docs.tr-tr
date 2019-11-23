---
title: 'Iactivescriptproperty:: SetProperty | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProperty.SetProperty
apilocation:
- scrobj.dll
helpviewer_keywords:
- SetProperty method, IActiveScriptProperty interface
ms.assetid: 0ba429c5-04a3-4505-bc5f-69c505dfca91
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0f8307a82f181be20205c7bfcc47e881b0fa1e90
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571312"
---
# <a name="iactivescriptpropertysetproperty"></a>IActiveScriptProperty::SetProperty
Parametresi tarafından belirtilen özelliği ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT SetProperty(  
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
 Ayarlanacak özellik değeri.  
  
 `pvarIndex`  
 Kullanılmadı.  
  
 `pvarValue`  
 Özelliğin değeri.  
  
 `dwProperty` için izin verilen değerler aşağıdaki tabloda açıklanmıştır.  
  
|Sabit|Değer|Anlamı|  
|--------------|-----------|-------------|  
|SCRIPTPROP_INTEGERMODE|0x00003000|Betik altyapısını kayan nokta modu yerine tamsayı modunda bölmeye zorlar. Varsayılan değer `False` şeklindedir.|  
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
 Tamsayı bölümünü etkinleştirmek veya devre dışı bırakmak için `SetProperty` çağırın ve bir `Boolean` `Object`dönüştürün. Varsayılan olarak, özellik değeri `False`. `True`olarak ayarlarsanız, bölüm işlemleri yalnızca tamsayılar döndürür.  
  
 Özel dize karşılaştırmayı etkinleştirmek veya devre dışı bırakmak için `SetProperty` çağırın ve bir `Object` değeri geçirin. Geçirdiğiniz nesnenin Interface [ıactivescriptstringcompare arabirimini](../../winscript/reference/iactivescriptstringcompare-interface.md)uygulaması gerekir. [Iactivescriptstringcompare Interface](../../winscript/reference/iactivescriptstringcompare-interface.md) arabiriminin [StrComp](../../winscript/reference/iactivescriptstringcompare-strcomp.md) yöntemi, bir dize karşılaştırma işlevi her yürütüldüğünde çağrılır.  
  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] betik altyapısı başlatıldığında desteklenecek dil özellikleri kümesini seçmek için, `SetProperty` çağırın ve SCRIPTPROP_INVOKEVERSIONING için etkinleştirilecek dil özelliği kümesine karşılık gelen bir değer geçirin. Bu özellik 1 (SCRIPTLANGUAGEVERSION_5_7) olarak ayarlandıysa, kullanılabilir dil özellikleri [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] betik altyapısının sürüm 5,7 ' de gösterilenler ile aynıdır. 2 (SCRIPTLANGUAGEVERSION_5_8) olarak ayarlandıysa, sürüm 5,8 ' de eklenen yeni özelliklerin yanı sıra, kullanılabilir dil özellikleri 5,7 sürümünde görüntülenenler olur. Varsayılan olarak, bu özellik 0 (SCRIPTLANGUAGEVERSION_DEFAULT) olarak ayarlanır ve ana bilgisayar farklı bir varsayılan davranışı desteklemediği takdirde sürüm 5,7 ' de görünen dil özelliği kümesine eşdeğerdir. Örneğin Internet Explorer 8, Internet Explorer 8 için varsayılan belge modu "Internet Explorer 8 Standartları" modundayken varsayılan olarak sürüm 5,8 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] komut dosyası altyapısı tarafından desteklenen [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] dil özelliklerine sahiptir. Internet Explorer 8 belge modunu Internet Explorer 7 standartlarına veya olağandışı moda geçirmek, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] betik altyapısını yalnızca sürüm 5,7 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] komut dosyası altyapısında bulunan dil özelliği kümesini destekleyecek şekilde sıfırlar.  
  
> [!NOTE]
> SCRIPTPROP_INVOKEVERSIONING, yalnızca [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] betik altyapısı başlatılırken ayarlanmalıdır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, komut dosyası altyapısının tamsayı bölümünü kullanma ve karşılaştırma işlevinin aşırı yüklenmesine nasıl izin vereceğini gösterir.  
  
```c#  
BMLScriptEngine bmlScriptEngine = new BMLScriptEngine();  
IActiveScriptProperty scriptProperties = bmlScriptEngine as   
    IActiveScriptProperty;  
  
// Force the scripting engine to use integer division.  
Boolean enableIntegerDivision = true;  
Object vtIntegerDivInstance = (Object)enableIntegerDivision;  
                scriptProperties.SetProperty(SCRIPTPROP_INTEGERDIVISION,   
    System.IntPtr.Zero, ref vtIntegerDivInstance);  
  
// Allow overloading of the compare function.  
BMLScriptStringCompare bmlScriptStringCompareInstance = new   
    BMLScriptStringCompare();  
Object vtStrCmpInstance = (Object)bmlScriptStringCompareInstance;  
scriptProperties.SetProperty(SCRIPTPROP_STRCOMPINST,   
    System.IntPtr.Zero, ref vtStrCmpInstance);  
```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Belge uyumluluğunu tanımlama](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/compatibility/cc288325(v=vs.85))   
 [Iactivescriptproperty](../../winscript/reference/iactivescriptproperty.md)   
 [Sürüm Bilgileri](../../javascript/reference/javascript-version-information.md)