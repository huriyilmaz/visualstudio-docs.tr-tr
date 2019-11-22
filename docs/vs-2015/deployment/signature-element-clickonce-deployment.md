---
title: '&lt;Signature&gt; öğesi (ClickOnce dağıtımı) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <Signature> element [ClickOnce deployment manifest]
ms.assetid: c99b07ad-e8ba-43f2-b0d6-3745e7a7c8b3
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: db696546fdd64199753054b38fa2ac554f6a774f
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295071"
---
# <a name="ltsignaturegt-element-clickonce-deployment"></a>&lt;Signature&gt; öğesi (ClickOnce dağıtımı)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu dağıtım bildirimini dijital olarak imzalamak için gereken bilgileri içerir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
  
      <Signature>   
   XML signature information   
</Signature>  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Bir zarf imzasını kullanarak bir dağıtım bildirimini imzalama isteğe bağlıdır, ancak önerilir. XML dosyalarını imzalama hakkında daha fazla bilgi için, [http://www.w3.org/TR/xmldsig-core/](https://www.w3.org/TR/xmldsig-core/)açıklanan World Wide Web Konsorsiyumu önerisi, "XML imzası sözdizimi ve işleme" başlığına bakın.  
  
 Bildiriminizi imzalamak istiyorsanız tüm dosyalar için karmaların sağlanması gerekir. Karma olmayan dosyaları olan bir bildirim, kullanıcılar karma olmayan dosyaların içeriğini doğrulayamadığından imzalanamıyor.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dağıtımında kullanılan bir dağıtım bildiriminde bir `Signature` öğesi gösterir.  
  
```  
<Signature xmlns="http://www.w3.org/2000/09/xmldsig#">  
  <SignedInfo>  
    <CanonicalizationMethod Algorithm=  
           "http://www.w3.org/TR/2001/REC-xml-c14n-20010315" />  
    <SignatureMethod Algorithm=  
           "http://www.w3.org/2000/09/xmldsig#rsa-sha1" />  
    <Reference URI="">  
      <Transforms>  
        <Transform Algorithm=  
           "http://www.w3.org/2000/09/xmldsig#enveloped-signature" />  
      </Transforms>  
      <DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
      <DigestValue>d2z5AE...</DigestValue>  
    </Reference>  
  </SignedInfo>  
  <SignatureValue>  
4PHj6SaopoLp...  
  </SignatureValue>  
  <KeyInfo>  
    <X509Data>  
      <X509Certificate>  
MIIHnTCCBoWgAwIBAgIKJY9+nwAHAAB...  
      </X509Certificate>  
    </X509Data>  
  </KeyInfo>  
</Signature>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ClickOnce Dağıtım Bildirimi](../deployment/clickonce-deployment-manifest.md)
