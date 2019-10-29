---
title: SharePoint proje öğeleri için öğe şablonları/proje şablonları
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 65bbd58bf9b3e0b399603a083615daccc382a98f
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72981169"
---
# <a name="create-item-templates-and-project-templates-for-sharepoint-project-items"></a>SharePoint proje öğeleri için öğe şablonları ve proje şablonları oluşturma

Özel bir SharePoint proje öğesi türü tanımladığınızda, bunu bir öğe şablonuyla veya proje şablonuyla ilişkilendirebilirsiniz. Bu ilişki, diğer geliştiricilerin Visual Studio 'daki Proje öğesini kullanmasına izin verir. Şablon için bir sihirbaz da oluşturabilirsiniz.

Örneğin, Visual Studio bir SharePoint sitesine alan eklemek için bir proje şablonu veya öğe şablonu içermez. Bir alanı temsil eden bir SharePoint proje öğesi türü tanımlayabilir ve ardından diğer geliştiricilerin bir SharePoint projesine alan öğesi eklemek için kullanabileceği bir öğe şablonu oluşturabilirsiniz. Ya da, geliştiricilerin alan öğesine sahip yeni bir SharePoint projesi oluşturabilmesi için bir proje şablonu oluşturabilirsiniz. Her iki durumda da, geliştiriciler şablonunuzu kullandıklarında görüntülenen bir sihirbaz da sağlayabilirsiniz. Bu sihirbaz, yeni öğeyi veya projeyi yapılandırmak için geliştiricilerden bilgi toplayabilir.

Öğe şablonları ve proje şablonları, Visual Studio tarafından bir proje öğesi veya proje oluşturmak için kullanılan dosyaları içeren *. zip* dosyalarıdır. Öğe şablonlarının ve proje şablonlarının temelleri hakkında daha fazla bilgi için bkz. [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md).

## <a name="create-item-templates"></a>Öğe şablonları oluşturma
 Bir SharePoint proje öğesi için bir öğe şablonu oluşturduğunuzda, her zaman gerekli olan bazı dosyalar ve belirli proje öğesi türleri tarafından kullanılabilen isteğe bağlı dosyalar vardır. Bir SharePoint proje öğesi türü tanımlama ve onun için bir öğe şablonu oluşturma hakkında yönergeler için bkz. [Izlenecek yol: öğe şablonu, Bölüm 1 ile özel eylem projesi öğesi oluşturma](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).

 Aşağıdaki tabloda bir SharePoint proje öğesi için bir öğe şablonu oluşturmak üzere gerekli dosyalar listelenmektedir.

|Gerekli dosya|Açıklama|
|-------------------|-----------------|
|Bir *. spdata* dosyası|Bu XML dosyası, proje öğesinin içeriğini ve varsayılan davranışını belirtir. Bu dosya, öğe şablonuna dahil olmalıdır. *. Spdata* dosyalarının içerikleri hakkında daha fazla bilgi için bkz. [SharePoint proje öğesi şema başvurusu](../sharepoint/sharepoint-project-item-schema-reference.md).|
|*. Vstemplate* dosyası.|Bu dosya, Visual Studio 'Yu **Yeni öğe Ekle** iletişim kutusunda şablonu göstermek ve şablondan bir proje öğesi oluşturmak için gereken bilgileri sağlar. Bu dosya, öğe şablonuna dahil olmalıdır. Daha fazla bilgi için bkz. [Visual Studio şablon meta verileri dosyaları](/previous-versions/visualstudio/visual-studio-2010/xsxc3ete\(v\=vs.100\)).|
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> arabirimini uygulayan bir Visual Studio Uzantı derlemesi.|Bu derleme proje öğesinin çalışma zamanı davranışını tanımlar. Bu derlemenin, öğe şablonuyla VSıX paketine dahil olması gerekir. Daha fazla bilgi için bkz. [Visual Studio 'Da SharePoint araçları için](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md) [özel SharePoint proje öğesi türleri tanımlama](../sharepoint/defining-custom-sharepoint-project-item-types.md) ve uzantıları dağıtma.|

 Aşağıdaki tabloda, öğe şablonuna eklenebilecek en sık kullanılan isteğe bağlı dosyaların bazıları listelenmiştir. Bazı proje öğesi türleri burada listelenmeyen diğer dosyaları gerektirebilir.

| İsteğe bağlı dosya | Açıklama |
|----------------------| - |
| *Elements. xml* | Bir *özellik öğesi* dosyası. Bu dosya, proje öğesi tarafından oluşturulan özelleştirmenin Kullanıcı arabirimini ve davranışını tanımlar. Liste örnekleri, içerik türleri veya özel eylemler gibi her özelleştirme türünün, bu dosyanın içeriğini tanımlayan farklı bir şeması vardır. Daha fazla bilgi için bkz. [Yapı bloğu: Özellikler](/previous-versions/office/developer/sharepoint-2010/ee537350(v=office.14)) ve [özellik şemaları](/previous-versions/office/developer/sharepoint-2010/ms414322(v=office.14)). |
| *Schema. xml* | Liste tanımlarının şema dosyası. Daha fazla bilgi için bkz. [Yapı bloğu: listeler ve belge kitaplıkları](/previous-versions/office/developer/sharepoint-2010/ee534985(v=office.14)) ve [Schema. xml](/previous-versions/office/developer/sharepoint-2010/ms459356(v=office.14)). |
| *. WebPart* | Bir *Web Bölümü tanım* dosyası. Bu dosya, bir Web bölümü için özellik ayarlarını içerir. Daha fazla bilgi için bkz. [yapı taşı: Web bölümleri](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)). |
| *. ascx* | Bir ASP.NET UserControl dosyası. Bu dosya, bir görsel web bölümünün Kullanıcı arabirimini tanımlar. |
| *.aspx* | Bir ASP.NET sayfa dosyası. Bu dosya, bir uygulama sayfasını tanımlayan XML biçimlendirmesi içerir. |
| *. cs* veya *. vb* dosyaları | Bu kod dosyaları, Visual C# veya Visual Basic kodundan erişilebilen, uygulama sayfaları, Web bölümleri ve iş akışları gibi bir programlama modeline sahip SharePoint özelleştirmelerinin davranışını tanımlar. |

