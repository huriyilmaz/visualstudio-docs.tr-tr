---
title: Valtlanguagepack öğesi (VSıX dil paketi şeması) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
ms.assetid: 767f5c22-8b87-49ca-92aa-a7a3f026469f
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e2e1df362fddeab5be98ff90460a8a1a7d4b7876
ms.sourcegitcommit: 26178b116cbf7353fee6ca989b8d872114f7b405
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2020
ms.locfileid: "89284361"
---
# <a name="vsixlanguagepack-element-vsix-language-pack-schema"></a>Valtlanguagepack öğesi (VSıX dil paketi şeması)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gereklidir. VSıX dil paketi için kök öğesi sağlar. VSıX dil paketi bir VSıX paketi için yerelleştirilmiş yükleme bilgilerini sağlar.  
  
## <a name="syntax"></a>Syntax  
  
```  
<VSIXLanguagePack>  
  <LocalizedName>...</LocalizedName>  
  <LocalizedDescription>...</LocalizedDescription>  
  <MoreInfoURL>...</MoreInfoURL>  
  <License>...</License>  
</VSIXLanguagePack>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`xmlns`|VSıX dil paketi şemasının tanımlandığı XML ad alanı.|  
  
## <a name="xmlns-attribute"></a>xmlns özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`http://schemas.microsoft.com/developer/vsx-schema-lp/2010`|Gereklidir. Dil paketleri şemasını tanımlayan dosyanın konumu.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[LocalizedName Öğesi](../extensibility/localizedname-element-vsix-language-pack-schema.md)|Gereklidir. Yüklenecek uzantının yerelleştirilmiş adı.|  
|[LocalizedDescription Öğesi](../extensibility/localizeddescription-element-vsix-language-pack-schema.md)|Gereklidir. Yüklenecek uzantının yerelleştirilmiş açıklaması.|  
|[MoreInfoURL Öğesi](../extensibility/moreinfourl-element-vsix-language-pack-schema.md)|İsteğe bağlı. Uzantı hakkındaki yerelleştirilmiş bilgilere bir bağlantı.|  
|[License Öğesi](../extensibility/license-element-vsix-language-pack-schema.md)|İsteğe bağlı. Uzantı için lisans dosyasının yerelleştirilmiş bir sürümünün yolu.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|Hiçbiri||  
  
## <a name="element-information"></a>Öğe Bilgisi  
  
|                 |                                                           |
|-----------------|-----------------------------------------------------------|
|    Ad Alanı    | `http://schemas.microsoft.com/developer/vsx-schema-lp/2010` |
|   Şema adı   |                 VSıX dil paketi şeması                 |
| Doğrulama dosyası |                Valtlanguagepackschema. xsd                 |
|  Boş olabilir   |                            Hayır                             |
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VSX dil paketi şema başvurusu](../extensibility/vsx-language-pack-schema-reference.md) [Yerelleştirme VSIX paketleri](../extensibility/localizing-vsix-packages.md) [VSIX uzantı şeması 1,0 başvurusu](/previous-versions/dd393700(v=vs.110))
