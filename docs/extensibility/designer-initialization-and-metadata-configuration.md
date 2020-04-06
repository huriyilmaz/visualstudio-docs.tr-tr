---
title: Tasarımcı Başlatma ve Metaveri Yapılandırması | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], initializing
- designers [Visual Studio SDK], configuring metadata
ms.assetid: f7fe9a7e-f669-4642-ad5d-186b2e6e6ec9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e876dd9e6fa95bbe180d1737bc8c4911f16e1e9a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712222"
---
# <a name="designer-initialization-and-metadata-configuration"></a>Tasarımcı başlatma ve meta veri yapılandırması

Tasarımcı veya tasarımcı bileşeni ile ilişkili meta veri ve filtre özniteliklerinin manipülasyonu, tasarımcı kullanılabilir olduğunda <xref:System.Type> belirli bir tasarımcı tarafından farklı nesneleri (veri yapıları, sınıflar veya grafik varlıklar gibi) işlemek için hangi araçların kullanıldığını ve Visual Studio IDE'nin tasarımcıyı destekleyecek şekilde nasıl yapılandırılacağını (örneğin, **araç kutusu** kategorisi veya sekmesinin kullanılabilir olduğunu) tanımlayan uygulamalar için bir mekanizma sağlar.

Bir [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] tasarımcının veya tasarımcı bileşeninin başlatılmasını ve meta verilerinin bir VSPackage tarafından manipüle ediletilmesinin denetimini kolaylaştırmak için çeşitli mekanizmalar sağlar.

## <a name="initialize-metadata-and-configuration-information"></a>Meta verileri ve yapılandırma bilgilerini başlatma
 İsteğe bağlı olarak yüklendikleri için VSPackages, bir tasarımcının anında yüklenmeden önce Visual Studio ortamı tarafından yüklenmemiş olabilir. Bu nedenle, VSPackages bir <xref:System.ComponentModel.Design.IDesignerEventService.DesignerCreated> olay işlemek için oluşturma, bir tasarımcı veya tasarımcı bileşeni yapılandırmak için standart mekanizma kullanamazsınız. Bunun yerine, VSPackage arabirimin <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> bir örneğini uygular ve tasarım yüzeyi uzantıları olarak adlandırılan özelleştirmeler sağlamak için kendisini kaydeder.

### <a name="customize-initialization"></a>Başlatmayı özelleştirme

Bir tasarımcıyı, bileşeni veya tasarımcı yüzeyini özelleştirmek şunları içerir:

1. Tasarımcı meta verilerini değiştirme ve belirli <xref:System.Type> bir verilere nasıl erişilebildiğini veya dönüştürüldüğünü etkili bir şekilde değiştirmek.

    Bu genellikle <xref:System.Drawing.Design.UITypeEditor> veya <xref:System.ComponentModel.TypeConverter> mekanizmaları aracılığıyla yapılır.

    Örneğin, <xref:System.Windows.Forms>tabanlı tasarımcılar baş harfe döndüğünde, Visual Studio ortamı, dosya sistemi yerine bit eşlemleri elde etmek <xref:System.Drawing.Design.UITypeEditor> için kaynak yöneticisini kullanmak için tasarımcıyla birlikte kullanılan nesneler için <xref:System.Web.UI.WebControls.Image> değiştirir.

2. Örneğin, olaylara abone olarak veya proje yapılandırma bilgilerini alarak ortamla bütünleştirme. Arayüz alarak proje yapılandırma bilgilerini alabilir ve <xref:System.ComponentModel.Design.ITypeResolutionService> etkinliklere abone olabilirsiniz.

3. Uygun **Araç Kutusu** kategorilerini etkinleştirerek veya <xref:System.ComponentModel.ToolboxItemFilterAttribute> sınıfın bir örneğini tasarımcıya uygulayarak tasarımcının uygulanabilirliğini kısıtlayarak kullanıcı ortamının değiştirilmesi.

### <a name="designer-initialization-by-a-vspackage"></a>VSPackage ile tasarımcı başlatma

Bir VSPackage tarafından tasarımcı başlatma ele almalıdır:

1. <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> Sınıfı uygulayan bir nesne oluşturma.

   > [!NOTE]
   > Sınıf, <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> <xref:Microsoft.VisualStudio.Shell.Package> sınıfla aynı nesne üzerinde asla uygulanmamalıdır.

2. VSPackage'ın tasarımcı <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> uzantıları için destek sağlamak olarak uygulayan sınıfa kaydolmak. VSPackage'ın uygulanmasını sağlayan <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>sınıfa <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> ve vspackage'ın uygulamalarını sağlayan sınıfa , ve <xref:Microsoft.VisualStudio.Shell.Package> <xref:Microsoft.VisualStudio.Shell.ProvideObjectAttribute>' örneklerini uygulayarak sınıfa kaydolun.