## <a name="create-project-templates"></a>Proje şablonları oluşturma
 Bir SharePoint proje şablonu oluşturduğunuzda, her zaman gereken bazı dosyalar ve belirli proje türleri tarafından kullanılabilen isteğe bağlı dosyalar vardır. Genellikle, SharePoint projeleri en az bir SharePoint proje öğesi içerir. Ancak, bu gerekli değildir. Örneğin, yalnızca diğer projelerde oluşturulan SharePoint çözümlerini dağıtmak için kullanılması amaçlanan bir SharePoint proje şablonu tanımlayabilirsiniz.

 Bir SharePoint proje öğesi türü tanımlama ve onun için bir proje şablonu oluşturma hakkında yönergeler için bkz. [Izlenecek yol: proje şablonu, Bölüm 1 ile bir site sütunu oluşturma proje öğesi](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).

 Aşağıdaki tabloda bir SharePoint proje şablonuna dahil olması gereken dosyalar listelenmektedir.

|Gerekli dosya|Açıklama|
|-------------------|-----------------|
|Bir *. vstemplate* dosyası|Bu dosya, Visual Studio 'Yu **Yeni proje** iletişim kutusunda şablonu göstermek ve şablondan bir proje oluşturmak için gereken bilgileri sağlar. Daha fazla bilgi için bkz. [Visual Studio şablon meta verileri dosyaları](/previous-versions/visualstudio/visual-studio-2010/xsxc3ete\(v\=vs.100\)).|
|Bir *. csproj* veya *. vbproj* dosyası|Bu proje dosyasıdır. Projenin içerik ve yapılandırma ayarlarını tanımlar.|
|*Package. Package*|Bu dosya, projenin dağıtım paketini tanımlar. Projeniz için çözüm paketini özelleştirmek üzere Paket Tasarımcısını kullandığınızda, Visual Studio bu dosyadaki çözüm paketiyle ilgili verileri depolar.<br /><br /> Özel bir SharePoint proje şablonu oluşturduğunuzda, *Package. Package* dosyasına yalnızca gerekli en az içeriği dahil etmenizi ve çözüm paketini, bir uzantıdaki <xref:Microsoft.VisualStudio.SharePoint.Packages> ad alanındaki API 'leri kullanarak yapılandırmanızı öneririz. Proje şablonuyla ilişkilendirilir. Bunu yaparsanız, proje şablonunuz *Package. Package* dosyasının yapısına gelecekteki değişikliklere karşı korunur. Yalnızca gereken en az içeriğe sahip bir *Package. Package* dosyası oluşturmayı gösteren bir örnek için bkz. [izlenecek yol: proje şablonu, Bölüm 1 ile bir site sütunu oluşturma proje öğesi](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).<br /><br /> *Package. Package* dosyasını doğrudan değiştirmek istiyorsanız, *% Program Files (x86)% \ Microsoft Visual Studio 11.0 \ Xml\schemas\packagemodelschema.exe*' konumundaki şemayı kullanarak içeriği doğrulayabilirsiniz.|
|*Package. Template. xml*|Bu dosya, projeden oluşturulan SharePoint çözüm paketi ( *. wsp*) için çözüm bildirim dosyası (*manifest. xml*) temelini sağlar. Proje türü kullanıcıları tarafından değiştirilmesi amaçlanmayan bazı davranışları belirtmek istiyorsanız bu dosyaya içerik ekleyebilirsiniz. Daha fazla bilgi için bkz. [Yapı bloğu: çözümler](/previous-versions/office/developer/sharepoint-2010/ee537008(v=office.14)) ve [çözüm şeması](/sharepoint/dev/schema/solution-schema).<br /><br /> Projeden bir çözüm paketi oluşturduğunuzda, Visual Studio *Package. Package* ve *Package. Template. xml* dosyalarının içeriğini çözüm bildirim dosyasına birleştirir. Çözüm paketleri oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: MSBuild görevlerini kullanarak bir SharePoint çözüm paketi oluşturma](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md).|

 Aşağıdaki tabloda, proje şablonunda yer alan isteğe bağlı dosyalar listelenmektedir.

