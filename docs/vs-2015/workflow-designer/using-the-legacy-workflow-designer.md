---
title: Eski İş Akışı Tasarımcısı kullanma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- Visual Studio 2005 Extensions for Windows Workflow Foundation, about
ms.assetid: 7af53077-afd7-465f-9c1d-b387e9d4f216
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 72c92b4431c21c27bc1fe2ff86b24c850cc34694
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75846090"
---
# <a name="using-the-legacy-workflow-designer"></a>Eski İş Akışı Tasarımcısını Kullanma
[!INCLUDE[vs2010](../includes/vs2010-md.md)] tarafından sunulan eski [!INCLUDE[wfd2](../includes/wfd2-md.md)], [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] veya [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]hedeflemek için kullanılabilir.

 **Yeni proje** penceresinin en üstündeki açılan listede **.NET Framework 3,0** seçeneği veya **.NET Framework 3,5** seçeneği belirlenerek erişilir. [!INCLUDE[vs2010](../includes/vs2010-md.md)] varsayılan seçeneği, [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)]hedefleyen [!INCLUDE[wf](../includes/wf-md.md)] uygulamalar oluşturmak için kullanılan **.NET Framework 4** ' tir.

 [!INCLUDE[wfd2](../includes/wfd2-md.md)] tanıdık [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Kullanıcı arabirimini kullanarak [!INCLUDE[wf](../includes/wf-md.md)] uygulamaları grafiksel olarak oluşturmak için bir yol sağlar. [!INCLUDE[wf](../includes/wf-md.md)] uygulamalar, etkinlik olarak adlandırılan iş akışı işlemi adımlarından oluşur. Bir iş akışı oluşturmak için, ilgili etkinlik tasarımcılarını **araç kutusu** 'ndan tasarım yüzeyine sürükleyerek tasarım yüzeyine etkinlik oluşturun.

 Aşağıdaki tabloda Windows Workflow Foundation için [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] temel özellikleri listelenmektedir.

|Özellik|Açıklama|
|-------------|-----------------|
|Etkinlik sürükle ve bırak|Bir iş akışı oluşturmak için **araç kutusundaki** etkinlikleri tasarım yüzeyine sürükleyin.|
|Özellik Tarayıcısı|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] içindeki standart **Özellikler** penceresi, bir etkinliğin özelliklerini yapılandırmak için kullanılır.|
|Yakınlaştır|Binocuklar **yakınlaştırma düzeyi** simgesi tasarım yüzeyinin sağ tarafındaki dikey kaydırma çubuğunun altında bulunur. Bir iş akışı grafiğinin yakınlaştırmasını veya ölçeğini yakınlaştırmak için, binocuklar ' a tıklayın ve bir yakınlaştırma yüzdesi seçin. Ayrıca, yakınlaştırmak ve uzaklaştırmak için **kaydırma** simgesi Büyüteç imlecini göster seçeneğini de kullanabilirsiniz.|
|Kaydır|Dört yönü işaret eden dört çapraz geçiş içeren bir daire olan **kaydırma** simgesi, tasarım yüzeyinin sağ tarafındaki dikey kaydırma çubuğunun altında, yalnızca Binocular yakınlaştırma simgesinin altında bulunur. Kaydırma simgesine tıklarsanız, bir açılır menü aşağıdaki imleç seçeneklerini sunar:<br /><br /> -Büyüteç imlecini **Yakınlaştırma** , tasarım yüzeyine tıklayarak yakınlaştırmanızı sağlar.<br />-Büyütme **büyütme camı imleci, tasarım** yüzeyine tıklayarak uzaklaştırmanıza olanak sağlar.<br />- **Gezinti Aracı** el imleci, Tasarım yüzeyinde bir iş akışının görünümünü "almanıza" ve kaydırabilmenizi sağlar.<br />- **Varsayılan** ok imleci diğer imleçlerden varsayılan ok imlecine geçiş yapmanızı sağlar.|
|Otomatik kaydırma|Büyük bir iş akışınız varsa, tasarım yüzeyi alanının görünür görüntülenmesini aşan bir etkinlik yerleştirmek isteyebilirsiniz. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], aktiviteyi yerleştirmek istediğiniz yere en yakın tasarım yüzeyi kenarına doğru bir etkinlik sürüklemenizi sağlar. Tasarım yüzeyi görünümü otomatik olarak bu yönde kayar.|
|Akıllı etiketler|Tamamen yapılandırılmamış veya geçerli yapılandırılmamış etkinlikler bir ünlem işareti simgesiyle işaretlenir. Simgeye tıklayabilir ve etkinlik üzerinde var olan yapılandırma gereksinimlerinin bir açılır listesini görebilirsiniz. Daha sonra etkinliği uygun şekilde yapılandırmak için **Özellikler** penceresini kullanabilirsiniz. Etkinlik için tüm özellikler geçerliyse, ünlem işareti simgesi kaybolur.|

## <a name="in-this-section"></a>Bu Bölümde
 [Visual Studio İş Akışı Pencereleri (Eski)](../workflow-designer/visual-studio-workflow-windows-legacy.md)

 [Eski İş Akışı Projeleri Oluşturma](../workflow-designer/creating-legacy-workflow-projects.md)

 [Sıralı İş Akışı Görünümleri (Eski)](../workflow-designer/sequential-workflow-views-legacy.md)

 [Eski İş Akışı Etkinlikleri ](../workflow-designer/legacy-workflow-activities.md)

 [İş Akışlarında Temaları Kullanma (Eski)](../workflow-designer/using-themes-in-workflows-legacy.md)

 [Eski Durum Makinesi İş Akışı Tasarımcısını Kullanma](../workflow-designer/using-the-legacy-state-machine-workflow-designer.md)

 [Eski Etkinlik Tasarımcısını Kullanma](../workflow-designer/using-the-legacy-activity-designer.md)

 [Windows Workflow Foundation Kullanıcı Arabirimi Yardımı için Eski Tasarımcı](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)

## <a name="see-also"></a>Ayrıca Bkz.
 [Iş akışları geliştirme](https://msdn2.microsoft.com/library/bb628448.aspx)
