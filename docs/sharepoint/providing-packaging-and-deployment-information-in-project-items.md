---
title: Proje & dağıtım bilgilerini paketleme
description: Özellik özellikleri, özellik alıcıları, SharePoint çıkış başvuruları ve güvenli denetim varlıklarını kullanarak proje öğelerine paketleme ve dağıtım verileri ekleyin.
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
ms.openlocfilehash: c9b9b91f97d1eb7f2025f3c96f588ddf1094491820e0c875b002c9b0ea0a415f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121409402"
---
# <a name="provide-packaging-and-deployment-information-in-project-items"></a>Proje öğelerinde paketleme ve dağıtım bilgilerini sağlama
  'SharePoint tüm proje öğeleri, proje SharePoint'a dağıtıldığında ek veri sağlamak [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] için kullanabileceğiniz özelliklere sahiptir. Bu özellikler aşağıdaki gibidir:

- Özellik Özellikleri

- Özellik Alıcıları

- Project Çıkış Başvuruları

- Kasa Denetim Girişleri

  Bu özellikler Özellikler **penceresinde** görünür.

## <a name="feature-properties"></a>Özellik özellikleri
 Özelliğin **kullandığı** verileri belirtmek için Özellik Özellikleri özelliğini kullanın. Özellik özellikleri verileri, özel bir özelle birlikte dağıtan bir değer kümesidir (anahtar/değer çiftleri olarak depolanır) SharePoint. Özellik dağıtıldıktan sonra kodundaki özellik değerlerine erişebilirsiniz.

 Bir proje öğesine özellik özelliği değeri eklerken, değer öğenin özelliğinin bildiriminde bir öğe olarak eklenir. İş Verileri Bağlantısı (BDC) model projesinde, örneğin ModelFileName özellik özelliği şöyle görünür:

