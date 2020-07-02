---
title: 'Nasıl yapılır: Outlook eklenti projesine form bölgesi ekleme'
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VSTO.NewFormRegionWizard.Page1
- VSTO.NewFormRegionWizard.Page3
- VSTO.NewFormRegionWizard.Page2
- VSTO.NewFormRegionWizard.Page0
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], adding
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a03ba05226720913d48dc1828dcb849bee72d17e
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85538404"
---
# <a name="how-to-add-a-form-region-to-an-outlook-add-in-project"></a>Nasıl yapılır: Outlook eklenti projesine form bölgesi ekleme
  **Yeni Outlook form bölgesi** Sihirbazı 'nı kullanarak standart veya özel bir Microsoft Office Outlook formunu genişletmek için form bölgesi oluşturun. Visual Studio 'da yeni bir form bölgesi oluşturabilir ve Kullanıcı arabirimini tasarlayabilirsiniz veya Outlook 'ta tasarlanan bir form bölgesini içeri aktarabilir ve Visual Basic veya C# kodu ekleyebilirsiniz.

 Başka bir Outlook projesinde kullandığınız bir Outlook form bölgeniz varsa, **var olan öğe Ekle** iletişim kutusunu kullanarak GEÇERLI Outlook VSTO eklenti projenizde onu yeniden kullanabilirsiniz. Daha fazla bilgi için bkz. [Outlook form bölgeleri oluşturma](../vsto/creating-outlook-form-regions.md).

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

### <a name="to-add-a-new-form-region-to-an-outlook-project"></a>Outlook projesine yeni bir form bölgesi eklemek için

1. ' De bir Outlook VSTO eklentisi projesi açın veya oluşturun [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'Da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. **Çözüm Gezgini**' de Outlook VSTO eklentisi proje düğümünü seçin.

3. **Proje** menüsünde **Yeni öğe Ekle**' ye tıklayın.

4. **Yeni öğe Ekle** Iletişim kutusunda **Outlook form bölgesi**' ni seçin.

5. **Ad** kutusuna form bölgesi için bir ad yazın ve ardından **Ekle**' ye tıklayın.

     **Newoutlook form bölgesi** Sihirbazı başlar.

6. **Form bölgesini nasıl oluşturmak Istediğinizi seçin** sayfasında, yönetilen denetimleri bir görsel tasarımcıya sürükleyerek veya Outlook 'ta tasarlanan form bölgesini içeri aktararak form bölgesini tasarlamak isteyip istemediğinizi seçin.

    > [!NOTE]
    > Outlook 'ta tasarlanan bir form bölgesini içeri aktarmayı seçerseniz, bir Outlook form depolama (*. ofs*) dosyasının konumunu belirtmeniz gerekir. Yönetilen denetimleri Outlook 'ta tasarladığınız form bölgesine ekleyemezsiniz; yalnızca mevcut kullanıcı arabiriminin arkasına kod ekleyebilirsiniz. Daha fazla bilgi için bkz. [Outlook form bölgeleri oluşturma](../vsto/creating-outlook-form-regions.md).

7. Oluşturmak istediğiniz **form bölgesinin türünü seçin** sayfasında, form bölgesi türlerini gözden geçirin ve bir tane seçin ve ardından **İleri**' ye tıklayın. Form bölgesi türleri hakkında daha fazla bilgi için bkz. [Outlook form bölgeleri oluşturma](../vsto/creating-outlook-form-regions.md).

8. **Açıklayıcı metin girin ve görüntüleme tercihlerini seçin** sayfasında, **ad** kutusuna form bölgesi için bir ad yazın. Değiştirme ve değiştirme-tüm form bölge türleri için **başlık** ve **Açıklama** kutuları da mevcuttur.

     Form bölgesini dağıtırken ad, başlık ve açıklamanın Outlook 'ta göründüğü hakkında daha fazla bilgi için, bkz. [Outlook form bölgeleri oluşturma](../vsto/creating-outlook-form-regions.md).

9. Form bölgesinin görünmesini istediğiniz bir veya daha fazla görüntüleme modunu seçin.

     Tüm form bölgesi türleri Inspectors 'da, oluşturma modunda (öğe oluşturmak için) ve okuma modunda (öğeleri görüntülemek için) görünebilir. Bitişik, değişim ve replace-all form bölgesi türleri, okuma bölmesinde de görünebilir.

10. **İleri**’ye tıklayın.

11. **Bu form bölgesini görüntüleyecek ileti sınıflarını belirleyin** sayfasında, standart Outlook ileti sınıfları ' nı seçin veya bir veya daha fazla özel ileti sınıfının adlarını yazın ve ardından **son**' a tıklayın. Daha fazla bilgi için bkz. [form bölgesini bir Outlook ileti sınıfıyla ilişkilendirme](../vsto/associating-a-form-region-with-an-outlook-message-class.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma zamanında form bölgesine erişme](../vsto/accessing-a-form-region-at-run-time.md)
- [Outlook çözümleri](../vsto/outlook-solutions.md)
- [Outlook form bölgeleri oluşturma](../vsto/creating-outlook-form-regions.md)
- [Outlook form bölgeleri oluşturma yönergeleri](../vsto/guidelines-for-creating-outlook-form-regions.md)
- [İzlenecek yol: Outlook form bölgesi tasarlama](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [İzlenecek yol: Outlook 'ta tasarlanan form bölgesini Içeri aktarma](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
- [Outlook form bölgelerindeki özel eylemler](../vsto/custom-actions-in-outlook-form-regions.md)
