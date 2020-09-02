---
title: Office projelerinde erişilebilirlik
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8bd74f4d61c74a4dc348f7a615e103b283a15fc0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "73189625"
---
# <a name="accessibility-in-office-projects"></a>Office projelerinde erişilebilirlik

Microsoft Visual Studio ve Microsoft Office, standart erişilebilirlik gereksinimlerini karşılayan özel çözümler oluşturmanıza olanak sağlayan birçok erişilebilirlik özelliği içerir. Microsoft, Web üzerinde erişilebilirlik için kılavuz yayınlar. Ayrıntılar için [Erişilebilirlik Web sitesine](https://www.microsoft.com/accessibility/)bakın.

Çoğu durumda, Visual Studio 'daki Office projeleri erişilebilirlik standartlarını karşılar veya çözümlerinizi erişilebilir hale getirmek için ayarlayabileceğiniz özellikleri sunar. Ancak, sınırlı erişilebilirliği olan bazı özellikler vardır.

[!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="accessibility-at-design-time"></a>Tasarım zamanında erişilebilirlik

### <a name="use-shortcut-keys-in-document-level-projects"></a>Belge düzeyi projelerde kısayol tuşlarını kullanma
 Visual Studio 'da bir Microsoft Office Word belgesi veya Microsoft Office Excel çalışma kitabı açık olduğunda, tek seferde yalnızca bir uygulama kısayol tuşu komutlarını alır. Varsayılan olarak, Visual Studio tüm kısayol tuşu komutlarını alır, ancak **Seçenekler** Iletişim kutusunun **klavye ayarları** sayfasında **dinamik klavye düzeni** ' ni seçerek Word veya Excel 'in bu dosyayı almasını sağlayabilirsiniz. Daha fazla bilgi için bkz. [Microsoft Office sözcük klavye, Microsoft Office Klavye ayarları, Seçenekler iletişim kutusu](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md) ve [Microsoft Office Excel klavye, Microsoft Office Klavye ayarları, Seçenekler iletişim kutusu](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md).

### <a name="display-shortcut-keys-for-the-ribbon-in-document-level-projects"></a>Belge düzeyi projelerde şerit için kısayol tuşlarını görüntüle
 Visual Studio 'da bir Word belgesi veya Excel çalışma kitabı açık olduğunda, Şeritteki sekmelerin ve denetimlerin kısayol tuşlarını görüntülemek için **alt** tuşuna basabilirsiniz. Belge veya çalışma kitabı tasarımcıda açıkken kısayol tuşlarını görüntülemek için aşağıdaki adımları gerçekleştirin.

#### <a name="to-view-shortcut-keys-for-ribbon-tabs-and-controls-in-the-designer"></a>Tasarımcıda Şerit sekmeleri ve denetimleri için kısayol tuşlarını görüntülemek için

1. Visual Studio 'da, **Araçlar** menüsünde **Seçenekler**' e tıklayın.

2. **Office Araçları** düğümünü genişletin ve uygun şekilde **Excel klavye Microsoft Office** veya **Microsoft Office sözcük klavye**' yi seçin.

3. **Dinamik klavye şemasını**seçin.

     Değişikliğin etkili olması için Visual Studio 'Yu yeniden başlatmanız gerektiğini belirten bir ileti görüntülenir.

4. **Tamam**’a tıklayın.

5. Visual Studio 'Yu yeniden başlatın ve projenizi yeniden açın.

6. Projeniz için belge veya çalışma kitabı tasarımcısını açın.

7. Şerite için kısayol tuşlarını göstermek için **F6** tuşuna basın.

## <a name="accessibility-at-run-time"></a>Çalışma zamanında erişilebilirlik

### <a name="windows-forms-controls-on-office-documents"></a>Office belgelerindeki denetimleri Windows Forms
 Windows Forms denetimleri, ekran okuyucular gibi erişilebilirlik yardımlarına yönelik denetim hakkında bilgi sağlamak için erişilebilirlik özelliklerini kullanıma sunar. Denetimler belge düzeyi özelleştirmesindeki bir Office belgesinde olduğunda, bu erişilebilirlik özelliklerinden faydalanabilirsiniz. Daha fazla bilgi için bkz. [Windows formundaki denetimler için erişilebilirlik bilgileri sağlama](/dotnet/framework/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form).

 Ancak, Windows Forms denetimleri bir Excel çalışma kitabında veya Word belgesinde barındırıldığı zaman çalışma zamanında bazı erişilebilirlik sınırlamaları vardır:

- Bir denetimden diğerine Tab yükleyemezsiniz.

- Belgenin yakınlaştırma ayarını %100 dışında bir şeye değiştirdiğinizde belgedeki denetimler devre dışı bırakılır.

  Belgelerde Windows Forms denetimlerinin sınırlamaları hakkında daha fazla bilgi için bkz. [Office belgelerindeki Windows Forms denetimlerinin sınırlamaları](../vsto/limitations-of-windows-forms-controls-on-office-documents.md).

### <a name="actions-panes-and-custom-task-panes"></a>Eylemler bölmeleri ve özel görev bölmeleri
 Bir eylemler bölmesi veya özel görev bölmesi odağa sahip olduğunda, denetimlere Windows Forms uygulamasındaki denetimlere erişen şekilde erişirsiniz. İmlecinizi eylemler bölmesi ve belge arasında taşımak için **F6**tuşuna basın.

 Eylemler bölmeleri ve özel görev bölmeleri hakkında daha fazla bilgi için bkz. [eylemler bölmesine genel bakış](../vsto/actions-pane-overview.md) ve [özel görev bölmeleri](../vsto/custom-task-panes.md).

### <a name="display-modes"></a>Görüntüleme modları

Visual Studio, görüntüleme modlarıyla ilgili aşağıdaki sınırlamalara sahiptir:

- Bir Word belgesi veya Excel çalışma sayfasındaki denetimler, belgenin yakınlaştırma ayarını %100 dışında bir şeye değiştirdiğinizde devre dışı bırakılır.

- **Yeni proje** iletişim kutusu, bir Kullanıcı bilgisayarın erişilebilirlik seçeneklerini **yüksek karşıtlık kullanacak**şekilde değiştirirse, denetimleri doğru görüntülemez.

Bu kısıtlamaları aşmak için büyüteci kullanabilirsiniz. Büyüteç, ekranın büyütülmüş bir bölümünü görüntüleyen ayrı bir pencere oluşturan Windows 'daki bir görüntüleme yardımcı programıdır.

## <a name="see-also"></a>Ayrıca bkz.

- [Office çözümleri geliştirme](../vsto/developing-office-solutions.md)
- [Office belgelerindeki denetimler](../vsto/controls-on-office-documents.md)
- [Engelli kişiler için erişilebilirlik](../ide/reference/accessibility-features-of-visual-studio.md)
- [Visual Studio 'nun erişilebilirlik özellikleri](../ide/reference/accessibility-features-of-visual-studio.md)