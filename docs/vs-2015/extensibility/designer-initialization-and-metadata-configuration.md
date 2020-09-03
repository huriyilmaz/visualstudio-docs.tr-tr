---
title: Tasarımcı başlatma ve meta veri yapılandırması | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], initializing
- designers [Visual Studio SDK], configuring metadata
ms.assetid: f7fe9a7e-f669-4642-ad5d-186b2e6e6ec9
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2dec3937616c712c56b7012949e044702e6b11f2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703062"
---
# <a name="designer-initialization-and-metadata-configuration"></a>Tasarımcıyı Başlatma ve Meta Verileri Yapılandırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir tasarımcı veya tasarımcı bileşeniyle ilişkili meta veri ve filtre özniteliklerinin düzenlemesi, belirli bir tasarımcı tarafından farklı <xref:System.Type> nesneleri (veri yapıları, sınıflar veya grafik varlıklar gibi) işlemek için hangi araçların kullanıldığını, tasarımcı 'nın kullanılabilir olduğunu ve Visual STUDIO IDE 'nin tasarımcıyı destekleyecek şekilde nasıl yapılandırıldığını (örneğin, **araç kutusu** kategorisi veya sekmenin kullanılabildiği) tanımlamak için bir mekanizma sağlar.  
  
 , [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] Bir tasarımcının veya tasarımcı bileşeninin başlatılmasının denetimini ve meta verilerinin VSPackage tarafından düzenlenmesini kolaylaştırmak için çeşitli mekanizmalar sağlar.  
  
## <a name="initializing-metadata-and-configuration-information"></a>Meta veriler ve yapılandırma bilgileri başlatılıyor  
 İsteğe bağlı olarak yüklendiği için VSPackages, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] bir tasarımcının örneklemesinin öncesinde ortam tarafından yüklenmemiş olabilir. Bu nedenle, VSPackages, bir olayı işlemek için kullanılan oluşturma sırasında tasarımcı veya Tasarımcı bileşeni yapılandırmak için standart mekanizmayı kullanamaz <xref:System.ComponentModel.Design.IDesignerEventService.DesignerCreated> . Bunun yerine, VSPackage arabirimin bir örneğini uygular <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> ve tasarım yüzeyi uzantıları olarak adlandırılan özelleştirmeler sağlamak için kendisini kaydeder.  
  
### <a name="customizing-initialization"></a>Başlatmayı özelleştirme  
 Tasarımcı, bileşen veya tasarımcı yüzeyini özelleştirme şunları içerir:  
  