|İsteğe bağlı dosya|Açıklama|
|-------------------|-----------------|
|SharePoint proje öğeleri|SharePoint proje öğesi türlerini tanımlayan bir veya daha fazla. spdata dosyası ekleyebilirsiniz. Her *. spdata* dosyası, proje şablonuyla VSIX paketine dahil edilen bir uzantı derlemesinde eşleşen bir <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> uygulamasına sahip olmalıdır. Daha fazla bilgi için bkz. [öğe şablonları oluşturma](#create-item-templates).<br /><br /> Genellikle, SharePoint projeleri en az bir SharePoint proje öğesi içerir. Ancak, bu gerekli değildir.|
|*\<featureName >. Feature*|Bu dosya, dağıtım için birkaç proje öğesini gruplandırmak üzere kullanılan bir SharePoint özelliğini tanımlar. Projenizdeki bir özelliği özelleştirmek için özellik tasarımcısını kullandığınızda, Visual Studio bu dosyadaki özellik hakkındaki verileri depolar. Proje öğelerini farklı özelliklere gruplandırmak isterseniz, birden fazla *. feature* dosyası ekleyebilirsiniz.<br /><br /> Özel bir SharePoint proje şablonu oluşturduğunuzda, her bir *. feature* dosyasına yalnızca gerekli en az içeriği dahil etmenizi ve bu özellikleri, ile ilişkili bir uzantıdaki <xref:Microsoft.VisualStudio.SharePoint.Features> ad alanındaki API 'leri kullanarak yapılandırmanızı öneririz. Proje şablonu. Bunu yaparsanız, proje şablonunuz daha sonra *. feature* dosyası yapısına karşı değişir. Yalnızca gerekli en az içeriğe sahip bir *. feature* dosyası oluşturmayı gösteren bir örnek için bkz. [izlenecek yol: proje şablonu, Bölüm 1 ile bir site sütunu oluşturma proje öğesi](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).<br /><br /> Bir *. feature* dosyasını doğrudan değiştirmek istiyorsanız, *% Program Files (x86)% \ Microsoft Visual Studio 11.0 \ Xml\schemas\featuremodelschema.exe. xsd*konumundaki şemayı kullanarak içeriği doğrulayabilirsiniz.|
|*\<featureName >. Template. xml*|Bu dosya, projeden oluşturulan her bir özellik için özellik bildirim dosyasının (*Feature. xml*) temelini sağlar. Proje türü kullanıcıları tarafından değiştirilmesi amaçlanmayan bazı davranışları belirtmek istiyorsanız bu dosyaya içerik ekleyebilirsiniz. Daha fazla bilgi için bkz. [Yapı bloğu: Özellikler](/previous-versions/office/developer/sharepoint-2010/ee537350(v=office.14)) ve [özellik. xml](/sharepoint/dev/schema/feature-xml-files) dosyaları.<br /><br /> Projeden bir çözüm paketi oluşturduğunuzda, Visual Studio her bir *\<featureName >. feature* dosyası ve *\<featureName > içeriğini birleştirir. Şablon. xml* dosyalarını bir özellik bildirim dosyasına ekleyin. Çözüm paketleri oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: MSBuild görevlerini kullanarak bir SharePoint çözüm paketi oluşturma](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md).|

## <a name="create-wizards-for-item-templates-and-project-templates"></a>Öğe şablonları ve proje şablonları için sihirbaz oluşturma
 Bir SharePoint proje öğesi türünü tanımladıktan ve bir öğe ya da proje şablonuyla ilişkilendirdikten sonra, bir sihirbaz de oluşturabilirsiniz. Sihirbaz, bir geliştirici SharePoint proje öğesini bir projeye eklemek için öğe şablonunu kullandığında veya bir geliştirici, SharePoint proje öğesini içeren yeni bir proje oluşturmak için proje şablonunu kullandığında görüntülenir. Sihirbaz, geliştiricilerden bilgi toplamak ve yeni SharePoint proje öğesini başlatmak için kullanılabilir.

 Öğe şablonları ve proje şablonları için sihirbazları oluşturmayı gösteren izlenecek yollar için bkz [. Izlenecek yol: bir öğe şablonuyla özel eylem projesi öğesi oluşturma, Bölüm 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md) ve [izlenecek yol: proje ile bir site sütunu proje öğesi oluşturma Şablon, Bölüm 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Özel SharePoint proje öğesi türlerini tanımlama](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [İzlenecek yol: öğe şablonu, Bölüm 1 ile özel bir eylem proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [İzlenecek yol: öğe şablonu, Bölüm 2 ile özel bir eylem proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)
- [İzlenecek yol: proje şablonu, Bölüm 1 ile bir site sütunu proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [İzlenecek yol: proje şablonu, Bölüm 2 ile bir site sütunu proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)
- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)