Bir tasarımcı veya tasarımcı bileşeni oluşturulduğunda, Visual Studio ortamı:

- Her kayıtlı tasarım yüzeyi uzantısı sağlayıcısına erişir.

- Her tasarım yüzey uzantısı sağlayıcısının <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> nesnesinin bir örneğini anında laştırır ve ortaya çıkar.

- Her tasarım yüzey uzantısı <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnDesignerCreated%2A> sağlayıcısının <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnComponentCreated%2A> yöntemini veya yöntemini (uygun olarak) çağırır.

Nesneyi <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> bir VSPackage üyesi olarak uygularken, aşağıdakileri anlamak önemlidir:

- Visual Studio ortamı, belirli `DesignSurfaceExtension` bir sağlayıcının hangi meta veri veya diğer yapılandırma ayarlarını değiştirip değiştirmediği üzerinde herhangi bir denetim sağlamaz. İki veya daha fazla `DesignSurfaceExtension` sağlayıcının aynı tasarımcı özelliğini çakışan şekillerde değiştirmesi ve son değişikliğin kesin olması mümkündür. En son hangi değişikliğin uygulandığı belirsizdir.

- Bu uygulamaya örneklerini <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> <xref:System.ComponentModel.ToolboxItemFilterAttribute> uygulayarak nesnenin uygulanmasını belirli tasarımcılarla açıkça kısıtlamak mümkündür. **Toolbox** öğesi filtreleme hakkında daha <xref:System.ComponentModel.ToolboxItemFilterAttribute> fazla <xref:System.ComponentModel.ToolboxItemFilterType>bilgi için bkz.

## <a name="additional-metadata-provisioning"></a>Ek meta veri sağlama

VSPackage, tasarım zamanı dışında bir tasarımcı veya tasarımcı bileşeninin yapılandırmasını değiştirebilir.

Sınıf <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> programlı olarak kullanılabilir veya bir tasarımcı sağlayan bir VSPackage uygulanabilir.

<xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> Sınıfın bir örneği, tasarım yüzeyinde oluşturulan bileşenlerin meta verilerini değiştirmek için kullanılır. Örneğin, nesneler tarafından <xref:System.Windows.Forms.CommonDialog> kullanılan varsayılan özellik tarayıcısı özel bir özellik tarayıcısı ile değiştirilebilir.

VSPackage'ın uygulanmasına <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> uygulanan bir örnek tarafından <xref:Microsoft.VisualStudio.Shell.Package> sağlanan değişiklikler iki kapsamdan birine sahip olabilir:

- Global -- belirli bir bileşenin tüm yeni örnekleri için

- Yerel -- yalnızca geçerli VSPackage tarafından sağlanan bir tasarım yüzeyinde oluşturulan bileşenin örneğine ilişkindir.

VSPackage uygulamasına uygulanan `IsGlobal` <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> örneğin özelliği bu <xref:Microsoft.VisualStudio.Shell.Package> kapsamı belirler.

Aşağıdaki <xref:Microsoft.VisualStudio.Shell.Package> gibi ayarlanan <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute.IsGlobal%2A> <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> `true`nesnenin özelliği ile bir uygulamaya öznitelik uygulanması, tüm Visual Studio ortamı için tarayıcı değiştirir:

`[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=true`  `)]`

`internal class MyPackage : Package {}`

Genel bayrak `false`ayarlanmışsa, meta veri değişikliği geçerli VSPackage tarafından desteklenen geçerli tasarımcı için yereldir:

`[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=false`  `)]`

`internal class MyPackage : Package {}`

> [!NOTE]
> Tasarım yüzeyi yalnızca bileşenleri oluşturmayı destekler ve bu nedenle yalnızca bileşenler yerel meta verilere sahip olabilir. Yukarıdaki örnekte, bir nesnenin `Color` özelliği gibi bir özelliği değiştirmeye çalışıyorduk. Eğer `false` küresel bayrak için geçirilirse, `CustomBrowser` tasarımcı asla görünmez, çünkü `Color`tasarımcı hiçbir zaman .'ın bir örneğini oluşturmaz. Genel bayrağı niçin `false` ayarla, denetimler, zamanlayıcılar ve iletişim kutuları gibi bileşenler için yararlıdır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>
- <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>
- <xref:System.ComponentModel.ToolboxItemFilterType>
- [Tasarım süresi desteğini genişletme](https://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)
