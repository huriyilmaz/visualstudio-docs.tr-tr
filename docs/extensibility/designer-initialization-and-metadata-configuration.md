---
title: Tasarımcı Başlatma ve Meta Veri Yapılandırma | Microsoft Docs
description: Visual Studio SDK'sını kullanarak tasarımcının veya tasarımcı bileşeninin başlatma ve meta verilerini VSPackage ile denetlemeyi nasıl kolaylaştırıyor?
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], initializing
- designers [Visual Studio SDK], configuring metadata
ms.assetid: f7fe9a7e-f669-4642-ad5d-186b2e6e6ec9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 2954d551b1a35c2de5e951111e746227aa9987a5
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726953"
---
# <a name="designer-initialization-and-metadata-configuration"></a>Tasarımcı başlatma ve meta veri yapılandırması

Bir tasarımcı veya tasarımcı bileşeniyle ilişkili meta verilerin ve filtre özniteliklerinin işlemesi, uygulamaların belirli bir tasarımcı tarafından farklı nesneleri (veri yapıları, sınıflar veya grafik varlıkları gibi) işlemek için hangi araçların kullandırıldığında, tasarımcının ne zaman kullanılabilir olduğunu ve Visual Studio IDE'nin tasarımcıyı destekleyecek şekilde <xref:System.Type> nasıl yapılandırıldığından (örneğin, hangi Araç Kutusu kategorisi veya sekmesinin kullanılabilir olduğunu) tanımlamaya yönelik bir mekanizma sağlar. 

, tasarımcının veya tasarımcı bileşeninin başlatma ve meta verilerini VSPackage ile işlemesini kolaylaştıran [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] çeşitli mekanizmalar sağlar.

## <a name="initialize-metadata-and-configuration-information"></a>Meta verileri ve yapılandırma bilgilerini başlatma
 Bunlar isteğe bağlı olarak yüklendiğinden, VSPackage'lar tasarımcı örneği Visual Studio önce bu ortam tarafından yüklenmemiş olabilir. Bu nedenle VSPackage'lar, oluşturma sırasında bir tasarımcı veya tasarımcı bileşenini yapılandırmak için bir olayı işlemek üzere standart mekanizmayı <xref:System.ComponentModel.Design.IDesignerEventService.DesignerCreated> kullanamaz. Bunun yerine VSPackage, arabirimin bir örneğini uygulayan ve tasarım yüzeyi uzantıları olarak adlandırılan özelleştirmeler sağlamak <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> için kendisini kaydettirmektedir.

### <a name="customize-initialization"></a>Başlatmayı özelleştirme

Tasarımcı, bileşen veya tasarımcı yüzeyini özelleştirme işlemi şunları içerir:

1. Tasarımcı meta verilerini değiştirme ve belirli bir veriye erişim veya <xref:System.Type> dönüştürmeyi etkili bir şekilde değiştirme.

    Bu genellikle veya mekanizmaları <xref:System.Drawing.Design.UITypeEditor> <xref:System.ComponentModel.TypeConverter> aracılığıyla yapılır.

    Örneğin, tabanlı tasarımcılar başlatılmış olduğunda, Visual Studio ortamı, dosya sistemi yerine bit eşlemleri almak üzere kaynak yöneticisini kullanmak üzere tasarımcı ile kullanılan nesneler için <xref:System.Windows.Forms> <xref:System.Drawing.Design.UITypeEditor> öğesini <xref:System.Web.UI.WebControls.Image> kullanır.

2. Örneğin, olaylara abone olarak veya proje yapılandırma bilgilerini elde ederek ortamla tümleştirme. Proje yapılandırma bilgilerini edinebilirsiniz ve arabirimini edinerek olaylara abone <xref:System.ComponentModel.Design.ITypeResolutionService> olabilirsiniz.

3. Uygun Araç Kutusu kategorilerini **etkinleştirerek** veya sınıfın bir örneğini tasarımcıya uygulayarak tasarımcının uygulanabilirlik kısıtlaması ile <xref:System.ComponentModel.ToolboxItemFilterAttribute> kullanıcı ortamının değiştirilmesi.

### <a name="designer-initialization-by-a-vspackage"></a>VSPackage tarafından tasarımcı başlatma

VSPackage, tasarımcı başlatmayı şu şekilde işlemeli:

1. sınıfını uygulayan bir nesne <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> oluşturma.

   > [!NOTE]
   > sınıf <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> hiçbir zaman sınıfıyla aynı nesne üzerinde <xref:Microsoft.VisualStudio.Shell.Package> uygulanmaz.