1. Tasarımcı meta verilerini değiştirme ve belirli bir şekilde nasıl <xref:System.Type> erişildiğini veya dönüştürüldüğünü değiştirme.  
  
     Bu genellikle veya mekanizmaları aracılığıyla yapılır <xref:System.Drawing.Design.UITypeEditor> <xref:System.ComponentModel.TypeConverter> .  
  
     Örneğin, <xref:System.Windows.Forms> tabanlı tasarımcılar başlatıldığında [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ortam, <xref:System.Drawing.Design.UITypeEditor> <xref:System.Web.UI.WebControls.Image> Kaynak Yöneticisi 'ni kullanarak dosya sistemi yerine bit eşlemler elde etmek üzere Tasarımcı ile kullanılan nesneleri için değiştirir.  
  
2. Örneğin, olaylara abone olarak veya proje yapılandırma bilgilerini alarak ortamla tümleştirme. Arabirimi alarak, proje yapılandırma bilgilerini alabilir ve olaylara abone olabilirsiniz <xref:System.ComponentModel.Design.ITypeResolutionService> .  
  
3. Uygun **araç kutusu** kategorilerini etkinleştirerek veya bir sınıfın örneğini tasarımcıya uygulayarak tasarımcı uygulanabilirliğini kısıtlayarak Kullanıcı ortamının değiştirilmesi <xref:System.ComponentModel.ToolboxItemFilterAttribute> .  
  
### <a name="designer-initialization-by-a-vspackage"></a>VSPackage tarafından tasarımcı başlatması  
 VSPackage, tasarımcı başlatmasını şu şekilde işlemelidir:  
  
1. Sınıfı uygulayan bir nesne oluşturma <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> .  
  
   > [!NOTE]
   > <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>Sınıfı asla sınıfla aynı nesneye uygulanmamalıdır <xref:Microsoft.VisualStudio.Shell.Package> .  
  
2. Örneğini <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>  <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute> <xref:Microsoft.VisualStudio.Shell.ProvideObjectAttribute> ve <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> VSPackage 'ın uygulamasını sağlayan sınıfına ve örneklerini uygulayarak VSPackage 'ın Tasarımcı uzantıları için destek sağlamak üzere uygulayan sınıfı kaydedin <xref:Microsoft.VisualStudio.Shell.Package> .  
  
   Her tasarımcı veya Tasarımcı bileşeni oluşturulduğunda, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ortam:  
  
3. Kayıtlı her tasarım yüzeyi uzantı sağlayıcısına erişir.  
  
4. Her tasarım yüzeyi uzantısı sağlayıcısının nesnesinin bir örneğini oluşturur ve başlatır <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>  
  
5. Her tasarım yüzeyi uzantısı sağlayıcısının <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnDesignerCreated%2A> yöntemini veya <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnComponentCreated%2A> yöntemini (uygun şekilde) çağırır.  
  
   <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>Nesneyi VSPackage 'un bir üyesi olarak uygularken, bunun anlaşılması önemlidir:  
  
6. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Ortam, belirli bir sağlayıcının değişiklik yaptığı meta veriler veya diğer yapılandırma ayarları üzerinde herhangi bir denetim sağlamaz `DesignSurfaceExtension` . İki veya daha fazla sağlayıcı, en `DesignSurfaceExtension` son değişiklikle birlikte çakışan yöntemlerle aynı tasarımcı özelliğini değiştiriyor olabilir. En son hangi değişikliğin uygulandığını belirsiz hale gelir.  
  
7. <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>Bu uygulamaya örnek uygulayarak nesnenin bir uygulamasını belirli tasarımcılara açıkça kısıtlamak mümkündür <xref:System.ComponentModel.ToolboxItemFilterAttribute> . **Araç kutusu** öğe filtrelemesi hakkında daha fazla bilgi için bkz <xref:System.ComponentModel.ToolboxItemFilterAttribute> <xref:System.ComponentModel.ToolboxItemFilterType> . ve.  
  
## <a name="additional-metadata-provisioning"></a>Ek meta veri sağlama  
 VSPackage tasarım zamanı dışında bir tasarımcı veya Tasarımcı bileşeni yapılandırmasını değiştirebilir.  
  
 <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>Sınıf programlı bir şekilde kullanılabilir veya tasarımcı sağlayan bir VSPackage öğesine uygulanabilir.  
  
 <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>Bir tasarım yüzeyinde oluşturulan bileşenlerin meta verilerini değiştirmek için sınıfının bir örneği kullanılır. Örneğin, bir tane, nesneler tarafından kullanılan varsayılan bir özellik tarayıcısını <xref:System.Windows.Forms.CommonDialog> özel bir özellik tarayıcısı ile değiştirebilir.  
  
 VSPackage 'ın uygulamasına uygulanan bir örneği tarafından sağlanmış değişiklikler <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> <xref:Microsoft.VisualStudio.Shell.Package> iki kapsamdan birine sahip olabilir:  
  
- Genel--belirli bir bileşenin tüm yeni örnekleri için  
  
- Yerel--yalnızca geçerli VSPackage tarafından sunulan bir tasarım yüzeyinde oluşturulan bileşenin örneği ile ilgili.  
  
  `IsGlobal` <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> VSPackage 'ın uygulamasına uygulanan örneğinin özelliği <xref:Microsoft.VisualStudio.Shell.Package> Bu kapsamı belirler.  
  
  <xref:Microsoft.VisualStudio.Shell.Package>Aşağıdaki gibi, nesne kümesi özelliği ile bir uygulamasına özniteliği uygulayarak, <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute.IsGlobal%2A> <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> `true` Tüm ortam için tarayıcıyı değiştirir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] :  
  
  `[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=true`  `)]`  
  
  `internal class MyPackage : Package {}`  
  
  Genel bayrak olarak ayarlandıysa `false` , meta veri değişikliği geçerli VSPackage tarafından desteklenen geçerli Tasarımcı için yereldir:  
  
  `[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=false`  `)]`  
  
  `internal class MyPackage : Package {}`  
  
> [!NOTE]
> Şimdiki zamanda tasarım yüzeyi yalnızca bileşen oluşturmayı destekler ve bu nedenle yalnızca bileşenlerin yerel meta verileri olabilir. Yukarıdaki örnekte, bir nesnenin özelliği gibi bir özelliği değiştirmeye çalışıyoruz `Color` . `false`Genel bayrak için geçirilmemişse, `CustomBrowser` Tasarımcı hiçbir şekilde bir örneğini oluşturmadığından hiçbir şekilde görünmez `Color` . Genel bayrağını olarak ayarlamak, `false` denetimler, zamanlayıcılar ve iletişim kutuları gibi bileşenler için kullanışlıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>   
 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>   
 <xref:System.ComponentModel.ToolboxItemFilterType>   
 [Tasarım Zamanı Desteği Sunma](https://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)
