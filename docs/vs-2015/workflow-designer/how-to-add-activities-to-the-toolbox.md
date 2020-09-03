---
title: 'Nasıl yapılır: araç kutusuna etkinlik ekleme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: b3a8a785-5928-457a-8a50-30267e29503d
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8fc2af704ab587480913c51cdbc593e6cc0f483a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663462"
---
# <a name="how-to-add-activities-to-the-toolbox"></a>Nasıl Yapılır: Araç Kutusuna Etkinlik Ekleme
Etkinlikler çözümünüzdeki **araç kutusuna** birkaç farklı şekilde eklenebilir. Bunları geçerli projenizin içinden ekleyebilir, farklı bir projeden başvurabilir veya farklı bir derlemeden bunlara başvurabilirsiniz.

### <a name="to-add-an-activity-from-within-your-current-project"></a>Geçerli projenizin içinden etkinlik eklemek için

1. Geçerli iş akışı projenize yeni bir özel etkinlik ekleyin. [!INCLUDE[crabout](../includes/crabout-md.md)] projenize yeni bir özel etkinlik eklemek için bkz. [nasıl yapılır: bir Iş akışı projesine yeni öğe ekleme](../workflow-designer/how-to-add-a-new-item-to-a-workflow-project.md).

2. Etkinliğinizi özel mantık ekleyin.

3. Projeyi derleyin. Yapı başarılı olduysa, "" adlı **araç kutusu** içindeki ve \<*project name*> Bu kategoriye dahil olan özel etkinlik içeren yeni bir kategori görüntülenir.

    > [!NOTE]
    > Araç kutusu sıfırlandığında, çözüm yeniden derlense bile özel etkinlikler kaldırılır. Araç kutusunu, sıfırlandıktan sonra özel etkinliklerle yeniden doldurmak için yeniden başlatın [!INCLUDE[vs2010](../includes/vs2010-md.md)] .

    > [!NOTE]
    > Araç kutusu yalnızca belirli bir adın bir etkinliğini gösterebilir. Farklı derlemelerden iki etkinlik aynı sınıf adına sahip ise, yalnızca bir tane görüntülenir.

    > [!NOTE]
    > Uygulama etki alanı, düzenleyici örnekleri arasında paylaşılır; statik değişkenler kullanılırsa, bu bunlar aynı zamanda düzenleyici örnekleri arasında paylaşılır. Bu istenen davranış değilse, değişken örnekleri izlemek için bir hizmetin kullanılması gerekir. Tasarımcı içindeki hizmetleri kullanma hakkında bilgi için bkz. [Modlıdıtem Editing bağlamını kullanma](https://msdn.microsoft.com/library/7f9f1ea5-0147-4079-8eca-be94f00d3aa1) .

### <a name="to-add-an-activity-from-within-a-different-project"></a>Farklı bir proje içinden etkinlik eklemek için

1. En az bir iş akışı projesi ve özel etkinlik kitaplığı projesi ya da özel bir etkinliği tanımlayan başka bir iş akışı projesi içeren bir çözüm açın.

2. Her iki projeyi de derleyin. Derlemeler başarılı olduysa, **araç kutusundaki** "" adlı ve \<*project name*> Bu kategoriye dahil olan özel etkinlik içeren yeni bir kategori görüntülenir.

### <a name="to-add-an-activity-to-the-toolbox-from-an-assembly"></a>Bir derlemeden araç kutusuna etkinlik eklemek için

1. Bir iş akışı çözümü açın.

2. **Araçlar** menüsünde **araç kutusu öğelerini Seç...** seçeneğini belirleyin.

3. **Araç kutusu öğelerini Seç** iletişim kutusunda, **System. Activities bileşenleri** sekmesini seçin ve ardından **araştır...** ' a tıklayın. eklemek istediğiniz özel etkinliği içeren derlemeye gitmek için.

4. Derlemeyi seçin ve **Tamam**' a tıklayın. Özel etkinlik bileşeni Bileşen listesine eklenir ve otomatik olarak seçilir.

    1. İletişim kutusunu kapatmak için **Tamam** ' ı tıklatın.

5. Araç kutusunu görüntülemek için, **Görünüm** menüsünden **araç kutusu** ' nu seçin.

6. Özel etkinlik, öğe eklenmeden önce odak edilen kategorinin altındaki **araç kutusunda** görüntülenir. Örneğin, araç kutusu öğesi eklenmeden önce **araç kutusunda** **genel** kategori seçildiyse, etkinlik **genel** kategorinin altında görüntülenir.

## <a name="see-also"></a>Ayrıca Bkz.
 [İş Akışı Tasarımcısını Kullanma](../workflow-designer/using-the-workflow-designer.md)