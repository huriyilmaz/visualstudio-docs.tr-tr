---
title: Tasarımcı başlatma ve meta veri yapılandırması | Microsoft Docs
description: Visual Studio SDK 'sının bir tasarımcının veya tasarımcı bileşeninin başlatma ve meta verisinin bir VSPackage denetimini nasıl kolaylaştırması gerektiğini öğrenin.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 9907298cf730d6e51c108dc92f633d0b50451f12
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996168"
---
# <a name="designer-initialization-and-metadata-configuration"></a>Tasarımcı başlatması ve meta veri yapılandırması

Bir tasarımcı veya tasarımcı bileşeniyle ilişkili meta veri ve filtre özniteliklerinin düzenlemesi, belirli bir tasarımcı tarafından farklı <xref:System.Type> nesneleri (veri yapıları, sınıflar veya grafik varlıklar gibi) işlemek için hangi araçların kullanıldığını, tasarımcı 'nın kullanılabilir olduğunu ve Visual STUDIO IDE 'nin tasarımcıyı destekleyecek şekilde nasıl yapılandırıldığını (örneğin, **araç kutusu** kategorisi veya sekmenin kullanılabildiği) tanımlamak için bir mekanizma sağlar.

, [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] Bir tasarımcının veya tasarımcı bileşeninin başlatılmasının denetimini ve meta verilerinin VSPackage tarafından düzenlenmesini kolaylaştırmak için çeşitli mekanizmalar sağlar.

## <a name="initialize-metadata-and-configuration-information"></a>Meta verileri ve yapılandırma bilgilerini başlatma
 İsteğe bağlı olarak yüklendiği için VSPackages, tasarımcı örneklemesinin öncesinde Visual Studio ortamı tarafından yüklenmemiş olabilir. Bu nedenle, VSPackages, bir olayı işlemek için kullanılan oluşturma sırasında tasarımcı veya Tasarımcı bileşeni yapılandırmak için standart mekanizmayı kullanamaz <xref:System.ComponentModel.Design.IDesignerEventService.DesignerCreated> . Bunun yerine, VSPackage arabirimin bir örneğini uygular <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> ve tasarım yüzeyi uzantıları olarak adlandırılan özelleştirmeler sağlamak için kendisini kaydeder.

### <a name="customize-initialization"></a>Başlatmayı özelleştirme

Tasarımcı, bileşen veya tasarımcı yüzeyini özelleştirme şunları içerir:

1. Tasarımcı meta verilerini değiştirme ve belirli bir şekilde nasıl <xref:System.Type> erişildiğini veya dönüştürüldüğünü değiştirme.

    Bu genellikle veya mekanizmaları aracılığıyla yapılır <xref:System.Drawing.Design.UITypeEditor> <xref:System.ComponentModel.TypeConverter> .

    Örneğin, <xref:System.Windows.Forms> -tabanlı tasarımcılar başlatıldığında, Visual Studio ortamı <xref:System.Drawing.Design.UITypeEditor> <xref:System.Web.UI.WebControls.Image> dosya sistemi yerine bit eşlemler elde etmek üzere Kaynak Yöneticisi 'ni kullanmak üzere Tasarımcı ile kullanılan nesneleri için değiştirir.

2. Örneğin, olaylara abone olarak veya proje yapılandırma bilgilerini alarak ortamla tümleştirme. Arabirimi alarak, proje yapılandırma bilgilerini alabilir ve olaylara abone olabilirsiniz <xref:System.ComponentModel.Design.ITypeResolutionService> .

3. Uygun **araç kutusu** kategorilerini etkinleştirerek veya bir sınıfın örneğini tasarımcıya uygulayarak tasarımcı uygulanabilirliğini kısıtlayarak Kullanıcı ortamının değiştirilmesi <xref:System.ComponentModel.ToolboxItemFilterAttribute> .

### <a name="designer-initialization-by-a-vspackage"></a>VSPackage tarafından tasarımcı başlatması

VSPackage, tasarımcı başlatmasını şu şekilde işlemelidir:

1. Sınıfı uygulayan bir nesne oluşturma <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> .

   > [!NOTE]
   > <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>Sınıfı asla sınıfla aynı nesneye uygulanmamalıdır <xref:Microsoft.VisualStudio.Shell.Package> .

2. Uygulayan sınıfı, <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> VSPackage 'ın Tasarımcı uzantıları için destek sağlayan şekilde kaydetme. <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>, <xref:Microsoft.VisualStudio.Shell.ProvideObjectAttribute> , Ve örneklerini, <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> VSPackage 'ın uygulamasını sağlayan sınıfına uygulayarak sınıfı kaydedin <xref:Microsoft.VisualStudio.Shell.Package> .

