---
title: Tasarımcılara geri alma desteği sağlama | Microsoft Docs
description: Otomatik olarak veya Visual Studio SDK 'daki özellikleri kullanarak tasarımcılarda geri alma desteği sağlamayı öğrenin.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 4108e259fb0a2e60c2719df8a7fb76f273634799
ms.sourcegitcommit: 94a57a7bda3601b83949e710a5ca779c709a6a4e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2020
ms.locfileid: "97715581"
---
# <a name="supply-undo-support-to-designers"></a>Tasarımcı için geri alma desteğini sağlama

Düzenleyicilerin benzer şekilde, bir kod öğesini değiştirirken kullanıcıların son değişikliklerini ters çevirebilmesi için genellikle geri alma işlemlerini desteklemesi gerekir.

Visual Studio 'da uygulanan çoğu tasarımcı, ortam tarafından otomatik olarak sağlanmış "geri al" desteğine sahiptir.

Geri alma özelliği için destek sağlaması gereken Tasarımcı uygulamaları:

- Özet taban sınıfını uygulayarak geri alma yönetimi sağlama <xref:System.ComponentModel.Design.UndoEngine>

- Ve sınıflarını uygulayarak Kalıcılık ve CodeDOM desteği sağlayın <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  <xref:System.ComponentModel.Design.IComponentChangeService> .

.NET Framework kullanarak tasarımcı yazma hakkında daha fazla bilgi için bkz. [genişletme Design-Time desteği](/previous-versions/37899azc(v=vs.140)).

, [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] Tarafından varsayılan bir geri alma altyapısı sağlar:

- Ve sınıfları aracılığıyla geri alma yönetimi uygulamaları sağlama <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> .

- Varsayılan ve uygulamalar aracılığıyla Kalıcılık ve CodeDOM desteği <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> sağlama <xref:System.ComponentModel.Design.IComponentChangeService> .

## <a name="obtain-undo-support-automatically"></a>Otomatik olarak geri alma desteğini al

Visual Studio 'da oluşturulan tüm tasarımcı, tasarımcı varsa otomatik ve tam geri alma desteğine sahiptir:

- <xref:System.Windows.Forms.Control>Kendi kullanıcı arabirimi için bir tabanlı sınıf kullanır.

- Kod oluşturma ve kalıcılık için standart CodeDOM tabanlı kod oluşturma ve ayrıştırma sistemini kullanır.

   Visual Studio CodeDOM desteğiyle çalışma hakkında daha fazla bilgi için bkz. [dinamik kaynak kodu oluşturma ve derleme](/dotnet/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation).

## <a name="when-to-use-explicit-designer-undo-support"></a>Açık tasarımcı ne zaman kullanılır desteği geri al
 Tasarımcı, tarafından sağlananlar dışında, görünüm bağdaştırıcısı olarak adlandırılan bir grafik kullanıcı arabirimi kullanıyorsa kendi geri alma yönetimini sağlamalıdır <xref:System.Windows.Forms.Control> .

 Buna bir örnek, .NET Framework tabanlı bir grafik arabirimi yerine Web tabanlı bir grafik tasarımı arabirimi ile bir ürün oluşturuyor olabilir.

 Bu gibi durumlarda, bu görünüm bağdaştırıcısını Visual Studio ile kaydetmesi <xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute> ve açıkça geri alma yönetimi sağlaması gerekir.

 Tasarımcıların ad alanında sunulan Visual Studio kod oluşturma modelini kullanmadıysa, CodeDOM ve kalıcılık desteği sağlaması gerekir <xref:System.CodeDom> .

## <a name="undo-support-features-of-the-designer"></a>Tasarımcının destek özelliklerini geri alma
 Ortam SDK 'Sı, <xref:System.Windows.Forms.Control> kendi kullanıcı arabirimleri veya standart CodeDOM ve Kalıcılık modeli için tabanlı sınıflar kullanmayan tasarımcılar tarafından kullanılabilen, geri alma desteği sağlamak için gereken arabirimlerin varsayılan uygulamalarını sağlar.

 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>Sınıfı, <xref:System.ComponentModel.Design.UndoEngine> <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> geri alma işlemlerini yönetmek için sınıfının bir uygulamasını kullanarak .NET Framework sınıfından türetilir.

 Visual Studio, tasarımcı geri alma için aşağıdaki özelliği sağlar:

- Birden çok tasarımcı genelinde bağlantı geri alma işlevi.

- Bir tasarlayıcı içindeki alt birimler, ve öğelerini uygulayarak üst öğeleri ile etkileşime geçebilir <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> .

Ortam SDK 'Sı aşağıdakileri sağlayarak CodeDOM ve kalıcılık desteği sağlar:

- <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> uygulama olarak <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>

- <xref:System.ComponentModel.Design.IComponentChangeService>Visual Studio tasarım ana bilgisayarı tarafından sağlanmaktadır.

## <a name="use-the-environment-sdk-features-to-supply-undo-support"></a>Geri alma desteğini sağlamak için ortam SDK özelliklerini kullanın

Geri alma desteğini almak için, Tasarımcı uygulayan bir nesne, <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> geçerli bir uygulamayla sınıfın bir örneğini oluşturmalıdır ve başlatmalıdır <xref:System.IServiceProvider> . Bu <xref:System.IServiceProvider> sınıfın aşağıdaki hizmetleri sağlaması gerekir:

- <xref:System.ComponentModel.Design.IDesignerHost>.

- <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>

   Visual Studio CodeDOM serileştirmesi kullanan tasarımcılar, uygulamasının <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> uygulamasıyla birlikte sağlanmış olarak kullanmayı seçebilir [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> .

   Bu durumda, <xref:System.IServiceProvider> oluşturucuya sunulan sınıf <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> Bu nesneyi sınıfının bir uygulamasına döndürmelidir <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> .

- <xref:System.ComponentModel.Design.IComponentChangeService>

   <xref:System.ComponentModel.Design.DesignSurface>Visual Studio tasarım ana bilgisayarı tarafından sunulan varsayılan olan tasarımcıların, sınıfının varsayılan bir uygulamasına sahip olduğu garanti edilir <xref:System.ComponentModel.Design.IComponentChangeService> .

Bir <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> tabanlı geri alma mekanizması uygulayan tasarımcılar, şu durumlarda değişiklikleri otomatik olarak izler:

- Özellik değişiklikleri nesne aracılığıyla yapılır <xref:System.ComponentModel.TypeDescriptor> .

- <xref:System.ComponentModel.Design.IComponentChangeService> geri alınamaz bir değişiklik yapıldığında olaylar el ile oluşturulur.

- Tasarımcıda değişiklik bir ' ın bağlamı içinde oluşturulmuştur <xref:System.ComponentModel.Design.DesignerTransaction> .

- Tasarımcı, bir uygulama veya Visual Studio 'Ya özgü uygulama tarafından sağlanan standart geri alma birimini kullanarak açıkça geri alma birimi oluşturmayı seçer <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> ve aynı zamanda ve ' de bir uygulama sağlar <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> .

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ComponentModel.Design.UndoEngine>
- <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>
- [Design-Time desteğini uzat](/previous-versions/37899azc(v=vs.140))
