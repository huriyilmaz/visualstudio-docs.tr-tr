---
title: Proje öğelerinde & dağıtım bilgilerini paketleme
description: Özellik özellikleri, özellik alıcıları, proje çıktı başvuruları ve güvenli denetim varlıklarını kullanarak SharePoint Proje Öğelerinde Paketleme ve dağıtım verileri ekleyin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.SafeControlEntries
- VS.SharePointTools.Project.ProjectOutputReference
- VS.SharePointTools.Project.FeatureProperties
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, safe controls
- project output references [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, feature properties
- SharePoint development in Visual Studio, project output references
- SharePoint development in Visual Studio, advanced packaging tools
- feature properties [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, feature receiver
- feature receiver [SharePoint development in Visual Studio]
- safe controls [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f73d8727fb960cf519d368d928aa20cae38ae1a9
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95970479"
---
# <a name="provide-packaging-and-deployment-information-in-project-items"></a>Proje Öğelerinde Paketleme ve dağıtım bilgileri sağlama
  İçindeki tüm SharePoint proje öğeleri [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , proje SharePoint 'e dağıtıldığında ek veri sağlamak için kullanabileceğiniz özelliklere sahiptir. Bu özellikler aşağıdaki gibidir:

- Özellik özellikleri

- Özellik alıcıları

- Proje çıktısı başvuruları

- Güvenli denetim girdileri

  Bu özellikler **Özellikler** penceresinde görünür.

## <a name="feature-properties"></a>Özellik özellikleri
 Özelliğin kullandığı verileri belirtmek için **özellik özellikleri** özelliğini kullanın. Özellik özellikleri verileri, SharePoint 'e dağıttığında bir özelliğe dahil edilen bir değerler kümesidir (anahtar/değer çiftleri olarak saklanır). Özellik dağıtıldıktan sonra, kodunuzda özellik değerlerine erişebilirsiniz.

 Bir proje öğesine Özellik özelliği değeri eklediğinizde, değer öğenin özelliğinin bildirimine bir öğe olarak eklenir. Bir Iş verileri bağlantısı (BDC) modeli projesinde, örneğin ModelFileName özelliği özelliği şöyle görünür:

```xml
<Property Key="ModelFileName" Value="BdcModel1\BdcModel1.bdcm" />
```

 Özellik özellik değerini ayarladıktan sonra, projenin *. spdata* dosyasına bir FeatureProperty öğesi olarak eklenir. SharePoint içindeki özelliklere erişme hakkında daha fazla bilgi için bkz. [SPFeaturePropertyCollection sınıfı](/previous-versions/office/sharepoint-server/ms461895(v=office.15)).

 Tüm proje öğelerinden özdeş Özellik özelliği değerleri, özellik bildiriminde birlikte birleştirilir. Ancak, iki farklı proje öğesi, eşleşmeyen değerlerle aynı özellik özelliği anahtarını belirtursa, bir doğrulama hatası oluşur.

 Özellik dosyasını doğrudan özellik dosyasına (*. feature*) eklemek için [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint nesne modeli yöntemini çağırın <xref:Microsoft.VisualStudio.SharePoint.Features.IPropertyCollection.Add%2A> . Bu yöntemi kullanırsanız, özellik özelliklerinde aynı özellik özelliği değerlerini eklemekle aynı kuralın aynı zamanda doğrudan özellik dosyasına eklenen özellikler için de geçerli olduğunu unutmayın.

## <a name="feature-receiver"></a>Özellik alıcısı
 Özellik alıcıları, bir proje öğesinin içeren özelliği için belirli olaylar gerçekleştiğinde yürütülen koddur. Örneğin, özellik yüklendiğinde, etkinleştirildiğinde veya yükseltildiğinde yürütülen Özellik alıcılarını tanımlayabilirsiniz. Özellik alıcısı eklemenin bir yolu, bunu [Izlenecek yol: özellik Olay alıcıları ekleme](../sharepoint/walkthrough-add-feature-event-receivers.md)bölümünde açıklandığı gibi doğrudan bir özelliğe eklemektir. Başka bir yöntem **de özellik alıcısı özelliğindeki bir** özellik alıcısı sınıf adına ve derlemesine başvurulmanız.

### <a name="direct-method"></a>Direct yöntemi
 Bir özelliğe doğrudan bir özellik alıcısı eklediğinizde, bir kod dosyası Çözüm Gezgini **özellik** düğümünün altına yerleştirilir. SharePoint Çözümünüzü oluşturduğunuzda, kod bir derlemede derlenir ve SharePoint 'e dağıtılır. Varsayılan olarak, özellik özellikleri **alıcı derleme** ve **alıcı sınıfı** , sınıf adına ve derlemeye başvurur.

### <a name="reference-method"></a>Reference yöntemi
 Özellik alıcısı eklemenin başka bir yolu da bir özellik alıcısı derlemesine başvurmak için bir proje öğesinin **özellik alıcısı** özelliğini kullanmaktır. Özellik alıcısı Özellik değeri iki alt özelliğe sahiptir: **derleme** ve **sınıf adı**. Derlemenin tam olarak nitelenmiş, "Strong" adını kullanması ve sınıf adının tam tür adı olması gerekir. Daha fazla bilgi için bkz. [Strong-adlandırılmış derlemeler](/previous-versions/dotnet/netframework-4.0/wd40t7ad(v=vs.100)). Çözümü SharePoint 'e dağıttıktan sonra, Özellik olayları işlemek için başvurulan özellik alıcısını kullanır.

 Çözüm derleme zamanında, özellikte ve projelerinde özellik alıcı özelliği değerleri, SharePoint çözümü (*. wsp*) dosyasının özellik bildiriminde özellik öğesinin ReceiverAssembly ve ReceiverClass özniteliklerini ayarlamak için birlikte birleştirilir. Bu nedenle, bir proje öğesi ve bir özelliğin derleme ve sınıf adı özellik değerleri belirtilirse, proje öğesi ve özellik özelliği değerleri eşleşmelidir. Değerler eşleşmiyorsa, bir doğrulama hatası alırsınız. Bir proje öğesinin özelliği tarafından kullanılan bir özellik alıcısı derlemesine başvurması istiyorsanız, onu başka bir özelliğe taşıyın.

 Zaten sunucuda olmayan bir özellik alıcısı derlemesine başvuru yaparsanız, derleme dosyasının kendisini pakete da dahil etmeniz gerekir; [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] bunu sizin için eklemez. Özelliği dağıttığınızda, derleme dosyası, sistemin [!INCLUDE[TLA#tla_gac](../sharepoint/includes/tlasharptla-gac-md.md)] veya SharePoint fiziksel dizinindeki bin klasörüne kopyalanır. Daha fazla bilgi için bkz. nasıl yapılır: [nasıl yapılır: ek derlemeler ekleme ve kaldırma](../sharepoint/how-to-add-and-remove-additional-assemblies.md).

 Özellik alıcıları hakkında daha fazla bilgi için bkz. [özellik olay alıcısı](/previous-versions/office/developer/sharepoint-2007/bb862634(v=office.12)) ve [Özellik olayları](/previous-versions/office/developer/sharepoint-2010/ms469501(v=office.14)).

## <a name="project-output-references"></a>Proje çıktısı başvuruları
 Proje çıktısı başvuruları özelliği, proje öğesinin çalıştırması gereken bir derleme gibi bir bağımlılık belirtir. Örneğin, çözümünüzün bir BDC projesi ve bir sınıf projesi olduğunu varsayalım. IVB projesinde, sınıf projesi tarafından çıktı olan derlemeye bir bağımlılık varsa, BDC projesinin proje çıktı başvuruları özelliğindeki derlemeye başvurabilirsiniz. IVB projesi paketlenmişse, bağımlı derleme pakete dahil edilir.

 Proje çıktı başvuruları genellikle derlemelerdir, ancak bazı durumlarda (örneğin, Silverlight projeleri) diğer dosya türleri olabilir.

 Daha fazla bilgi için bkz. [nasıl yapılır: proje çıktı başvurusu ekleme](../sharepoint/how-to-add-a-project-output-reference.md).

## <a name="safe-control-entries"></a>Güvenli denetim girdileri
 SharePoint, güvenilmeyen kullanıcıların erişimini belirli denetimlere sınırlamak için güvenli denetim girişleri adlı bir güvenlik mekanizması sağlar. Tasarım, SharePoint 'e güvenilmeyen kullanıcıların, SharePoint sunucusunda ASPX sayfaları yüklemesine ve oluşturmalarına olanak tanır. Bu kullanıcıların ASPX sayfalarına güvenli olmayan kod eklemesini engellemek için, SharePoint *güvenli denetimlere* erişimini sınırlandırır. Güvenli denetimler, sitenizdeki herhangi bir kullanıcı tarafından kullanılabilen ve güvenli olarak belirlenmiş olan ASPX denetimleridir ve Web bölümleridir. Daha fazla bilgi için bkz. [4. Adım: Web bölümünü güvenli denetimler listesine ekleme](/previous-versions/office/developer/sharepoint-2007/ms581321(v=office.12)).

 İçindeki her SharePoint proje öğesi, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Iki Boolean alt özelliğine sahip **Güvenli denetim girişleri** adlı bir özelliğe sahiptir: **betikte** **güvenli** ve güvenlidir. Safe özelliği, güvenilmeyen kullanıcıların bir denetime erişip erişemeyeceğini belirtir. Betik özelliği açısından güvenli, güvenilmeyen kullanıcıların bir denetimin özelliklerini görüntüleyip değiştiremeyeceğini belirtir.

 Güvenli denetim girişlerine bir derleme temelinde başvurulur. Proje öğesinin **Güvenli denetim girişleri** özelliğine girerek bir projenin derlemesine güvenli denetim girişleri eklersiniz. Ancak, pakete ek bir derleme eklediğinizde, **paket Tasarımcısı** ' nda **Gelişmiş** sekmesi aracılığıyla bir projenin derlemesine güvenli denetim girişleri de ekleyebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: denetimleri güvenli denetim olarak işaretleme](../sharepoint/how-to-mark-controls-as-safe-controls.md) veya [bir Web Bölümü derlemesini güvenli denetim olarak kaydetme](/previous-versions/office/developer/sharepoint2003/dd587360(v=office.11)).

### <a name="xml-entries-for-safe-controls"></a>Güvenli denetimler için XML girdileri
 Bir proje öğesine veya projenin derlemesine bir güvenli denetim girişi eklediğinizde, paket bildirimine aşağıdaki biçimde bir başvuru yazılır:

```xml
<Assemblies>
    <Assembly Location="<assembly name>.dll"
      DeploymentTarget="<'GlobalAssemblyCache' or 'WebApplication'">>
        <SafeControls>
            <SafeControl Assembly="<assembly name>.dll" Namespace=
              "<SharePoint project name>" Safe="<true/false>"
                TypeName="<control name>"
                SafeAgainstScript="<true/false>" />
        </SafeControls>
    </Assembly>
</Assemblies>
```

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint çözümlerini paketleme ve dağıtma](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
- [Çözümdeki dosyaları dahil etmek için modülleri kullanma](../sharepoint/using-modules-to-include-files-in-the-solution.md)
- [SharePoint paketleme ve dağıtımını genişletme](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