Bir tasarımcı veya Tasarımcı bileşeni oluşturulduğunda, Visual Studio ortamı:

- Kayıtlı her tasarım yüzeyi uzantı sağlayıcısına erişir.

- Her tasarım yüzeyi uzantısı sağlayıcısının nesnesinin bir örneğini oluşturur ve başlatır <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> .

- Her tasarım yüzeyi uzantısı sağlayıcısının <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnDesignerCreated%2A> yöntemini veya <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnComponentCreated%2A> yöntemini (uygun şekilde) çağırır.

<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>Nesneyi VSPackage 'un bir üyesi olarak uygularken, bunun anlaşılması önemlidir:

- Visual Studio ortamı, belirli bir sağlayıcının değişiklik yaptığı meta veriler veya diğer yapılandırma ayarları üzerinde herhangi bir denetim sağlamaz `DesignSurfaceExtension` . İki veya daha fazla sağlayıcı, en `DesignSurfaceExtension` son değişiklikle birlikte çakışan yöntemlerle aynı tasarımcı özelliğini değiştiriyor olabilir. En son hangi değişikliğin uygulandığını belirsiz hale gelir.

- <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>Bu uygulamaya örnekler uygulayarak nesnenin bir uygulamasını belirli tasarımcılara açıkça kısıtlamak mümkündür <xref:System.ComponentModel.ToolboxItemFilterAttribute> . **Araç kutusu** öğe filtrelemesi hakkında daha fazla bilgi için bkz <xref:System.ComponentModel.ToolboxItemFilterAttribute> <xref:System.ComponentModel.ToolboxItemFilterType> . ve.

## <a name="additional-metadata-provisioning"></a>Ek meta veri sağlama

VSPackage tasarım zamanı dışında bir tasarımcı veya Tasarımcı bileşeni yapılandırmasını değiştirebilir.

<xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>Sınıf programlı bir şekilde kullanılabilir veya tasarımcı sağlayan bir VSPackage 'a uygulanabilir.

<xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>Bir tasarım yüzeyinde oluşturulan bileşenlerin meta verilerini değiştirmek için sınıfının bir örneği kullanılır. Örneğin, bir tane, <xref:System.Windows.Forms.CommonDialog> özel bir özellik tarayıcısı olan nesneler tarafından kullanılan varsayılan bir özellik tarayıcısını değiştirebilir.

VSPackage 'ın uygulamasına uygulanan bir örneği tarafından sağlanmış değişiklikler <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> <xref:Microsoft.VisualStudio.Shell.Package> iki kapsamdan birine sahip olabilir:

- Genel--belirli bir bileşenin tüm yeni örnekleri için

- Yerel--yalnızca geçerli VSPackage tarafından sunulan bir tasarım yüzeyinde oluşturulan bileşenin örneği ile ilgili.

`IsGlobal` <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> VSPackage 'ın uygulamasına uygulanan örneğinin özelliği <xref:Microsoft.VisualStudio.Shell.Package> Bu kapsamı belirler.

Özniteliği, ' a ' <xref:Microsoft.VisualStudio.Shell.Package> <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute.IsGlobal%2A> öğesine ayarlanan nesnenin özelliği ile uygulamasına uygulama, <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> `true` aşağıdaki gibi, tüm Visual Studio ortamı için tarayıcıyı değiştirir:

`[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=true`  `)]`

`internal class MyPackage : Package {}`

Genel bayrak olarak ayarlandıysa `false` , meta veri değişikliği geçerli VSPackage tarafından desteklenen geçerli Tasarımcı için yereldir:

`[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=false`  `)]`

`internal class MyPackage : Package {}`

> [!NOTE]
> Tasarım yüzeyi yalnızca bileşen oluşturmayı destekler ve bu nedenle yalnızca bileşenlerin yerel meta verileri olabilir. Yukarıdaki örnekte, bir nesnenin özelliği gibi bir özelliği değiştirmeye çalışıyoruz `Color` . `false`Genel bayrak için geçirilmemişse, `CustomBrowser` Tasarımcı hiçbir şekilde bir örneğini oluşturmadığından hiçbir şekilde görünmez `Color` . Genel bayrağını olarak ayarlamak, `false` denetimler, zamanlayıcılar ve iletişim kutuları gibi bileşenler için kullanışlıdır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>
- <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>
- <xref:System.ComponentModel.ToolboxItemFilterType>
- [Tasarım zamanı desteğini genişletme](/previous-versions/37899azc(v=vs.140))