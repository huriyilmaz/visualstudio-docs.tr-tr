---
title: POPLISTFUNC | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- POPDIRLISTFUNC
helpviewer_keywords:
- POPLISTFUNC callback function
ms.assetid: b2199fd5-d707-4628-92dd-e2a01e2f507a
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8c3ae2ce451f076c33ea5613b71c6d262c1d7a0e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64811745"
---
# <a name="poplistfunc"></a>POPLISTFUNC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu geri çağırma, IDE tarafından [SccPopulateList](../extensibility/sccpopulatelist-function.md) için sağlanır ve kaynak denetim eklentisi tarafından, bir dosya veya dizinlerin listesini güncelleştirmek için kullanılır (işleve de sağlanır `SccPopulateList` ).  
  
 Bir Kullanıcı IDE 'de **Get** komutunu SEÇTIĞINDE, IDE kullanıcının alabilir tüm dosyaların bir liste kutusunu görüntüler. Ne yazık ki IDE, kullanıcının alabilir tüm dosyaların tam listesini bilmez; yalnızca eklentide bu liste vardır. Diğer kullanıcılar kaynak kodu denetim projesine dosya eklemiş ise, bu dosyalar listede görünmelidir, ancak IDE bunun hakkında bilgi sahibi değildir. IDE, kullanıcının alabilir olduğunu düşündüğü dosyaların bir listesini oluşturur. Bu listeyi kullanıcıya görüntülemeden önce, [SccPopulateList](../extensibility/sccpopulatelist-function.md) `,` kaynak denetimi eklentisine, listeden dosya ekleme ve silme şansı sağlayan SccPopulateList öğesini çağırır.  
  
## <a name="signature"></a>İmza  
 Kaynak denetimi eklentisi, aşağıdaki prototiple IDE uygulanmış bir işlev çağırarak listeyi değiştirir:  
  
```cpp#  
typedef BOOL (*POPLISTFUNC) (  
   LPVOID pvCallerData,  
   BOOL fAddRemove,  
   LONG nStatus,  
   LPSTR lpFileName  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 pvCallerData  
 `pvCallerData`Çağıran tarafından (IDE) [SccPopulateList](../extensibility/sccpopulatelist-function.md)öğesine geçirilen parametre. Kaynak denetimi eklentisinin bu parametrenin içeriğiyle ilgili hiçbir şey kabul etmesi gerekir.  
  
 fAddRemove  
 `TRUE`, `lpFileName` Dosya listesine eklenmesi gereken bir dosyadır. İse `FALSE` , `lpFileName` dosya listesinden silinmesi gereken bir dosyadır.  
  
 nDurum  
 Durumu `lpFileName` ( `SCC_STATUS` bitlerin birleşimi; Ayrıntılar Için [dosya durum koduna](../extensibility/file-status-code-enumerator.md) bakın).  
  
 lpFileName  
 Listeye eklenecek veya listeden Silinecek dosya adının tam dizin yolu.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`TRUE`|Eklenti bu işlevi çağırmaya devam edebilir.|  
|`FALSE`|IDE tarafında (yetersiz bellek durumu gibi) ilgili bir sorun oluştu. Eklenti işlemi durdurmalıdır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Kaynak denetimi eklentisinin dosya listesine eklemek veya silmek istediği her dosya için, bu işlevi çağırır `lpFileName` . `fAddRemove`Bayrak, listeye eklenecek yeni bir dosyayı veya silinecek eski bir dosyayı gösterir. `nStatus`Parametresi, dosyanın durumunu verir. SCC eklentisinin dosya ekleme ve silme işlemi tamamlandığında, [SccPopulateList](../extensibility/sccpopulatelist-function.md) çağrısından geri döner.  
  
> [!NOTE]
> `SCC_CAP_POPULATELIST`Visual Studio için yetenek biti gereklidir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDE tarafından uygulanan geri çağırma Işlevleri](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [Kaynak denetimi eklentileri](../extensibility/source-control-plug-ins.md)   
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)   
 [Dosya Durumu Kodu](../extensibility/file-status-code-enumerator.md)
