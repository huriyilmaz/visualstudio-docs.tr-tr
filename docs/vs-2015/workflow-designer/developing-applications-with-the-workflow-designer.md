---
title: İş Akışı Tasarımcısı ile uygulama geliştirme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- DefaultWorkflowDesigner
- DefaultWorkflowDesigner.UI
helpviewer_keywords:
- Visual Studio 2010 Workflow Designer [WFD], overview
- Workflow Designer [WFD]
- Visual Studio 2010 Workflow Designer [WFD]
- Workflow Designer [WFD], overview
ms.assetid: 4cd062b1-b496-4668-bbc1-ee85545e066d
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 848300c54800e229ee1f487fc415bad45d982a6c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656822"
---
# <a name="developing-applications-with-the-workflow-designer"></a>İş Akışı Tasarımcısı ile Uygulama Geliştirme
@No__t_0, [!INCLUDE[vs2010](../includes/vs2010-md.md)] geliştirme ortamında barındırılan [!INCLUDE[netfx40_long](../includes/netfx40-long-md.md)] [!INCLUDE[wf](../includes/wf-md.md)] uygulamalarda grafik oluşturma ve hata ayıklama için bir görsel tasarımcı ve hata ayıklayıcısıdır. Şablonları ve etkinlik tasarımcılarını kullanarak bileşik bir iş akışı uygulaması, etkinlik kitaplığı veya [!INCLUDE[indigo1](../includes/indigo1-md.md)] hizmeti oluşturmanız mümkün olur. iş akışları [!INCLUDE[crabout](../includes/crabout-md.md)], bkz [. &#91;Windows Workflow Foundation .NET Framework&#93;4](https://msdn.microsoft.com/library/9a23ea6b-d600-483e-89cd-8889cfec5f66).

 Aşağıda, [!INCLUDE[wfd2](../includes/wfd2-md.md)] [!INCLUDE[wfd2](../includes/wfd2-md.md)] eski sürümlerinden ayrı olarak bu yeni sürümü ayarlanan çeşitli yeni tasarım özellikleri verilmiştir:

- @No__t_0, [!INCLUDE[avalon1](../includes/avalon1-md.md)] kullanılarak oluşturulmuştur. Bu, etkinlik Tasarımcısı deneyimini geliştirir ve büyük ve karmaşık iş akışlarının performansını geliştirir.

- Özel etkinlikler artık [!INCLUDE[avalon2](../includes/avalon2-md.md)] ile tasarlanmıştır, XAML kullanımı ve etkinlik tasarımcıları oluşturmak için programlama modeli basitleştirilmiştir.

- Bir akış çizelgesi etkinliği uygulandı, böylece tanıdık akış çizelgesi modelleme stilini kullanarak program akışını görselleştirebilirsiniz.

- @No__t_0, iş akışlarınızda değişkenleri bildirmenizi ve kapsamını etkinliklere bağlamayı sağlayan yeni bir değişken tasarımcısına sahiptir.

- @No__t_0, [!INCLUDE[wfd2](../includes/wfd2-md.md)] [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] iş akışlarınızda Visual Basic ifadeleri yazarken tam IntelliSense özellikleri sağlar.

- Hata ayıklama deneyimi artık XAML 'e taşıyor ve XAML iş akışı tanımınızda kesme noktaları ayarlamanıza ve yönetilen kodda buna benzer bir deneyim sağlayan çalışma zamanında XAML kodunuzu adım adım görmenize olanak tanır.

- @No__t_0 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] dışında yeniden barındırma, önceki sürümlere kıyasla büyük ölçüde basitleştirilmiştir, şimdi yalnızca birkaç satır kod gerektirir.

- Yeni <xref:System.Activities.Statements.Flowchart> etkinliği ve onun [akış çizelgesi](../workflow-designer/flowchart-activity-designer.md) , tanıdık akış çizelgesi modelleme stilini kullanarak program akışınızı görselleştirmenize olanak tanır.

- Mesajlaşma etkinlikleri geliştirilmiştir, tam bildirime dayalı (kod yok) [!INCLUDE[indigo1](../includes/indigo1-md.md)] Hizmetleri yazmanızı sağlar.

- **Hizmet başvurusu Ekle..** . işlevselliği, Web hizmetlerine erişim sağlayan etkinlikleri otomatik olarak oluşturmanıza olanak tanır.

## <a name="in-this-section"></a>Bu Bölümde
 [İş akışı Tasarımcısı kullanma](../workflow-designer/using-the-workflow-designer.md) Yerleşik tasarımcıları ve tasarımcı tarafından sunulan diğer araçların bağımsız değişkenleri, değişkenleri, ifadeleri, içeri aktarımları ve içerik haritası gezintisini işlemek için nasıl kullanılacağını gösterir.

 [Etkinlik tasarımcılarını kullanma](../workflow-designer/using-the-activity-designers.md) Etkinlikleri ve şablonları ve sistem tarafından belirtilen tasarımcılarının kategorilerini açıklar.

 [İş akışı Tasarımcısı Iş akışlarında hata ayıklama](../workflow-designer/debugging-workflows-with-the-workflow-designer.md) Geleneksel hata ayıklama yordamlarının yanı sıra XAML ve ifadelerin hatalarını ayıklamanın nasıl yapılacağını açıklamaktadır.

 [İş akışı TASARıMCıSı UI Yardımı](../workflow-designer/workflow-designer-ui-help.md) @No__t_1 tarafından sağlanan iletişim kutuları için bağlama duyarlı Yardım konuları ve tasarımcı kabuğu özellikleri, klavye kısayolları ve hata iletileri hakkında yönergeler içerir.

 [.Net 3,0 veya .net 3,5 çerçevesini hedefleyen Iş akışı uygulamaları geliştirme](../workflow-designer/developing-workflow-applications-targeting-the-dotnet-3-0-or-dotnet-3-5-framework.md) @No__t_1 veya [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] hedefleyen eski tasarımcıyı kullanma hakkında rehberlik içerir.

 [Tasarımcı örnek oluşturma &#91;WF örnekleri&#93; ](https://msdn.microsoft.com/library/b676ad31-5f64-4d84-9a36-b4d7113a2f4d) Bu örnek, tasarımcıyı içeren WPF düzeninin nasıl oluşturulacağını gösterir.

 [Özel etkinlik tasarımcıları](https://msdn.microsoft.com/library/dcf14dca-ce6d-4278-96ba-062f0a679075) Bu bölüm, iş akışı tasarımcısında görüntülenmek üzere özel tasarımcılar kullanan etkinlik örneklerini içerir.