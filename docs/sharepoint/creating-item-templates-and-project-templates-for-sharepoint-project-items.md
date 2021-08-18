---
title: Proje öğeleri için öğe şablonları/SharePoint şablonları
description: Proje öğeleri oluşturmak için öğe şablonları ve SharePoint şablonları oluşturun. Öğe şablonları ve proje şablonları için sihirbazlar oluşturun.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, creating custom templates
- .spdata files
- projects [SharePoint development in Visual Studio], creating custom templates
- SharePoint projects, creating custom templates
- SharePoint development in Visual Studio, creating custom project and item templates
- project items [SharePoint development in Visual Studio], creating custom templates
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: edcc56e0b92d5a694793f54ede8056fbe81ce2b1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122149643"
---
# <a name="create-item-templates-and-project-templates-for-sharepoint-project-items"></a>Proje öğeleri için öğe şablonları ve SharePoint şablonları oluşturma

Özel bir proje SharePoint türü tanımladığınız zaman, bunu bir öğe şablonu veya proje şablonuyla ilişkilendirilebilirsiniz. Bu ilişki, diğer geliştiricilerin proje öğesini Visual Studio. Şablon için bir sihirbaz da oluşturabilirsiniz.

Örneğin, Visual Studio bir siteye alan eklemek için bir proje şablonu veya öğe şablonu SharePoint değildir. Bir alanı temsil eden SharePoint bir proje öğesi türü tanımlayabilir ve ardından diğer geliştiricilerin alan öğesini bir alan projesine eklemek için kullanabileceği bir SharePoint oluşturabilirsiniz. Veya geliştiricilerin alan öğesinin olduğu yeni bir SharePoint proje oluştura bir proje şablonu oluşturabilirsiniz. Her iki durumda da, geliştiriciler şablonlarınızı kullanırken görüntülenen bir sihirbaz da sabilirsiniz. Bu sihirbaz, yeni öğeyi veya projeyi yapılandırmak için geliştiricilerden bilgi toplayabilirsiniz.

Öğe şablonları ve proje şablonları, *.zip* veya proje oluşturmak için Visual Studio dosyalar içeren dosyalardır. Öğe şablonları ve proje şablonlarının temelleri hakkında daha fazla bilgi için [bkz. Proje ve öğe şablonları oluşturma.](../ide/creating-project-and-item-templates.md)

## <a name="create-item-templates"></a>Öğe şablonları oluşturma
 Bir proje öğesi için bir SharePoint şablonu oluşturursanız, her zaman gerekli olan bazı dosyalar ve belirli proje öğesi türleri tarafından kullanılmaktadır isteğe bağlı dosyalar vardır. Bir proje öğesi türü tanımlamayı ve bunun için bir öğe şablonu SharePoint gösteren bir kılavuz için bkz. Adım adım: Öğe şablonuyla özel eylem proje öğesi [oluşturma, Bölüm 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).

 Aşağıdaki tabloda, bir proje öğesi için bir öğe şablonu oluşturmak SharePoint dosyalar listelemektedir.

|Gerekli dosya|Açıklama|
|-------------------|-----------------|
|*Bir .spdata* dosyası|Bu XML dosyası, proje öğesinin içeriğini ve varsayılan davranışını belirtir. Bu dosyanın öğe şablonuna dahil olması gerekir. *.spdata* dosyalarının içeriği hakkında daha fazla bilgi için [bkz. SharePoint proje öğesi şema başvurusu.](../sharepoint/sharepoint-project-item-schema-reference.md)|
|Bir *.vstemplate* dosyası.|Bu dosya Visual Studio Yeni Öğe Ekle iletişim kutusunda şablonu  görüntülemek ve şablondan bir proje öğesi oluşturmak için gereken bilgileri sağlar. Bu dosyanın öğe şablonuna dahil olması gerekir. Daha fazla bilgi için [bkz. Visual Studio Meta Veri Dosyaları.](/previous-versions/visualstudio/visual-studio-2010/xsxc3ete\(v\=vs.100\))|
|Arabirimi Visual Studio bir uzantı <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> derlemesi.|Bu derleme, proje öğesinin çalışma zamanı davranışını tanımlar. Bu derleme, öğe şablonuyla VSIX paketine dahil edilecektir. Daha fazla bilgi için [bkz. SharePoint proje](../sharepoint/defining-custom-sharepoint-project-item-types.md) öğesi türlerini tanımlama ve SharePoint [araçları için uzantıları Visual Studio.](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)|

 Aşağıdaki tabloda, öğe şablonuna dahil edilecek en yaygın isteğe bağlı dosyalardan bazıları liste almaktadır. Bazı proje öğeleri türleri, burada listelenmiyor diğer dosyaları gerekli olabilir.