2. <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>VSPackage'ın tasarımcı uzantıları için destek sağlama olarak uygulayan sınıfı kaydetme. VSPackage'ın uygulamasını sağlayan sınıfına , ve örneklerini  <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute> <xref:Microsoft.VisualStudio.Shell.ProvideObjectAttribute> uygulayarak <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> sınıfını <xref:Microsoft.VisualStudio.Shell.Package> kaydettirin.

Tasarımcı veya tasarımcı bileşeni oluşturulduğunda, Visual Studio gerekir:

- Kayıtlı her tasarım yüzeyi uzantısı sağlayıcısına erişer.

- Her tasarım yüzeyi uzantısı sağlayıcısının nesnesinin örneğini oluşturur ve <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> başlatıyor.

- Her tasarım yüzeyi uzantısı sağlayıcısının yöntemini <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnDesignerCreated%2A> veya yöntemini <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnComponentCreated%2A> (uygun şekilde) çağıran.

Nesneyi <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> VSPackage'ın bir üyesi olarak uygulamak için şunları anlamanız önemlidir:

- Bu Visual Studio, belirli bir sağlayıcının hangi meta veriler veya diğer yapılandırma ayarları üzerinde `DesignSurfaceExtension` herhangi bir denetim sağlamaz. İki veya daha fazla sağlayıcının aynı tasarımcı özelliğini çakışan yollarla değiştirmesi ve son `DesignSurfaceExtension` değişikliğin kesin olması mümkündür. Son uygulanan değişiklik belirsizdir.

- Nesnesinin örneklerini bu uygulamaya uygulayarak nesnesinin uygulamasını <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> belirli tasarımcılarla açıkça <xref:System.ComponentModel.ToolboxItemFilterAttribute> kısıtlamak mümkündür. Araç kutusu öğesi **filtreleme hakkında daha** fazla bilgi için, bkz. ve <xref:System.ComponentModel.ToolboxItemFilterAttribute> <xref:System.ComponentModel.ToolboxItemFilterType> .

## <a name="additional-metadata-provisioning"></a>Ek meta veri sağlama

VSPackage, tasarım zamanından farklı bir tasarımcı veya tasarımcı bileşeninin yapılandırmasını değiştirebilir.

sınıfı <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> program aracılığıyla kullanılabilir veya tasarımcı sağlayan bir VSPackage'a uygulanabilir.

Bir tasarım yüzeyinde <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> oluşturulan bileşenlerin meta verilerini değiştirmek için sınıfının bir örneği kullanılır. Örneğin, nesneler tarafından kullanılan varsayılan özellik tarayıcısını özel <xref:System.Windows.Forms.CommonDialog> bir özellik tarayıcısıyla değiştirebilirsiniz.

VSPackage'ın uygulamasına uygulanan bir örneği tarafından <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> sağlanan değişiklikler iki <xref:Microsoft.VisualStudio.Shell.Package> kapsamdan birini olabilir:

- Genel -- bir bileşenin tüm yeni örnekleri için

- Yerel -- yalnızca geçerli VSPackage tarafından sağlanan tasarım yüzeyinde oluşturulan bileşenin örneğiyle ilgili.

`IsGlobal` <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> VsPackage'ın uygulamasına uygulanan örneğin özelliği bu <xref:Microsoft.VisualStudio.Shell.Package> kapsamı belirler.

nesnesinin özelliği olarak ayarlanmış bir uygulamasına özniteliğini uygulamak, aşağıda olduğu gibi tüm ortam için <xref:Microsoft.VisualStudio.Shell.Package> <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute.IsGlobal%2A> <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> `true` tarayıcıyı Visual Studio değiştirir:

`[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=true`  `)]`

`internal class MyPackage : Package {}`

Genel bayrak olarak ayarlanmışsa, meta veri değişikliği geçerli VSPackage tarafından desteklenen `false` geçerli tasarımcıya yerel olarak değişir:

`[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=false`  `)]`

`internal class MyPackage : Package {}`

> [!NOTE]
> Tasarım yüzeyi yalnızca bileşen oluşturmayı destekler ve bu nedenle yalnızca bileşenlerin yerel meta verileri olabilir. Yukarıdaki örnekte, bir nesnesinin özelliği gibi bir özelliği değiştirmeye `Color` girişiminde bulunduk. genel bayrağı için geçirildi ise, tasarımcı hiçbir zaman gerçekten bir `false` `CustomBrowser` örneği oluşturmaz çünkü hiçbir zaman `Color` görünmez. Genel bayrağı olarak `false` ayarlama, denetimler, süreerler ve iletişim kutuları gibi bileşenler için kullanışlıdır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>
- <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>
- <xref:System.ComponentModel.ToolboxItemFilterType>
- [Tasarım zamanı desteğini genişletme](/previous-versions/37899azc(v=vs.140))