---
title: Tasarımcılara Geri Alma Desteği | Microsoft Docs
description: Tasarımcılara otomatik olarak veya Visual Studio SDK'daki özellikleri kullanarak Geri Al desteği sağlamayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], undo support
ms.assetid: 43eb1f14-b129-404a-8806-5bf9b099b67b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: e53cf66118bbc98526c3daa029b07fba0df2d3ba
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122144411"
---
# <a name="supply-undo-support-to-designers"></a>Tasarımcılara geri alma desteği sağlar

Düzenleyiciler gibi tasarımcıların da genellikle kullanıcıların kod öğesini değiştirirken son değişikliklerini tersine çeviremelerini için geri alma işlemlerini desteklemesi gerekir.

Bu hizmette uygulanan tasarımcıların Visual Studio tarafından otomatik olarak "geri alma" desteği sağlanır.

Geri alma özelliği için destek sağlamaları gereken tasarımcı uygulamaları:

- Soyut temel sınıfı uygulayarak geri alma yönetimi sağlama <xref:System.ComponentModel.Design.UndoEngine>

- ve sınıflarını kullanarak kalıcılık ve CodeDOM <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> desteği  <xref:System.ComponentModel.Design.IComponentChangeService> sağlar.

.NET Framework kullanarak tasarımcı yazma hakkında daha fazla bilgi için [bkz. Design-Time Desteği'ne genişletme.](/previous-versions/37899azc(v=vs.140))

, [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] aşağıdakiler tarafından varsayılan bir geri alma altyapısı sağlar:

- ve sınıfları aracılığıyla geri alma yönetim <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> uygulamaları <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> sağlama.

- Varsayılan ve uygulamalar aracılığıyla kalıcılık ve CodeDOM <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> <xref:System.ComponentModel.Design.IComponentChangeService> desteği sağlar.

## <a name="obtain-undo-support-automatically"></a>Geri Alma Desteğini Otomatik Olarak Alma

Bir tasarımcının Visual Studio otomatik ve tam geri alma desteği vardır; tasarımcı:

- Kullanıcı arabirimi için <xref:System.Windows.Forms.Control> tabanlı bir sınıf kullanır.

- Kod oluşturma ve kalıcılık için standart CodeDOM tabanlı kod oluşturma ve ayrıştırma sistemini kullanın.

   CodeDOM desteğiyle çalışma hakkında Visual Studio için bkz. [Dinamik Kaynak Kodu Oluşturma ve Derleme.](/dotnet/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation)

## <a name="when-to-use-explicit-designer-undo-support"></a>Açık Tasarımcı Geri Alma Desteği Ne Zaman Kullanılır?
 Tasarımcılar, tarafından sağlanandan farklı bir görünüm bağdaştırıcısı olarak adlandırılan bir grafik kullanıcı arabirimi kullanıyorsa kendi geri alma yönetimini <xref:System.Windows.Forms.Control> sağlanmalıdır.

 Bunun bir örneği, web tabanlı grafik tabanlı grafik arabirim yerine web tabanlı grafik tasarım arabirimine .NET Framework ürün oluşturmak olabilir.

 Bu gibi durumlarda, bu görünüm bağdaştırıcısını kullanarak Visual Studio ve açık <xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute> geri alma yönetimi sağlamak gerekebilir.

 Tasarımcıların, ad alanı içinde sağlanan kod oluşturma modelini kullanmaları Visual Studio CodeDOM ve kalıcılık <xref:System.CodeDom> desteği sağlamaları gerekir.

## <a name="undo-support-features-of-the-designer"></a>Tasarımcının Destek Özelliklerini Geri Alma
 Ortam SDK'sı, kullanıcı arabirimleri veya standart CodeDOM ve kalıcılık modeli için tabanlı sınıflar kullanmayan tasarımcılar tarafından kullanılmaktadır geri alma desteği sağlamak için gereken arabirimlerin varsayılan <xref:System.Windows.Forms.Control> uygulamalarını sağlar.

 sınıfı, <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> geri alma işlemlerini .NET Framework için sınıfının bir uygulamasını kullanarak sınıf <xref:System.ComponentModel.Design.UndoEngine> <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> sınıfından türetilen bir sınıftır.

 Visual Studio, tasarımcıyı geri almak için aşağıdaki özelliği sağlar:

- Birden çok tasarımcı arasında bağlantılı geri alma işlevi.

- Bir tasarımcı içindeki alt birimler, üzerinde ve kullanarak ebeveynleriyle <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> etkileşime <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> olabilir.

Ortam SDK'sı şunları belirterek CodeDOM ve kalıcılık desteği sağlar:

- <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> uygulamasının bir uygulaması olarak <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>

- Bir <xref:System.ComponentModel.Design.IComponentChangeService> tasarım ana bilgisayarı Visual Studio tarafından sağlanır.

## <a name="use-the-environment-sdk-features-to-supply-undo-support"></a>Geri Alma Desteği Sağlamak için Ortam SDK'sı Özelliklerini Kullanma

Geri alma desteğini almak için, tasarımcı uygulayan bir nesnenin geçerli bir uygulamayla sınıfının bir örneğini <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> başlatması ve başlatması <xref:System.IServiceProvider> gerekir. Bu <xref:System.IServiceProvider> sınıfın aşağıdaki hizmetleri sağlaması gerekir:

- <xref:System.ComponentModel.Design.IDesignerHost>.

- <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>

   CodeDOM serileştirme Visual Studio kullanan tasarımcılar, uygulaması olarak ile sağlanan <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] kullanmayı <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> seçebilir.

   Bu durumda, <xref:System.IServiceProvider> oluşturucuya sağlanan <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> sınıf bu nesneyi sınıfın bir uygulaması olarak <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> getirmalıdır.

- <xref:System.ComponentModel.Design.IComponentChangeService>

   Visual Studio tasarım ana bilgisayarı tarafından sağlanan varsayılan değeri kullanan tasarımcıların <xref:System.ComponentModel.Design.DesignSurface> sınıfının varsayılan uygulamasına sahip olduğu <xref:System.ComponentModel.Design.IComponentChangeService> garantidir.

Tabanlı bir geri alma mekanizması <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> uygulayan tasarımcılar şu durumlarda değişiklikleri otomatik olarak izler:

- Özellik değişiklikleri nesnesi aracılığıyla <xref:System.ComponentModel.TypeDescriptor> yapılır.

- <xref:System.ComponentModel.Design.IComponentChangeService> geri alınamaz bir değişiklik işlendi olduğunda olaylar el ile oluşturulur.

- Tasarımcıda yapılan değişiklikler, bir bağlamında <xref:System.ComponentModel.Design.DesignerTransaction> oluşturulmuştur.

- Tasarımcı, bir uygulaması tarafından sağlanan standart geri alma birimini veya 'den türetilen ve aynı zamanda hem hem de uygulamasını sağlayan Visual Studio'a özgü uygulamasını kullanarak açıkça geri alma <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> birimlerini <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> oluşturmayı <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> seçer.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ComponentModel.Design.UndoEngine>
- <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>
- [Destek Design-Time Genişletme](/previous-versions/37899azc(v=vs.140))
