---
title: Proje öğelerinde & dağıtım bilgilerini paketleme
description: özellik özellikleri, özellik alıcıları, proje çıktı başvuruları ve güvenli denetim varlıklarını kullanarak SharePoint proje öğelerinde paketleme ve dağıtım verileri ekleyin.
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
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 907bb1ed7131859dbf618c7b4b53e1d87b23e2ae
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635601"
---
# <a name="provide-packaging-and-deployment-information-in-project-items"></a>Proje Öğelerinde Paketleme ve dağıtım bilgileri sağlama
  içindeki tüm SharePoint proje öğeleri [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , proje SharePoint dağıtıldığında ek veri sağlamak için kullanabileceğiniz özelliklere sahiptir. Bu özellikler aşağıdaki gibidir:

- Özellik özellikleri

- Özellik alıcıları

- Project Çıkış başvuruları

- Kasa Denetim girişleri

  Bu özellikler **Özellikler** penceresinde görünür.

## <a name="feature-properties"></a>Özellik özellikleri
 Özelliğin kullandığı verileri belirtmek için **özellik özellikleri** özelliğini kullanın. Özellik özellikleri verileri, SharePoint dağıtılan bir özelliğe eklenen bir değerler kümesidir (anahtar/değer çiftleri olarak saklanır). Özellik dağıtıldıktan sonra, kodunuzda özellik değerlerine erişebilirsiniz.

 Bir proje öğesine Özellik özelliği değeri eklediğinizde, değer öğenin özelliğinin bildirimine bir öğe olarak eklenir. Bir Iş verileri bağlantısı (BDC) modeli projesinde, örneğin ModelFileName özelliği özelliği şöyle görünür:

```xml
<Property Key="ModelFileName" Value="BdcModel1\BdcModel1.bdcm" />
```

 Özellik özellik değerini ayarladıktan sonra, projenin *. spdata* dosyasına bir FeatureProperty öğesi olarak eklenir. SharePoint özelliklere erişme hakkında daha fazla bilgi için bkz. [spfeaturepropertycollection sınıfı](/previous-versions/office/sharepoint-server/ms461895(v=office.15)).

 Tüm proje öğelerinden özdeş Özellik özelliği değerleri, özellik bildiriminde birlikte birleştirilir. Ancak, iki farklı proje öğesi, eşleşmeyen değerlerle aynı özellik özelliği anahtarını belirtursa, bir doğrulama hatası oluşur.

 özellik dosyasına (*. feature*) doğrudan özellik özellikleri eklemek için, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint nesne modeli yöntemini çağırın <xref:Microsoft.VisualStudio.SharePoint.Features.IPropertyCollection.Add%2A> . Bu yöntemi kullanırsanız, özellik özelliklerinde aynı özellik özelliği değerlerini eklemekle aynı kuralın aynı zamanda doğrudan özellik dosyasına eklenen özellikler için de geçerli olduğunu unutmayın.

## <a name="feature-receiver"></a>Özellik alıcısı
 Özellik alıcıları, bir proje öğesinin içeren özelliği için belirli olaylar gerçekleştiğinde yürütülen koddur. Örneğin, özellik yüklendiğinde, etkinleştirildiğinde veya yükseltildiğinde yürütülen Özellik alıcılarını tanımlayabilirsiniz. Özellik alıcısı eklemenin bir yolu, bunu [Izlenecek yol: özellik Olay alıcıları ekleme](../sharepoint/walkthrough-add-feature-event-receivers.md)bölümünde açıklandığı gibi doğrudan bir özelliğe eklemektir. Başka bir yöntem **de özellik alıcısı özelliğindeki bir** özellik alıcısı sınıf adına ve derlemesine başvurulmanız.

### <a name="direct-method"></a>Direct yöntemi
 Bir özelliğe doğrudan bir özellik alıcısı eklediğinizde, bir kod dosyası Çözüm Gezgini **özellik** düğümünün altına yerleştirilir. SharePoint çözümünüzü oluşturduğunuzda, kod bir derlemeye derlenir ve SharePoint dağıtır. Varsayılan olarak, özellik özellikleri **alıcı derleme** ve **alıcı sınıfı** , sınıf adına ve derlemeye başvurur.

### <a name="reference-method"></a>Reference yöntemi
 Özellik alıcısı eklemenin başka bir yolu da bir özellik alıcısı derlemesine başvurmak için bir proje öğesinin **özellik alıcısı** özelliğini kullanmaktır. Özellik alıcısı Özellik değeri iki alt özelliğe sahiptir: **derleme** ve **sınıf adı**. Derlemenin tam olarak nitelenmiş, "Strong" adını kullanması ve sınıf adının tam tür adı olması gerekir. Daha fazla bilgi için bkz. [Strong-adlandırılmış derlemeler](/previous-versions/dotnet/netframework-4.0/wd40t7ad(v=vs.100)). çözümü SharePoint dağıttıktan sonra, özellik olayları işlemek için başvurulan özellik alıcısını kullanır.

 çözüm derleme zamanında, özellik ve projeleri içindeki özellik alıcı özelliği değerleri, SharePoint çözümü (*. wsp*) dosyasının özellik bildiriminde özellik öğesinin ReceiverAssembly ve ReceiverClass özniteliklerini ayarlamak için birlikte birleştirilir. Bu nedenle, bir proje öğesi ve bir özelliğin derleme ve sınıf adı özellik değerleri belirtilirse, proje öğesi ve özellik özelliği değerleri eşleşmelidir. Değerler eşleşmiyorsa, bir doğrulama hatası alırsınız. Bir proje öğesinin özelliği tarafından kullanılan bir özellik alıcısı derlemesine başvurması istiyorsanız, onu başka bir özelliğe taşıyın.

 Zaten sunucuda olmayan bir özellik alıcısı derlemesine başvuru yaparsanız, derleme dosyasının kendisini pakete da dahil etmeniz gerekir; [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] bunu sizin için eklemez. özelliği dağıttığınızda, derleme dosyası [!INCLUDE[TLA#tla_gac](../sharepoint/includes/tlasharptla-gac-md.md)] SharePoint fiziksel dizinindeki sistemin veya Bin klasörünün içine kopyalanır. Daha fazla bilgi için bkz. nasıl yapılır: [nasıl yapılır: ek derlemeler ekleme ve kaldırma](../sharepoint/how-to-add-and-remove-additional-assemblies.md).

 Özellik alıcıları hakkında daha fazla bilgi için bkz. [özellik olay alıcısı](/previous-versions/office/developer/sharepoint-2007/bb862634(v=office.12)) ve [Özellik olayları](/previous-versions/office/developer/sharepoint-2010/ms469501(v=office.14)).

## <a name="project-output-references"></a>çıkış başvurularını Project
 Project Output başvuruları özelliği, proje öğesinin çalıştırması gereken bir derleme gibi bir bağımlılık belirtir. Örneğin, çözümünüzün bir BDC projesi ve bir sınıf projesi olduğunu varsayalım. ivb projesinde, sınıf projesi tarafından çıktı olan derlemeye bir bağımlılık varsa, bdc projesinin Project çıktı başvuruları özelliğindeki derlemeye başvurabilirsiniz. IVB projesi paketlenmişse, bağımlı derleme pakete dahil edilir.

 Project çıktı başvuruları genellikle derlemelerdir, ancak bazı durumlarda (örneğin, Silverlight projeleri) diğer dosya türleri olabilir.

 Daha fazla bilgi için bkz. [nasıl yapılır: proje çıktı başvurusu ekleme](../sharepoint/how-to-add-a-project-output-reference.md).

## <a name="safe-control-entries"></a>denetim girişlerini Kasa
 SharePoint güvenilmeyen kullanıcıların erişimini belirli denetimlere sınırlamak için güvenli denetim girişleri adlı bir güvenlik mekanizması sağlar. SharePoint, güvenilmeyen kullanıcıların SharePoint sunucusunda ASPX sayfaları yüklemesine ve oluşturmasına izin verir. bu kullanıcıların ASPX sayfalarına güvenli olmayan kod eklemesini engellemek için SharePoint *güvenli denetimlere* erişimini kısıtlar. Kasa denetimleri, sitenizdeki herhangi bir kullanıcı tarafından kullanılabilen ve güvenli olarak belirlenmiş olan ASPX denetimleridir ve Web bölümleridir. daha fazla bilgi için bkz. [4. adım: Web bölümünü Kasa denetimleri listesine ekleme](/previous-versions/office/developer/sharepoint-2007/ms581321(v=office.12)).

 içindeki her SharePoint proje öğesi [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] iki Boolean alt özelliğine sahip **Kasa denetim girdileri** olan bir özelliğe sahiptir: **Kasa** ve **betikte Kasa**. Kasa özelliği, güvenilmeyen kullanıcıların bir denetime erişip erişemeyeceğini belirtir. betiğe karşı Kasa, güvenilmeyen kullanıcıların bir denetimin özelliklerini görüntüleyip değiştiremeyeceğini belirtir.

 Kasa denetim girişlerine bir derleme temelinde başvurulur. proje öğesinin **Kasa denetim girdileri** özelliğine girerek, bir projenin derlemesine güvenli denetim girişleri eklersiniz. Ancak, pakete ek bir derleme eklediğinizde, **paket Tasarımcısı** ' nda **Gelişmiş** sekmesi aracılığıyla bir projenin derlemesine güvenli denetim girişleri de ekleyebilirsiniz. daha fazla bilgi için bkz. [nasıl yapılır: denetimleri güvenli denetim olarak işaretleme](../sharepoint/how-to-mark-controls-as-safe-controls.md) veya [bir Web bölümü derlemesini Kasa denetimi olarak kaydetme](/previous-versions/office/developer/sharepoint2003/dd587360(v=office.11)).

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
- [paketleme ve dağıtım SharePoint uzat](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