| İsteğe Bağlı Dosya | Açıklama |
|----------------------| - |
| *Elements.xml* | Özellik *öğesi* dosyası. Bu dosya, proje öğesi tarafından oluşturulan özelleştirmenin kullanıcı arabirimini ve davranışını tanımlar. Liste örnekleri, içerik türleri veya özel eylemler gibi her özelleştirme türünün, bu dosyanın içeriğini tanımlayan farklı bir şeması vardır. Daha fazla bilgi için [bkz. Yapı Taşı: Özellikler](/previous-versions/office/developer/sharepoint-2010/ee537350(v=office.14)) [ve Özellik Şemaları.](/previous-versions/office/developer/sharepoint-2010/ms414322(v=office.14)) |
| *Schema.xml* | Liste tanımları için şema dosyası. Daha fazla bilgi için bkz. [Yapı Taşı: Listeler ve Belge Kitaplıkları ve](/previous-versions/office/developer/sharepoint-2010/ee534985(v=office.14)) [Schema.xml. ](/previous-versions/office/developer/sharepoint-2010/ms459356(v=office.14)) |
| *.webpart* | Web *Bölümü tanım* dosyası. Bu dosya bir Web Bölümü için özellik ayarlarını içerir. Daha fazla bilgi için bkz. [Building Block: Web Bölümleri.](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)) |
| *Ascx* | Bir ASP.NET UserControl dosyası. Bu dosya, bir Görsel Web Bölümü kullanıcı arabirimini tanımlar. |
| *Aspx* | Bir ASP.NET sayfası dosyası. Bu dosya, bir uygulama sayfasını tanımlayan XML işaretlemesini içerir. |
| *.cs* veya *.vb* dosyaları | Bu kod dosyaları, Visual C# SharePoint veya uygulama sayfaları, Web bölümleri ve iş akışları gibi Visual Basic kodlarından erişilebilen bir programlama modeline sahip olan özelleştirme özelleştirmelerinin davranışını tanımlar. |

## <a name="create-project-templates"></a>Proje şablonları oluşturma
 Bir proje şablonu SharePoint, her zaman gerekli olan bazı dosyalar ve belirli proje türleri tarafından kullanılmaktadır isteğe bağlı dosyalar vardır. Genellikle, SharePoint proje öğesi en az bir SharePoint içerir. Ancak bu gerekli değildir. Örneğin, yalnızca diğer projelerde oluşturulan SharePoint dağıtmak için kullanılmak üzere bir SharePoint proje şablonu tanımlayabilirsiniz.

 Bir proje öğesi türü tanımlamayı ve bunun için bir proje şablonu SharePoint gösteren bir kılavuz için bkz. Adım adım: Proje şablonuyla site sütunu proje öğesi [oluşturma, Bölüm 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).

 Aşağıdaki tabloda, bir proje şablonuna dahil edilecek SharePoint listele.

|Gerekli dosya|Açıklama|
|-------------------|-----------------|
|*Bir .vstemplate* dosyası|Bu dosya Visual Studio Yeni Uygulama iletişim kutusunda şablonu görüntülemek ve şablondan proje **oluşturmak Project** gereken bilgileri sağlar. Daha fazla bilgi için [bkz. Visual Studio Meta Veri Dosyaları.](/previous-versions/visualstudio/visual-studio-2010/xsxc3ete\(v\=vs.100\))|
|*.csproj* veya *.vbproj* dosyası|Bu, proje dosyasıdır. Projenin içeriğini ve yapılandırma ayarlarını tanımlar.|
|*Package.package*|Bu dosya, projenin dağıtım paketini tanımlar. Projeniz için çözüm paketini özelleştirmek üzere Paket Tasarımcısı'Visual Studio çözüm paketiyle ilgili verileri bu dosyada depolar.<br /><br /> Özel bir SharePoint proje şablonu oluştururken *Package.package* dosyasına yalnızca gereken en düşük içeriği dahil etmek ve proje şablonuyla ilişkili bir uzantıda ad alanı içinde API'leri kullanarak çözüm paketini <xref:Microsoft.VisualStudio.SharePoint.Packages> yapılandırmanızı öneririz. Bunu yaparsanız, proje şablonunuz Package.package dosyasının yapısında gelecekte yapılan *değişikliklerden korunur.* Yalnızca gerekli en düşük içeriğe sahip *bir Package.package* dosyası oluşturma örneği için bkz. Adım adım: Proje şablonuyla site sütunu proje öğesi [oluşturma, Bölüm 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).<br /><br /> *Package.package* dosyasını doğrudan değiştirmek için *%Program Files (x86)%\Microsoft Visual Studio 11.0\Xml\Schemas\PackageModelSchema.xsd* konumundaki şemayı kullanarak içeriği doğruabilirsiniz.|
|*Package.Template.xml*|Bu dosya, projeden oluşturulan SharePoint çözüm *paketi*(*.wsp*) için çözüm bildirim dosyası (manifest.xml) için temel sağlar. Proje türü kullanıcıları tarafından değişmesi amaçlanan bir davranış belirtmek için bu dosyaya içerik ebilirsiniz. Daha fazla bilgi için bkz. [Yapı Taşı: Çözümler](/previous-versions/office/developer/sharepoint-2010/ee537008(v=office.14)) ve [Çözüm Şeması.](/sharepoint/dev/schema/solution-schema)<br /><br /> Projeden bir çözüm paketi derlemek Visual Studio *Package.package içeriğini* vePackage.Template.xml *çözüm* bildirim dosyasıyla birleşiyor. Çözüm paketleri oluşturma hakkında daha fazla bilgi için, [bkz. How to: Create a SharePoint Solution Package by using MSBuild görevleri.](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)|

 Aşağıdaki tabloda, proje şablonuna dahil edilecek isteğe bağlı dosyalar liste almaktadır.

