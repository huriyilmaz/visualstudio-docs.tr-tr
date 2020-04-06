---
title: Tasarımcılara Geri Alma Desteği Sağlanması | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], undo support
ms.assetid: 43eb1f14-b129-404a-8806-5bf9b099b67b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0580f974c362a71c3e400946f2ad34f565ad1232
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699671"
---
# <a name="supply-undo-support-to-designers"></a>Tasarımcılara geri alım desteği

Düzenleyiciler gibi tasarımcıların, kullanıcıların bir kod öğesini değiştirirken son değişikliklerini tersine çevirebilmeleri için genellikle geri alma işlemlerini desteklemesi gerekir.

Visual Studio'da uygulanan tasarımcıların çoğu, çevre tarafından otomatik olarak sağlanan "geri" desteğine sahiptir.

Geri alma özelliği için destek sağlaması gereken tasarımcı uygulamaları:

- Soyut taban sınıfını uygulayarak geri alma yönetimini sağlama<xref:System.ComponentModel.Design.UndoEngine>

- Tedarik sebat ve CodeDOM desteği <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> <xref:System.ComponentModel.Design.IComponentChangeService> uygulayarak ve sınıflar.

.NET Framework'u kullanarak tasarımcıları yazma hakkında daha fazla bilgi için [Tasarım-Zaman Desteğini Genişlet'e](/previous-versions/37899azc(v=vs.140))bakın.

Aşağıdakiler [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] tarafından varsayılan geri aparat altyapısı sağlar:

- Ve sınıflar aracılığıyla geri alma yönetimi uygulamaları sağlamak. <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>

- Varsayılan <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> ve uygulamalar aracılığıyla kalıcılık ve <xref:System.ComponentModel.Design.IComponentChangeService> CodeDOM desteği sağlama.

## <a name="obtain-undo-support-automatically"></a>Otomatik olarak Geri Al Desteği Edinin

Visual Studio oluşturulan herhangi bir tasarımcı otomatik ve tam geri alma desteği varsa, tasarımcı:

- Kullanıcı arabirimi <xref:System.Windows.Forms.Control> için tabanlı bir sınıf kullanır.

- Kod oluşturma ve kalıcılık için standart CodeDOM tabanlı kod oluşturma ve ayrıştırma sistemi kullanır.

   Visual Studio CodeDOM desteği ile çalışma hakkında daha fazla bilgi için [Dinamik Kaynak Kodu Oluşturma ve Derleme'ye](/dotnet/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation)bakın.

## <a name="when-to-use-explicit-designer-undo-support"></a>Açık Tasarımcı Geri Ala Desteği Ne Zaman Kullanılır
 Tasarımcılar, bir görünüm bağdaştırıcısı olarak adlandırılan bir grafik kullanıcı arabirimi kullanıyorsanız, kendi <xref:System.Windows.Forms.Control>geri alım yönetimini sağlamalıdır.

 Bunun bir örneği, .NET Framework tabanlı grafik arabirimi yerine web tabanlı grafik tasarım arabirimine sahip bir ürün oluşturmak olabilir.

 Bu gibi durumlarda, bu görünüm bağdaştırıcısını <xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute>Visual Studio'ya kaydettirmemiz ve açık geri alabilme yönetimini sağlamanız gerekir.

 <xref:System.CodeDom> Tasarımcılar, ad alanında sağlanan Visual Studio kod oluşturma modelini kullanmıyorlarsa CodeDOM ve kalıcılık desteği sağlamaları gerekir.

## <a name="undo-support-features-of-the-designer"></a>Tasarımcının Destek Özelliklerini Geri Ala
 Çevre SDK, kullanıcı arabirimleri veya standart CodeDOM ve kalıcılık modeli için <xref:System.Windows.Forms.Control> temel sınıfları kullanmayan tasarımcılar tarafından kullanılabilecek geri alma desteği sağlamak için gereken arabirimlerin varsayılan uygulamalarını sağlar.

 Sınıf, <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> geri alma işlemlerini yönetmek <xref:System.ComponentModel.Design.UndoEngine> için <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> sınıfın bir uygulamasını kullanarak .NET Framework sınıfından türetilmiştir.

 Visual Studio tasarımcı geri almak için aşağıdaki özelliği sağlar:

- Birden çok tasarımcı arasında bağlantılı geri alaişlevi.

- Bir tasarımcı içinde Çocuk birimleri uygulayarak <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> ve <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>ebeveynleri ile etkileşim eolabilir.

Çevre SDK, aşağıdakileri sağlayarak CodeDOM ve kalıcılık desteği sağlar:

- <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>bir uygulama olarak<xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>

- Bir <xref:System.ComponentModel.Design.IComponentChangeService> Visual Studio tasarım ev sahibi tarafından sağlanmaktadır.

## <a name="use-the-environment-sdk-features-to-supply-undo-support"></a>Geri Al Desteği Sağlamak Için Çevre SDK Özelliklerini Kullanın

Geri alma desteği elde etmek için, tasarımcıyı uygulayan bir nesnenin, <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> geçerli <xref:System.IServiceProvider> bir uygulamayla sınıfın bir örneğini anında anlaması ve başlatması gerekir. Bu <xref:System.IServiceProvider> sınıf aşağıdaki hizmetleri sağlamalıdır:

- <xref:System.ComponentModel.Design.IDesignerHost>.

- <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>

   Visual Studio CodeDOM serileştirme kullanan tasarımcılar, <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> uygulanması [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] olarak sağlanan <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>kullanmayı tercih edebilirsiniz.

   Bu durumda, <xref:System.IServiceProvider> <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> oluşturucuya sağlanan sınıf <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> sınıfın bir uygulaması olarak bu nesneyi döndürmelidir.

- <xref:System.ComponentModel.Design.IComponentChangeService>

   Visual Studio tasarım <xref:System.ComponentModel.Design.DesignSurface> ana bilgisayarı tarafından sağlanan varsayılanı kullanan tasarımcıların <xref:System.ComponentModel.Design.IComponentChangeService> sınıfın varsayılan uygulamasına sahip olması garanti edilir.

Tabanlı geri <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> alma mekanizmasını uygulayan tasarımcılar, şu nda varsa değişiklikleri otomatik olarak izler:

- Özellik değişiklikleri <xref:System.ComponentModel.TypeDescriptor> nesne üzerinden yapılır.

- <xref:System.ComponentModel.Design.IComponentChangeService>geri alabilen bir değişiklik yapıldığında olaylar el ile oluşturulur.

- Tasarımcı üzerinde değişiklik bir <xref:System.ComponentModel.Design.DesignerTransaction>bağlam içinde oluşturuldu.

- Tasarımcı açıkça bir <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> uygulama veya Visual Studio özgü uygulama <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>tarafından sağlanan standart geri alma birimi kullanarak geri alma <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> birimleri oluşturmak için seçer <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> , hangi türetilmiştir ve aynı zamanda hem bir uygulama sağlar ve <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit>.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ComponentModel.Design.UndoEngine>
- <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>
- [Tasarım Süresi Desteğini Genişlet](/previous-versions/37899azc(v=vs.140))
