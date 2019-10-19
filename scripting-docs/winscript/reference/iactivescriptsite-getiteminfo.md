---
title: 'IActiveScriptSite:: GetItemInfo | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.GetItemInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_GetItemInfo
ms.assetid: f859ed3b-02c1-4924-99f8-5f5bf1bf8405
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3c0458f42466a264c30a440b1b14a028a2457f12
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570919"
---
# <a name="iactivescriptsitegetiteminfo"></a>IActiveScriptSite::GetItemInfo
Betik altyapısının [IActiveScript:: Addnamedidıtem](../../winscript/reference/iactivescript-addnameditem.md) yöntemiyle eklenen bir öğe hakkında bilgi almasına izin verir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetItemInfo(  
    LPCOLESTR pstrName,     // address of item name  
    DWORD dwReturnMask,     // bit mask for information retrieval  
    IUnknown **ppunkItem,   // address of pointer to item's IUnknown  
    ITypeInfo **ppTypeInfo  // address of pointer to item's ITypeInfo  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pstrName`  
 'ndaki [IActiveScript:: Addnamedidıtem](../../winscript/reference/iactivescript-addnameditem.md) yönteminde belirtilen şekilde öğesiyle ilişkili ad.  
  
 `dwReturnMask`  
 'ndaki Öğe hakkında hangi bilgilerin döndürüleceğini belirten bir bit maskesi. Betik altyapısı, bazı dönüş parametrelerinden (örneğin, `ITypeInfo`) yüklenmesi veya oluşturulması uzun sürebileceğinden, mümkün olan en düşük miktarda bilgiyi istemelidir. Aşağıdaki değerlerin bir birleşimi olabilir:  
  
|Değer|Açıklama|  
|-----------|-------------|  
|SCRIPTINFO_IUNKNOWN|Bu öğe için `IUnknown` arabirimini döndürür.|  
|SCRIPTINFO_ITYPEINFO|Bu öğe için `ITypeInfo` arabirimini döndürür.|  
  
 `ppunkItem`  
 dışı Verilen öğeyle ilişkili `IUnknown` arabirimine yönelik bir işaretçi alan bir değişkenin adresi. Betik altyapısı, öğe için `IDispatch` arabirimini almak üzere `IUnknown::QueryInterface` yöntemini kullanabilir. Bu parametre, `dwReturnMask` SCRIPTINFO_IUNKNOWN değerini içermiyorsa NULL alır. Ayrıca, öğe adıyla ilişkili bir nesne yoksa NULL alır; Bu mekanizma, [IActiveScript:: Addnamedidıtem](../../winscript/reference/iactivescript-addnameditem.md) YÖNTEMINDE ayarlanan SCRIPTITEM_CODEONLY bayrağıyla adlandırılmış öğe eklendiğinde basit bir sınıf oluşturmak için kullanılır.  
  
 `ppTypeInfo`  
 dışı Öğeyle ilişkili `ITypeInfo` arabirimine yönelik bir işaretçi alan bir değişkenin adresi. Bu parametre, `dwReturnMask` SCRIPTINFO_ITYPEINFO değerini içermiyorsa veya bu öğe için tür bilgisi yoksa NULL alır. Tür bilgisi yoksa, nesne olayları kaynak olarak içeremez ve ad bağlamasının `IDispatch::GetIDsOfNames` yöntemiyle birlikte gerçekleştirilmelidir. @No__t_0 arabirimin, öğe birden çok arabirimi ve olay arabirimlerini destekleyebileceğinden öğenin coclass 'ı (TKIND_COCLASS) desteklediğini unutmayın. Öğe `IProvideMultipleTypeInfo` arabirimini destekliyorsa, alınan `ITypeInfo` arabirimi `IProvideMultipleTypeInfo::GetInfoOfIndex` yöntemi kullanılarak elde edilen Dizin sıfır `ITypeInfo` ile aynıdır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Aşağıdaki değerlerden birini döndürür:  
  
|Dönüş Değeri|Açıklama|  
|------------------|-------------|  
|`S_OK`|Başarılı.|  
|`E_INVALIDARG`|Bağımsız değişken geçersizdi.|  
|`E_POINTER`|Geçersiz bir işaretçi belirtildi.|  
|`TYPE_E_ELEMENTNOTFOUND`|Belirtilen ada sahip bir öğe bulunamadı.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem yalnızca `dwReturnMask` parametresi tarafından belirtilen bilgileri alır; Bu, performansı geliştirir. Örneğin, bir `ITypeInfo` arabirimi bir öğe için gerekmiyorsa, `dwReturnMask` yalnızca belirtilmemiş.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)