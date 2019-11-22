---
title: 'Nasıl yapılır: bir uzantıyı El Ile paketleme (VSıX dağıtımı) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: d25990e0-e782-4a79-9d9a-1caf3c56c6a2
caps.latest.revision: 10
manager: jillfra
ms.openlocfilehash: a615aea75ec00e49ee4d2837b8b4e2b1d20d3306
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74293625"
---
# <a name="how-to-manually-package-an-extension-vsix-deployment"></a>Nasıl yapılır: bir uzantıyı El Ile paketleme (VSıX dağıtımı)
Dağıtım için bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] uzantısını kaydırmak üzere bir VSıX paketi oluşturabilirsiniz. Paketi oluşturmak için üç yol vardır:  
  
- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] SDK 'sında bulunan genişletilebilirlik şablonlarından birini kullanarak bir VSıX paketi projesi oluşturun. Bu çoğu senaryo için en kolay seçenektir.  
  
- Uzantı projenizin çıkışını boş bir [VSIX projesinde](../extensibility/vsix-project-template.md)sarın. Bu seçeneği şablonlar, desteklenmeyen derlemeler ve özel türler için öneririz.  
  
- El ile bir VSıX paketi oluşturun. Bu seçeneği yalnızca diğer iki seçenek kullanılabilir olmadığında öneririz.  
  
  Bu belge, üçüncü seçeneği açıklar.  
  
## <a name="creating-a-vsix-package"></a>VSıX paketi oluşturma  
 Bir uzantıyı el ile paketlemek için uzantı projesine bir uzantı. manifest dosyası ve bir [Content_Types]. xml dosyası ekleyin, derleme Çıktılarınızla birlikte sıkıştırılmış bir dosyaya yerleştirin ve sıkıştırılmış dosyayı. vsix dosya adı uzantısına sahip olacak şekilde yeniden adlandırın. Paketlenecek uzantı [VSIX şeması](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)tarafından desteklenen bir türde olmalıdır.  
  
> [!NOTE]
> VSıX paketlerindeki dosyaların adları, [\[RFC2396\]](https://go.microsoft.com/fwlink/?LinkId=90339)altında tanımlandığı şekilde Tekdüzen Kaynak tanımlayıcılarında (URI) ayrılan boşluk veya karakterleri içermemelidir.  
  
#### <a name="to-manually-create-a-vsix-package"></a>El ile bir VSıX paketi oluşturmak için  
  
1. VSıX şeması tarafından desteklenen bir türün Visual Studio uzantısı oluşturun.  
  
2. Bir XML dosyası oluşturun ve `extension.vsixmanifest`adlandırın.  
  
3. Extension. valtmanifest dosyasını VSıX şemasına göre girin. Örnek bildirim için bkz. [PackageManifest öğesi (root öğesi, VSX şeması)](https://msdn.microsoft.com/f8ae42ba-775a-4d2b-976a-f556e147f187).  
  
4. İkinci bir XML dosyası oluşturun ve `[Content_Types].xml`olarak adlandırın.  
  
5. [Content_Types]. xml dosyasını [Content_types\]. xml dosyasının yapısında](../extensibility/the-structure-of-the-content-types-dot-xml-file.md)belirtilen şekilde girin.  
  
6. XML dosyalarını, dağıtılacak uzantıyla birlikte bir dizine yerleştirin.  
  
     Proje şablonu veya öğe şablonu söz konusu olduğunda, şablonu içeren. zip dosyasını XML dosyalarıyla aynı klasöre yerleştirin. XML dosyalarını. zip dosyasına yerleştirmeyin.  
  
     Diğer tüm durumlarda, XML dosyalarını yapı çıkışıyla aynı dizine yerleştirin.  
  
7. Windows Gezgini 'nde, uzantı içeriğini ve iki XML dosyasını içeren klasöre sağ tıklayın, **Gönder ' e**tıklayın ve ardından **Sıkıştırılmış (daraltılmış) klasör**' e tıklayın.  
  
8. Elde edilen. zip dosyasını *filename*. vsix olarak yeniden adlandırın; burada *filename* , paketinizi yükleyen yeniden dağıtılabilir dosyanın adıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio uzantılarını gönderme](../extensibility/shipping-visual-studio-extensions.md)   
 [VSIX paketinin Anatomumu](../extensibility/anatomy-of-a-vsix-package.md)   
 [PackageManifest öğesi (root öğesi, VSX şeması)](https://msdn.microsoft.com/f8ae42ba-775a-4d2b-976a-f556e147f187)