|İsteğe bağlı dosya|Açıklama|
|-------------------|-----------------|
|SharePoint proje öğeleri|Proje öğesi türlerini tanımlayan bir veya daha fazla .spdata SharePoint dahilebilirsiniz. Her *.spdata* dosyasının, proje şablonuyla VSIX paketine dahil edilen bir uzantı <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> derlemesinde eşleşen bir uygulaması olması gerekir. Daha fazla bilgi için [bkz. Öğe şablonları oluşturma.](#create-item-templates)<br /><br /> Genellikle, SharePoint proje öğesi en az bir SharePoint içerir. Ancak bu gerekli değildir.|
|*\<featureName>.feature*|Bu dosya, SharePoint proje öğelerini grup için kullanılan bir Özel durum özelliği tanımlar. Projeniz içinde bir Özelliği özelleştirmek için Özellik Tasarımcısı'Visual Studio özellikle ilgili verileri bu dosyada depolar. Proje öğelerini farklı Özellikler olarak gruplasanız, birden çok *.feature dosyası* dahilebilirsiniz.<br /><br /> Özel bir SharePoint proje şablonu oluştururken, *her bir .feature* dosyasına yalnızca gereken en düşük içeriği eklemenizi ve proje şablonuyla ilişkili bir uzantıda ad alanı içinde API'leri kullanarak Özellikleri <xref:Microsoft.VisualStudio.SharePoint.Features> yapılandırmanızı öneririz. Bunu yaparsanız, proje şablonunuz gelecekteki .feature dosyasının yapısına yapılan *değişikliklerden korunur.* Yalnızca gerekli en düşük içeriğe sahip *bir .feature* dosyası oluşturma örneği için bkz. Adım adım: Proje şablonuyla site sütunu proje öğesi [oluşturma, Bölüm 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).<br /><br /> bir *. feature* dosyasını doğrudan değiştirmek istiyorsanız, *% Program Files (x86)% \ Microsoft Visual Studio 11.0 \ xml\schemas\featuremodelschema.exe. xsd* konumundaki şemayı kullanarak içeriği doğrulayabilirsiniz.|
|*\<featureName>.Template.xml*|Bu dosya, projeden oluşturulan her bir özellik için özellik bildirim dosyası (*Feature.xml*) temelini sağlar. Proje türü kullanıcıları tarafından değiştirilmesi amaçlanmayan bazı davranışları belirtmek istiyorsanız bu dosyaya içerik ekleyebilirsiniz. Daha fazla bilgi için bkz. [Yapı bloğu: Özellikler](/previous-versions/office/developer/sharepoint-2010/ee537350(v=office.14)) ve [Feature.xml](/sharepoint/dev/schema/feature-xml-files) dosyaları.<br /><br /> projeden bir çözüm paketi oluşturduğunuzda, Visual Studio her bir *\<featureName> . feature* dosyası ve *\<featureName>.Template.xml* dosyanın içeriğini bir özellik bildirim dosyası olarak birleştirir. çözüm paketleri oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: MSBuild görevlerini kullanarak SharePoint çözüm paketi oluşturma](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md).|

## <a name="create-wizards-for-item-templates-and-project-templates"></a>Öğe şablonları ve proje şablonları için sihirbaz oluşturma
 SharePoint proje öğesi türünü tanımladıktan ve bir öğe veya proje şablonuyla ilişkilendirdikten sonra, bir sihirbaz de oluşturabilirsiniz. sihirbaz, bir geliştirici bir projeye SharePoint proje öğesi eklemek için öğe şablonunu kullandığında veya bir geliştirici, SharePoint proje öğesini içeren yeni bir proje oluşturmak için proje şablonunu kullandığında görüntülenir. sihirbaz, geliştiricilerden bilgi toplamak ve yeni SharePoint proje öğesini başlatmak için kullanılabilir.

 Öğe şablonları ve proje şablonları için sihirbazları oluşturmayı gösteren izlenecek yollar için bkz [. Izlenecek yol: bir öğe şablonuyla özel eylem projesi öğesi oluşturma, Bölüm 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md) ve [izlenecek yol: proje şablonu, Bölüm 2 ile bir site sütunu proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).

## <a name="see-also"></a>Ayrıca bkz.

- [özel SharePoint proje öğesi türlerini tanımlama](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [İzlenecek yol: öğe şablonu, Bölüm 1 ile özel bir eylem proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [İzlenecek yol: öğe şablonu, Bölüm 2 ile özel bir eylem proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)
- [İzlenecek yol: proje şablonu, Bölüm 1 ile bir site sütunu proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [İzlenecek yol: proje şablonu, Bölüm 2 ile bir site sütunu proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)
- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)
