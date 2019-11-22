---
title: VSıX paketinin anatomumu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- visual studio extension
- vsix
- packages
ms.assetid: 8b86d62f-c274-4e91-82e0-38cdb9a423d5
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 156b221265b4c3c23b795b09b9a50ccb27a63bcf
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295645"
---
# <a name="anatomy-of-a-vsix-package"></a>Bir VSIX Paketinin Anatomisi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSıX paketi, Visual Studio 'Nun uzantıları sınıflandırmak ve yüklemek için kullandığı meta verilerle birlikte bir veya daha fazla Visual Studio uzantısı içeren bir. VSIX dosyasıdır. Bu meta veriler VSıX bildiriminde ve [Content_Types]. xml dosyasında bulunur. Bir VSıX paketi ayrıca yerelleştirilmiş kurulum metni sağlamak için bir veya daha fazla Extension. valtlangpack dosyası içerebilir ve bağımlılıkları yüklemek için ek VSıX paketleri içerebilir.  
  
 VSıX paketi biçimi açık paketleme kuralları (OPC) standardını izler. Paket, bir [Content_Types]. xml dosyası ve bir. vsix bildirim dosyası ile birlikte ikili dosyaları ve destekleyici dosyaları içerir. Bir VSıX paketi birden çok projenin çıkışını ya da kendi bildirimlerine sahip birden çok paketi içerebilir.  
  
> [!NOTE]
> VSıX paketlerine dahil edilen dosyaların adları, [\[RFC2396\]](https://go.microsoft.com/fwlink/?LinkId=90339)altında tanımlandığı gibi Tekdüzen Kaynak tanımlayıcılarında (URI) ayrılan boşluk veya karakterleri içermemelidir.  
  
## <a name="the-vsix-manifest"></a>VSıX bildirimi  
 VSıX bildirimi yüklenecek uzantı hakkında bilgiler içerir ve VSX şemasını izler. Daha fazla bilgi için bkz. [VSIX uzantı şeması 1,0 başvurusu](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b). Örnek VSıX bildirimi için bkz. [PackageManifest öğesi (root öğesi, VSX şeması)](https://msdn.microsoft.com/f8ae42ba-775a-4d2b-976a-f556e147f187).  
  
 VSıX bildirimi bir. vsix dosyasına dahil edildiğinde `extension.vsixmanifest` olarak adlandırılmalıdır.  
  
## <a name="the-content"></a>Içerik  
 Bir VSıX paketi, Visual Studio tarafından desteklenen şablonlar, araç kutusu öğeleri, VSPackages veya diğer uzantı türlerini içerebilir.  
  
## <a name="language-packs"></a>Dil Paketleri  
 Bir VSıX paketi, yükleme sırasında yerelleştirilmiş metin sağlamak için bir veya daha fazla Extension. valtlangpack dosyası içerebilir. Daha fazla bilgi için bkz. [VSIX paketlerini yerelleştirme](../extensibility/localizing-vsix-packages.md).  
  
## <a name="dependencies-and-references"></a>Bağımlılıklar ve başvurular  
 VSıX paketi, diğer VSıX paketlerini başvuru olarak içerebilir. Bu diğer paketlerin her biri kendi VSıX bildirimini içermelidir.  
  
 Bir Kullanıcı bağımlılıkları olan bir uzantıyı yüklemeye çalışırsa, yükleyici gerekli derlemelerin Kullanıcı sisteminde yüklü olduğunu doğrular. Gerekli derlemeler bulunamazsa, **Uzantılar ve güncelleştirmeler** eksik derlemelerin bir listesini görüntüler.  
  
 Uzantı bildirimi bir veya daha fazla [başvuru](https://msdn.microsoft.com/32c52934-e81e-4b53-8cb6-4df45ef7bfa8) öğesi Içeriyorsa, **Uzantılar ve güncelleştirmeler** , her başvurunun bildirimini sistemde yüklü olan uzantılara göre karşılaştırır ve henüz yüklenmemişse başvurulan uzantıyı ekler. Başvurulan bir uzantının önceki bir sürümü yüklüyse, yeni sürüm yerini alır.  
  
 Çoklu proje çözümündeki bir proje aynı çözümdeki başka bir projeye başvuru içeriyorsa, VSıX paketi o projenin bağımlılıklarını içerir. İç proje başvurusuna tıklayarak ve ardından **Özellikler** penceresinde **VSIX özelliğinde bulunan çıkış gruplarını** `BuiltProjectOutputGroup`olarak ayarlayarak bu davranışı geçersiz kılabilirsiniz.  
  
 VSıX paketindeki başvurulan derlemelerden uydu dll 'Leri eklemek için, **VSIX özelliğinde bulunan çıkış gruplarına** `SatelliteDllsProjectOutputGroup` ekleyin.  
  
## <a name="installation-location"></a>Yükleme Konumu  
 Yükleme sırasında, **Uzantılar ve güncelleştirmeler** , VSIX paketinin içeriğini%LocalAppData%\Microsoft\VisualStudio\14.0\extensionaltındaki bir klasörde arar.  
  
 Varsayılan olarak, yükleme yalnızca geçerli kullanıcı için geçerlidir, çünkü% LocalAppData% kullanıcıya özgü bir dizindir. Ancak, bildirimin [ALLUSERS](https://msdn.microsoft.com/ac817f50-3276-4ddb-b467-8bbb1432455b) öğesini `True`olarak ayarlarsanız, uzantı altına yüklenir.\\*VisualStudioInstallationFolder*\Common7\IDE\Extensions ve bilgisayarın tüm kullanıcıları tarafından kullanılabilir.  
  
## <a name="content_typesxml"></a>[Content_Types]. xml  
 [Content_Types]. xml dosyası genişletilmiş. vsix dosyasındaki dosya türlerini tanımlar. Visual Studio, paketin yüklenmesi sırasında bu dosyayı kullanır, ancak dosyanın kendisini yüklemez. Bu dosya hakkında daha fazla bilgi için [Content_types\]. xml dosyasının yapısına](../extensibility/the-structure-of-the-content-types-dot-xml-file.md)bakın.  
  
 Açık paketleme kuralları (OPC) standardı için bir [Content_Types]. xml dosyası gereklidir. OPC hakkında daha fazla bilgi için bkz. [OPC: msdn Web sitesinde verilerinizi paketlemeye yönelik yeni bir standart](https://go.microsoft.com/fwlink/?LinkID=148207) .
