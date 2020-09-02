---
title: Tasarımcılara geri alma desteği sağlama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], undo support
ms.assetid: 43eb1f14-b129-404a-8806-5bf9b099b67b
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6136caaec0cb8f0d79e3fb7b96245fc3fd070710
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65675336"
---
# <a name="supplying-undo-support-to-designers"></a>Tasarımcılara Geri Alma Desteği Sağlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Düzenleyicilerin benzer şekilde, bir kod öğesini değiştirirken kullanıcıların son değişikliklerini ters çevirebilmesi için genellikle geri alma işlemlerini desteklemesi gerekir.  
  
 Visual Studio 'da uygulanan çoğu tasarımcı, ortam tarafından otomatik olarak belirtilen geri alma desteğine sahiptir.  
  
 Geri alma özelliği için destek sağlaması gereken Tasarımcı uygulamaları:  
  
- Özet taban sınıfını uygulayarak geri alma yönetimi sağlama <xref:System.ComponentModel.Design.UndoEngine>  
  
- Ve sınıflarını uygulayarak Kalıcılık ve CodeDOM desteği sağlayın <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> <xref:System.ComponentModel.Design.IComponentChangeService> .  
  
  Kullanarak tasarımcı yazma hakkında daha fazla bilgi için [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] bkz. [Tasarım zamanı desteğini genişletme](https://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2).  
  
  , [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] Tarafından varsayılan bir geri alma altyapısı sağlar:  
  
- Ve sınıfları aracılığıyla geri alma yönetimi uygulamaları sağlama <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> .  
  
- Varsayılan ve uygulamalar aracılığıyla Kalıcılık ve CodeDOM desteği <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> sağlama <xref:System.ComponentModel.Design.IComponentChangeService> .  
  
## <a name="obtaining-undo-support-automatically"></a>Otomatik olarak geri alma desteğini alma  
 İçinde oluşturulan herhangi bir tasarımcı [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , tasarımcı varsa otomatik ve tam geri alma desteğine sahiptir:  
  
- <xref:System.Windows.Forms.Control>Kendi kullanıcı arabirimi için bir tabanlı sınıf kullanır.  
  
- Kod oluşturma ve kalıcılık için standart CodeDOM tabanlı kod oluşturma ve ayrıştırma sistemini kullanır.  
  
     Visual Studio CodeDOM desteğiyle çalışma hakkında daha fazla bilgi için bkz. [dinamik kaynak kodu oluşturma ve derleme](https://msdn.microsoft.com/library/d077a3e8-bd81-4bdf-b6a3-323857ea30fb)  
  
## <a name="when-to-use-explicit-designer-undo-support"></a>Açık tasarımcı ne zaman kullanılır desteği geri al  
 Tasarımcı, tarafından sağlananlar dışında, görünüm bağdaştırıcısı olarak adlandırılan bir grafik kullanıcı arabirimi kullanıyorsa kendi geri alma yönetimini sağlamalıdır <xref:System.Windows.Forms.Control> .  
  
 Buna bir örnek, temel bir grafik arabirimi yerine Web tabanlı bir grafik tasarımı arabirimi ile bir ürün oluşturuyor olabilir [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .  
  
 Bu gibi durumlarda, birinin bu görünüm bağdaştırıcısını [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] kullanarak kaydetmesi <xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute> ve açık geri alma yönetimi sağlaması gerekir.  
  
 Tasarımcıların, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ad alanında sunulan kod oluşturma modelini kullanmadıysa, CodeDOM ve kalıcılık desteği sağlaması gerekir <xref:System.CodeDom> .  
  
## <a name="undo-support-features-of-the-designer"></a>Tasarımcının destek özelliklerini geri alma  
 Ortam SDK 'Sı, <xref:System.Windows.Forms.Control> kendi kullanıcı arabirimleri veya standart CodeDOM ve Kalıcılık modeli için tabanlı sınıflar kullanmayan tasarımcılar tarafından kullanılabilen, geri alma desteği sağlamak için gereken arabirimlerin varsayılan uygulamalarını sağlar.  
  
 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>Sınıfı, [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] <xref:System.ComponentModel.Design.UndoEngine> <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> geri alma işlemlerini yönetmek için sınıfının bir uygulamasını kullanarak sınıfından türetilir.  
  
 Visual Studio, tasarımcı geri alma için aşağıdaki özelliği sağlar:  
  
- Birden çok tasarımcı genelinde bağlantı geri alma işlevi.  
  
- Bir tasarlayıcı içindeki alt birimler, ve öğelerini uygulayarak üst öğeleri ile etkileşime geçebilir <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> .  
  
  Ortam SDK 'Sı aşağıdakileri sağlayarak CodeDOM ve kalıcılık desteği sağlar:  
  
- <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> uygulamasının bir uygulaması olarak <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
  <xref:System.ComponentModel.Design.IComponentChangeService> [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ' ' Tasarım ana bilgisayarı tarafından sağlanmış.  
  
## <a name="using-the-environment-sdk-features-to-supply-undo-support"></a>Geri alma desteğini sağlamak için ortam SDK özelliklerini kullanma  
 Geri alma desteğini almak için, Tasarımcı uygulayan bir nesne şunları içermelidir:  
  
- <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>Geçerli bir uygulamayla sınıfın bir örneğini oluşturun ve başlatın <xref:System.IServiceProvider> .  
  
- Bu <xref:System.IServiceProvider> sınıfın aşağıdaki hizmetleri sağlaması gerekir:  
  
  - <xref:System.ComponentModel.Design.IDesignerHost>.  
  
  - <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
       CodeDOM serileştirme kullanan tasarımcılar, uygulamasının [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> uygulamasıyla birlikte sağlanmış olarak kullanmayı seçebilir [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> .  
  
       Bu durumda, <xref:System.IServiceProvider> oluşturucuya sunulan sınıf <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> Bu nesneyi sınıfının bir uygulamasına döndürmelidir <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> .  
  
  - <xref:System.ComponentModel.Design.IComponentChangeService>  
  
       <xref:System.ComponentModel.Design.DesignSurface>Tasarım ana bilgisayarı tarafından sunulan varsayılan olarak kullanılan tasarımcılar, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sınıfının varsayılan bir uygulamasına sahip olmak için garanti edilir <xref:System.ComponentModel.Design.IComponentChangeService> .  
  
  Bir <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> tabanlı geri alma mekanizması uygulayan tasarımcılar, şu durumlarda değişiklikleri otomatik olarak izler:  
  
- Özellik değişiklikleri nesne aracılığıyla yapılır <xref:System.ComponentModel.TypeDescriptor> .  
  
- <xref:System.ComponentModel.Design.IComponentChangeService> geri alınamaz bir değişiklik yapıldığında olaylar el ile oluşturulur.  
  
- Tasarımcıda değişiklik bir ' ın bağlamı içinde oluşturulmuştur <xref:System.ComponentModel.Design.DesignerTransaction> .  
  
- Tasarımcı, bir uygulama veya Visual Studio 'Ya özgü uygulama tarafından sağlanan standart geri alma birimini kullanarak açıkça geri alma birimi oluşturmayı seçer <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> ve aynı zamanda ve ' de bir uygulama sağlar <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> .  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ComponentModel.Design.UndoEngine>   
 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>   
 [Tasarım Zamanı Desteği Sunma](https://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)