```xml
<Property Key="ModelFileName" Value="BdcModel1\BdcModel1.bdcm" />
```

 Bir Özellik Özelliği değeri ayardikten sonra, projenin *.spdata* dosyasına FeatureProperty öğesi olarak eklenir. SharePoint'daki özelliklere erişme hakkında bilgi için bkz. [SPFeaturePropertyCollection Sınıfı.](/previous-versions/office/sharepoint-server/ms461895(v=office.15))

 Tüm proje öğelerinden aynı özellik özelliği değerleri, özellik bildiriminde birlikte birleştirilir. Ancak, iki farklı proje öğe eşleşmeyen değerlerle aynı özellik özellik anahtarını belirtirse doğrulama hatası oluşur.

 Özellik özelliklerini doğrudan özellik dosyasına (*.feature)* eklemek için nesne [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint yöntemini <xref:Microsoft.VisualStudio.SharePoint.Features.IPropertyCollection.Add%2A> arayın. Bu yöntemi kullanırsanız, Özellik Özellikleri'ne özdeş özellik değerleri eklemeyle ilgili aynı kuralın doğrudan özellik dosyasına eklenen özellikler için de geçerli olduğunu unutmayın.

## <a name="feature-receiver"></a>Özellik alıcısı
 Özellik alıcıları, bir proje öğesinin içeren özelliğinde belirli olaylar oluştuğunda yürütülen koddur. Örneğin, özellik yüklenirken, etkinleştirildiğinde veya yükseltildiğinde yürütülen özellik alıcılarını tanımlayabilirsiniz. Özellik alıcısı eklemenin yollarından biri, bunu Kılavuz: Özellik olayı alıcıları ekleme konusunda açıklandığı [gibi doğrudan bir özelliğe eklemektir.](../sharepoint/walkthrough-add-feature-event-receivers.md) Bir diğer yol da Özellik Alıcısı özelliğinde özellik alıcısı sınıf adına ve **derlemeye başvuru yapmaktır.**

### <a name="direct-method"></a>Doğrudan yöntem
 Bir özelliği doğrudan bir özellik alıcısına eklerken, bir kod dosyası, doğrudan bir özellik **Çözüm Gezgini.** Uygulama çözümünüz SharePoint kod bir derlemede derlenmiş ve SharePoint. Varsayılan olarak, Alıcı Derlemesi **ve Alıcı Sınıfı** özellik özellikleri **sınıf** adına ve derlemeye başvurur.

### <a name="reference-method"></a>Reference yöntemi
 Özellik alıcısı eklemenin başka bir  yolu, bir özellik alıcı derlemesine başvuru yapmak için bir proje öğesinin Özellik Alıcısı özelliğini kullanmaktır. Özellik Alıcısı özellik değerinin iki alt özelliği vardır: **Derleme ve** **Sınıf Adı.** Derlemenin tam, "güçlü" adını ve sınıf adının tam tür adını kullanması gerekir. Daha fazla bilgi için [bkz. Güçlü Adlandırılmış Derlemeler.](/previous-versions/dotnet/netframework-4.0/wd40t7ad(v=vs.100)) Çözümü SharePoint dağıtan özellik, özellik olaylarını işlemek için başvurulan özellik alıcısını kullanır.

 Çözüm derleme zamanında, özellik ve projeleri özellik alıcısı özellik değerleri, SharePoint çözümü (*.wsp*) dosyasının özellik bildiriminde Feature öğesinin ReceiverAssembly ve ReceiverClass özniteliklerini ayarlamak için bir araya geliyor. Bu nedenle, bir proje öğesinin Ve bir özelliğin Derleme ve Sınıf Adı özellik değerleri belirtilmişse, proje öğesi ve özellik özellik değerleri eşleşmesi gerekir. Değerler eşleşmezse doğrulama hatası alırsınız. Bir proje öğesinin, özelliğinin kullandığı derleme dışında bir özellik alıcı derlemesine başvurursa, bunu başka bir özelle taşıması gerekir.

 Sunucuda zaten yer almamış bir özellik alıcı derlemeye başvurursanız, derleme dosyasının kendisini de pakete dahil etmek gerekir; [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sizin için eklemez. Özelliği dağıtarak derleme dosyası, fiziksel dizindeki sistem veya Bin [!INCLUDE[TLA#tla_gac](../sharepoint/includes/tlasharptla-gac-md.md)] klasörüne SharePoint. Daha fazla bilgi için, bkz. nasıl? Nasıl 2012: Ek [derlemeler ekleme ve kaldırma.](../sharepoint/how-to-add-and-remove-additional-assemblies.md)

 Özellik alıcıları hakkında daha fazla bilgi için bkz. [Özellik Olayı Alıcısı ve](/previous-versions/office/developer/sharepoint-2007/bb862634(v=office.12)) Özellik [Olayları.](/previous-versions/office/developer/sharepoint-2010/ms469501(v=office.14))

## <a name="project-output-references"></a>Project çıkış başvuruları
 Project Çıkış Başvuruları özelliği, proje öğenizin çalışması gereken bir derleme gibi bir bağımlılığı belirtir. Örneğin, çözüm bir BDC projesi ve bir sınıf projesi olduğunu varsayalım. BDC projesinin sınıf projesinin çıkışı olan derlemeye bağımlılığı varsa, BDC projesinin Project Çıkış Başvuruları özelliğinde derlemeye başvurabilirsiniz. BDC projesi pakete ekli olduğunda bağımlı derleme pakete dahil edilir.

 Project başvuruları genellikle derlemelerdir, ancak bazı durumlarda (Silverlight projeleri gibi) diğer dosya türleri olabilir.

 Daha fazla bilgi için, [bkz. How to: Add a project output reference](../sharepoint/how-to-add-a-project-output-reference.md).

## <a name="safe-control-entries"></a>Kasa girişlerini denetleme
 SharePoint, güvenilmeyen kullanıcıların erişimini belirli denetimler ile sınırlamak için güvenli denetim girişleri olarak adlandırılan bir güvenlik mekanizması sağlar. Tasarım olarak, SharePoint güvenilmeyen kullanıcıların SharePoint sunucusunda ASPX sayfaları yüklemelerine ve oluşturmalarını sağlar. Bu kullanıcıların ASPX sayfalarına güvenli olmayan kod eklemesini önlemek SharePoint erişimlerini güvenli *denetimlere sınırlar.* Kasa, aspx denetimleri ve güvenli olarak belirlenmiş web bölümleridir ve siteniz üzerinde herhangi bir kullanıcı tarafından kullanılabilir. Daha fazla bilgi için [bkz. 4. Adım: Web Bölümü'nizi Kasa Listesine ekleme.](/previous-versions/office/developer/sharepoint-2007/ms581321(v=office.12))

 içinde SharePoint proje öğesinin iki Boole alt özelliği olan Kasa Denetim Girdileri adlı bir özelliği [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] vardır: **Kasa** ve Kasa **Karşı.**  Kasa özelliği güvenilmeyen kullanıcıların bir denetime erişip erişe olmadığını belirtir. Against Script Kasa özelliği güvenilmeyen kullanıcıların bir denetimin özelliklerini görüntüp değiştiremeyeceklerini belirtir.

 Kasa denetim girişlerine derleme temelinde başvurulmaktadır. Projenin derlemesine güvenli denetim girişleri eklemek için bunları proje öğesinin Kasa **Girdileri özelliğine girersiniz.** Ancak, pakete ek bir derleme eklerken Paket Tasarımcısı'nın Gelişmiş  sekmesi aracılığıyla projenin derlemesi için güvenli denetim girdileri de ekleyebilirsiniz.  Daha fazla bilgi için [bkz. Nasıl olur: Denetimleri](../sharepoint/how-to-mark-controls-as-safe-controls.md) güvenli denetim olarak işaretleme veya Web Bölümü Derlemesini Denetim [olarak Kasa.](/previous-versions/office/developer/sharepoint2003/dd587360(v=office.11))

### <a name="xml-entries-for-safe-controls"></a>Güvenli denetimler için XML girişleri
 Bir proje öğesine veya projenin derlemesine güvenli denetim girişi eklerken, paket bildirimine aşağıdaki biçimde bir başvuru yazılır:

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
- [Paket ve dağıtım SharePoint dağıtma](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
- [Çözüme dosya eklemek için modülleri kullanma](../sharepoint/using-modules-to-include-files-in-the-solution.md)
- [Paketleme SharePoint dağıtımı genişletme](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
