---
title: Office projelerinde erişilebilirlik
description: Microsoft Office projelerinin, standart erişilebilirlik gereksinimlerini karşılayan özel çözümler oluşturmanıza olanak sağlayan birçok erişilebilirlik özelliği nasıl ekleneceğini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, accessibility
- shortcut keys [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], shortcut keys
- accessibility [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 440eb9ee0e5d228280cc8a8052abc3e7267e681e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122059900"
---
# <a name="accessibility-in-office-projects"></a>Office projelerinde erişilebilirlik

Microsoft Visual Studio ve Microsoft Office, standart erişilebilirlik gereksinimlerini karşılayan özel çözümler oluşturmanıza olanak sağlayan birçok erişilebilirlik özelliği içerir. Microsoft, Web üzerinde erişilebilirlik için kılavuz yayınlar. Ayrıntılar için [Erişilebilirlik Web sitesine](https://www.microsoft.com/accessibility/)bakın.

çoğu durumda, Visual Studio Office projeler erişilebilirlik standartlarını karşılar veya çözümlerinizi erişilebilir hale getirmek için ayarlayabileceğiniz özellikleri sunar. Ancak, sınırlı erişilebilirliği olan bazı özellikler vardır.

[!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="accessibility-at-design-time"></a>Tasarım zamanında erişilebilirlik

### <a name="use-shortcut-keys-in-document-level-projects"></a>Belge düzeyi projelerde kısayol tuşlarını kullanma
 bir Microsoft Office Word belgesi veya bir Microsoft Office Excel çalışma kitabı Visual Studio açıksa, tek seferde yalnızca bir uygulama kısayol tuşu komutlarını alır. varsayılan olarak, Visual Studio tüm kısayol tuşu komutlarını alır, ancak belge odağa sahip olduğunda Word veya Excel, **seçenekler** iletişim kutusunun **klavye Ayarlar** sayfasında **dinamik klavye düzeni** ' ni seçerek alabilir. daha fazla bilgi için bkz. [Microsoft Office sözcük klavye, Microsoft Office klavye Ayarlar, seçenekler iletişim kutusu](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md) ve [Microsoft Office Excel klavye, Microsoft Office klavye Ayarlar, seçenekler iletişim kutusu](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md).

### <a name="display-shortcut-keys-for-the-ribbon-in-document-level-projects"></a>Belge düzeyi projelerde şerit için kısayol tuşlarını görüntüle
 bir Word belgesi veya Excel çalışma kitabı Visual Studio açık olduğunda, şeritteki sekmelerin ve denetimlerin kısayol tuşlarını görüntülemek için **Alt** tuşuna basabilirsiniz. Belge veya çalışma kitabı tasarımcıda açıkken kısayol tuşlarını görüntülemek için aşağıdaki adımları gerçekleştirin.

#### <a name="to-view-shortcut-keys-for-ribbon-tabs-and-controls-in-the-designer"></a>Tasarımcıda Şerit sekmeleri ve denetimleri için kısayol tuşlarını görüntülemek için

1. Visual Studio, **araçlar** menüsünde **seçenekler**' e tıklayın.

2. **Office araçları** düğümünü genişletin ve uygun şekilde **Microsoft Office Excel klavye** veya **klavye klavyeyi Microsoft Office** seçin.

3. **Dinamik klavye şemasını** seçin.

     değişikliğin etkili olması için Visual Studio yeniden başlatmanız gerektiğini belirten bir ileti görüntülenir.

4. **Tamam**'a tıklayın.

5. Visual Studio yeniden başlatın ve projenizi yeniden açın.

6. Projeniz için belge veya çalışma kitabı tasarımcısını açın.

7. Şerite için kısayol tuşlarını göstermek için **F6** tuşuna basın.

## <a name="accessibility-at-run-time"></a>Çalışma zamanında erişilebilirlik

### <a name="windows-forms-controls-on-office-documents"></a>Windows Office belgelerde Forms denetimleri
 Windows Forms denetimleri, ekran okuyucular gibi erişilebilirlik yardımlarına yönelik denetim hakkında bilgi sağlamak için erişilebilirlik özelliklerini kullanıma sunar. denetimler belge düzeyi özelleştirmesindeki bir Office belge üzerinde olduğunda, bu erişilebilirlik özelliklerinden faydalanabilirsiniz. daha fazla bilgi için bkz. [Windows Form üzerindeki denetimler için erişilebilirlik bilgileri sağlama](/dotnet/framework/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form).

 ancak, Windows Forms denetimleri bir Excel çalışma kitabında veya Word belgesinde barındırıldığı zaman çalışma zamanında bazı erişilebilirlik sınırlamaları vardır:

- Bir denetimden diğerine Tab yükleyemezsiniz.

- Belgenin yakınlaştırma ayarını %100 dışında bir şeye değiştirdiğinizde belgedeki denetimler devre dışı bırakılır.

  belgelerde Windows Forms denetimlerinin sınırlamaları hakkında daha fazla bilgi için, bkz. [Office belgelerindeki Windows Forms denetimlerinin sınırlamaları](../vsto/limitations-of-windows-forms-controls-on-office-documents.md).

### <a name="actions-panes-and-custom-task-panes"></a>Eylemler bölmeleri ve özel görev bölmeleri
 bir eylemler bölmesi veya özel görev bölmesi odağa sahip olduğunda, denetimlere Windows Forms uygulamasındaki denetimlere erişen şekilde erişirsiniz. İmlecinizi eylemler bölmesi ve belge arasında taşımak için **F6** tuşuna basın.

 Eylemler bölmeleri ve özel görev bölmeleri hakkında daha fazla bilgi için bkz. [eylemler bölmesine genel bakış](../vsto/actions-pane-overview.md) ve [özel görev bölmeleri](../vsto/custom-task-panes.md).

### <a name="display-modes"></a>Görüntüleme modları

Visual Studio, görüntüleme modlarıyla ilgili aşağıdaki sınırlamalara sahiptir:

- bir Word belgesi veya Excel çalışma sayfasındaki denetimler, belgenin yakınlaştırma ayarını %100 dışında bir şeye değiştirdiğinizde devre dışıdır.

- **yeni Project** iletişim kutusu, bir kullanıcı bilgisayarın erişilebilirlik seçeneklerini **Yüksek Karşıtlık kullanacak** şekilde değiştirirse denetimleri doğru görüntülemez.

Bu kısıtlamaları aşmak için büyüteci kullanabilirsiniz. büyüteç, ekranın büyütülmüş bölümünü görüntüleyen ayrı bir pencere oluşturan Windows içindeki bir görüntüleme yardımcı programıdır.

## <a name="see-also"></a>Ayrıca bkz.

- [Office çözümleri geliştirme](../vsto/developing-office-solutions.md)
- [Office belgelerdeki denetimler](../vsto/controls-on-office-documents.md)
- [Engelli kişiler için erişilebilirlik](../ide/reference/accessibility-features-of-visual-studio.md)
- [Visual Studio erişilebilirlik özellikleri](../ide/reference/accessibility-features-of-visual-studio.md)