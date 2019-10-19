---
title: 'Iprovideexpressionbağlamları:: Trmexpressionbağlamları | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IProvideExpressionContexts.EnumExpressionContexts
apilocation:
- jscript.dll
helpviewer_keywords:
- IProvideExpressionContexts::EnumExpressionContexts
ms.assetid: ec5f0065-00df-41e6-b480-4c04ba464872
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f161c1591267af1398d5c04d00623381cfae2ad4
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572393"
---
# <a name="iprovideexpressioncontextsenumexpressioncontexts"></a>IProvideExpressionContexts::EnumExpressionContexts
Bu bileşen tarafından bilinen ifade bağlamlarının bir listeleyici döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT EnumExpressionContexts(  
   IEnumDebugExpressionContexts**  ppedec  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppedec`  
 dışı Bu bileşen tarafından bilinen ifade bağlamlarının numaralandırıcısı.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 İşlem hata ayıklama Yöneticisi, belirli bir iş parçacığı ile ilişkili tüm genel ifade bağlamlarını bulmak için bu yöntemi kullanır.  
  
> [!NOTE]
> Bu yöntem, ilgilendiğiniz iş parçacığı içinden çağrılır. Bu, geçerli iş parçacığını tanımlamak ve uygun bir Numaralandırıcı döndürmek için uygulayıcıya sahiptir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IProvideExpressionContexts Arabirimi](../../winscript/reference/iprovideexpressioncontexts-interface.md)