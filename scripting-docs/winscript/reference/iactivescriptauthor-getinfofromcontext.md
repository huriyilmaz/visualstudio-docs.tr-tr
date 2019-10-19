---
title: 'Iactivescriptauthor:: GetInfoFromContext | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetInfoFromContext
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetInfoFromContext
ms.assetid: 9891b095-6eb5-4473-87c0-c2e5cd2afc1a
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 457b2ad1bda3226caf3604e3ccd6b976f01bca83
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576208"
---
# <a name="iactivescriptauthorgetinfofromcontext"></a>IActiveScriptAuthor::GetInfoFromContext
Kod bloğundaki belirli bir karakter için tür bilgilerini ve yer işareti konumlarını döndürür. Bu, üye IntelliSense, genel listeler ve parametre ipuçları hakkında bilgiler sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetInfoFromContext(  
   LPCOLESTR  pszCode,  
   ULONG      cchCode,  
   ULONG      ichCurrentPosition,  
   DWORD      dwListTypesRequested,  
   DWORD      *pdwListTypesProvided,  
   ULONG      *pichListAnchorPosition,  
   ULONG      *pichFuncAnchorPosition,  
   MEMBERID   *pmemid,  
   LONG       *piCurrentParameter,  
   IUnknown   **ppunk  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pszCode`  
 'ndaki Bilgi sonuçlarını oluşturmak için kullanılan kod bloğu dizesinin adresi.  
  
 `cchCode`  
 'ndaki Kod bloğunun uzunluğu.  
  
 `ichCurrentPosition`  
 'ndaki Bloğunun başlangıcına göre karakterin konumu.  
  
 `dwListTypesRequested`  
 'ndaki İstenen liste türleri. Aşağıdaki değerlerin bir birleşimi olabilir:  
  
|Sabit|Değer|Açıklama|  
|--------------|-----------|-----------------|  
|SCRIPT_CMPL_NOLIST|0x0000|Liste yok.|  
|SCRIPT_CMPL_MEMBERLIST|0x0001|Üye listesi.|  
|SCRIPT_CMPL_ENUMLIST|0x0002|Numaralandırma listesi.|  
|SCRIPT_CMPL_PARAMLIST|0x0004|Yöntem parametre listesini çağırın.|  
|SCRIPT_CMPL_GLOBALLIST|0x0008|Genel liste.|  
  
 SCRIPT_CMPL_GLOBALLIST türü, diğer tamamlama öğeleriyle OR işleci kullanılarak birleştirilebilecek bir varsayılan tamamlama öğesi olarak değerlendirilir. Betik yazma altyapısı öncelikle diğer tamamlanma listesi öğeleri için tür bilgilerini doldurmayı dener. Bu başarısız olursa, motor SCRIPT_CMPL_GLOBALLIST için de doldurulur.  
  
 `pdwListTypesProvided`  
 dışı Belirtilen liste türü.  
  
 `pichListAnchorPosition`  
 dışı Geçerli konumu içeren bağlamın başlangıç dizini. Başlangıç dizini bloğunun başlangıcına göre belirlenir.  
  
 Bu yalnızca `dwListTypesRequested` SCRIPT_CMPL_MEMBERLIST, SCRIPT_CMPL_ENUMLIST veya SCRIPT_CMPL_GLOBALLIST içerdiğinde doldurulur. İstenen diğer liste türleri için sonuç tanımsızdır.  
  
 `pichFuncAnchorPosition`  
 dışı Geçerli konumu içeren işlev çağrısının başlangıç dizini. Başlangıç dizini bloğunun başlangıcına göre belirlenir.  
  
 Bu, yalnızca geçerli konumu içeren bağlam bir işlev çağrısı olduğunda ve `dwListTypesRequested` SCRIPT_CMPL_PARAMLIST içerdiğinde doldurulur. Aksi takdirde, sonuç tanımsızdır.  
  
 `pmemid`  
 dışı @No__t_0 Out parametresindeki bir tür tarafından tanımlanan şekilde işlevin ÜYEKODU 'ı.  
  
 Bu yalnızca `dwListTypesRequested` SCRIPT_CMPL_PARAMLIST içerdiğinde doldurulur.  
  
 `piCurrentParameter`  
 dışı Geçerli konumu içeren parametrenin dizini. Geçerli konum işlev adı üzerinde ise-1 döndürülür.  
  
 @No__t_0 değeri yalnızca `dwListTypesRequested` SCRIPT_CMPL_PARAMLIST içerdiğinde doldurulur.  
  
 `ppunk`  
 @No__t_0 nesne biçiminde belirtilen tür bilgileri.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IProvideMultipleClassInfo arabirimi](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.ole.interop.iprovidemultipleclassinfo)    
 [IActiveScriptAuthor Arabirimi](../../winscript/reference/iactivescriptauthor-interface.md)