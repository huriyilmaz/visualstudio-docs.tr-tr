---
title: 'Iactivescriptauthor:: Addnamedidıtem | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.AddNamedItem
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::AddNamedItem
ms.assetid: 951003b6-1c4a-4086-b7ce-2f128e007280
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f0d2f08a49fdc768e87152bf486ce48687c79e68
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577251"
---
# <a name="iactivescriptauthoraddnameditem"></a>IActiveScriptAuthor::AddNamedItem
Kök düzeyindeki bir öğenin adını betik yazma altyapısının ad alanına ekler. *Kök düzeyindeki öğe* , Özellikler ve Yöntemler içerebilen ve bir olay kaynağı içerebilen bir nesnedir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT AddNamedItem(  
   LPCOLESTR          pszName,  
   DWORD              dwFlags,  
   IDispatch          *pdisp  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pszName`  
 'ndaki Betikten görüntülenen öğenin adı. Ad benzersiz ve persistable olmalıdır.  
  
 `dwFlags`  
 'ndaki Adlandırılmış öğeyle ilişkili bayraklar. Aşağıdaki değerlerin bir birleşimi olabilir:  
  
|Sabit|Değer|Açıklama|  
|--------------|-----------|-----------------|  
|SCRIPTITEM_ISVISIBLE|0x00000002|Öğenin adının betiğin ad alanında kullanılabilir olduğunu gösterir. Bu, öğenin özelliklerine, yöntemlerine ve olaylarına erişim sağlar.<br /><br /> Kurala göre, öğenin özellikleri öğenin alt üyelerini içerir. Bu nedenle, tüm alt nesne özelliklerine ve yöntemlerine (ve bunların alt üyelerine yinelemeli olarak) erişilebilir.|  
|SCRIPTITEM_ISSOURCE|0x00000004|Komut dosyasının betik olay işleyicilerine sahip olduğu öğe kaynağının olaylarını gösterir.|  
|SCRIPTITEM_GLOBALMEMBERS|0x00000008|Öğenin, komut dosyasıyla ilişkili genel özellikler ve yöntemlerin bir koleksiyonu olduğunu gösterir. Üyeleri genel değişkenler ve yöntemler olarak yazılır.|  
|SCRIPTITEM_ISPERSISTENT|0x00000040|Betik yazma altyapısı kaydedilirse öğenin kaydedilmesi gerektiğini belirtir.|  
|SCRIPTITEM_CODEONLY|0x00000200|Adlandırılmış öğenin yalnızca bir kod nesnesini temsil ettiğini ve yazmak için bir üyeye sahip olmadığını gösterir.|  
|SCRIPTITEM_NOCODE|0x00000400|Adlandırılmış öğenin yalnızca bir ad eklendiğini ve yazamayacağını belirtir.|  
  
 `pdisp`  
 'ndaki Yöntemleri, özellikleri veya olay kaynağını toplamak için kullanılan `NamedItem` nesnesinin `IDispatch`.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Iactivescriptauthor arabirimi](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)