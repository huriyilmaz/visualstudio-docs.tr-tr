---
title: 'IActiveScript:: Addnamedidıtem | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.AddNamedItem
apilocation:
- scrobj.dll
helpviewer_keywords:
- AddNamedItem method, IActiveScript interface
ms.assetid: a7c6317d-948f-4bb3-b169-1bbe5b7c7cc5
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a343e38b944ca36da221da39832046c19b332230
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575822"
---
# <a name="iactivescriptaddnameditem"></a>IActiveScript::AddNamedItem
Kök düzeyindeki bir öğenin adını betik altyapısının ad alanına ekler. Kök düzeyindeki bir öğe, özellikleri ve yöntemleri, bir olay kaynağını veya üçünü içeren bir nesnedir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT AddNamedItem(  
    LPCOLESTR pstrName,  // address of item name  
    DWORD dwFlags          // item flags  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pstrName`  
 'ndaki Betikten görüntülenen öğenin adını içeren bir arabelleğin adresi. Ad benzersiz ve persistable olmalıdır.  
  
 `dwFlags`  
 'ndaki Bir öğeyle ilişkili bayraklar. Şu değerlerin bir birleşimi olabilir:  
  
|Değer|Açıklama|  
|-----------|-------------|  
|SCRIPTITEM_CODEONLY|Adlandırılmış öğenin yalnızca bir kod nesnesini temsil ettiğini ve konağın bu yalnızca kod nesnesiyle ilişkilendirilebilen `IUnknown` olmadığını gösterir. Konağın bu nesne için yalnızca bir adı vardır. Gibi nesne yönelimli dillerde C++, bu bayrak bir sınıf oluşturur. Tüm diller bu bayrağı desteklemez.|  
|SCRIPTITEM_GLOBALMEMBERS|Öğenin, komut dosyasıyla ilişkili genel özellikler ve yöntemlerin bir koleksiyonu olduğunu gösterir. Normalde, bir komut dosyası motoru nesne adını ( [IActiveScriptSite:: GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md) yöntemi için bir tanımlama bilgisi olarak kullanmak veya açık kapsamları çözümlemek için) ve üyelerini genel değişkenler ve yöntemler olarak kullanıma sunacaktır. Bu, konağın bir kitaplığı (çalışma zamanı işlevleri vb.), komut dosyası tarafından kullanılabilmesini sağlar. Ad çakışmaları ile başa çıkmak için komut dosyası motoruna (örneğin, iki SCRIPTITEM_GLOBALMEMBERS öğe aynı ada sahip olduğunda), ancak bu durum nedeniyle bir hata döndürülmemelidir.|  
|SCRIPTITEM_ISPERSISTENT|Betik altyapısı kaydedilirse öğenin kaydedilmesi gerektiğini belirtir. Benzer şekilde, bu bayrak ayarlandığında, başlatılan duruma geri geçiş, öğenin adını ve tür bilgilerini tutabilmelidir (komut dosyası altyapısı, ancak gerçek nesnedeki arabirimlerin tüm işaretçilerini serbest bırakmalıdır).|  
|SCRIPTITEM_ISSOURCE|Öğenin, komut dosyasının havuza alabileceğiniz olayları belirtir. Alt nesneler (kendi nesnelerinde bulunan nesnenin özellikleri) de komut dosyasına olay kaynağı verebilir. Bu özyinelemeli değildir, ancak örneğin bir kapsayıcı ve tüm üye denetimlerini oluşturma gibi yaygın durum için kullanışlı bir mekanizma sağlar.|  
|SCRIPTITEM_ISVISIBLE|Öğenin adının betiğin ad alanında kullanılabildiğini, öğenin özelliklerine, yöntemlerine ve olaylarına izin vermeyi gösterir. Kurala göre öğenin özellikleri öğenin alt öğelerini içerir; Bu nedenle, tüm alt nesne özelliklerine ve yöntemlerine (ve alt öğelerine yinelemeli olarak) erişilebilecektir.|  
|SCRIPTITEM_NOCODE|Öğenin yalnızca betiğin ad alanına eklenen bir ad olduğunu ve kodun ilişkilendirilmesi gereken bir öğe olarak değerlendirilmeyeceğini gösterir. Örneğin, bu bayrak belirtilmeden VBScript, adlandırılmış öğe için ayrı bir modül oluşturur ve C++ adlandırılmış öğe için ayrı bir sarmalayıcı sınıfı oluşturabilir.|  
  
## <a name="return-value"></a>Dönüş Değeri  
 Aşağıdaki değerlerden birini döndürür:  
  
|Dönüş Değeri|Açıklama|  
|------------------|-------------|  
|`S_OK`|Başarılı.|  
|`E_INVALIDARG`|Bağımsız değişken geçersizdi.|  
|`E_POINTER`|Geçersiz bir işaretçi belirtildi.|  
|`E_UNEXPECTED`|Çağrı beklenmiyordu (örneğin, komut dosyası altyapısı henüz yüklenmemiş veya başlatılmamış).|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IActiveScript](../../winscript/reference/iactivescript.md)