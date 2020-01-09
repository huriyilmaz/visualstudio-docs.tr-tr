---
title: 'İş Akışı Tasarımcısı-nasıl yapılır: araç kutusuna etkinlik ekleme'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: b3a8a785-5928-457a-8a50-30267e29503d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d3cde4f3a41a1a07f982f85c0c19e9f16b047068
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593934"
---
# <a name="how-to-add-activities-to-the-toolbox"></a>Nasıl yapılır: araç kutusuna etkinlik ekleme

Etkinlikler çözümünüzdeki **araç kutusuna** birkaç farklı şekilde eklenebilir. Bunları geçerli projenizin içinden ekleyebilir, farklı bir projeden başvurabilir veya farklı bir derlemeden bunlara başvurabilirsiniz.

## <a name="to-add-an-activity-from-within-your-current-project"></a>Geçerli projenizin içinden etkinlik eklemek için

1. Geçerli iş akışı projenize yeni bir özel etkinlik ekleyin. Projenize yeni bir özel etkinlik ekleme hakkında daha fazla bilgi için bkz. [nasıl yapılır: bir Iş akışı projesine yeni öğe ekleme](../workflow-designer/how-to-add-a-new-item-to-a-workflow-project.md).

2. Etkinliğinizi özel mantık ekleyin.

3. Projeyi oluşturun. Yapı başarılı olduysa, "\<*Project name*>" adlı **araç kutusundaki** yeni bir kategori, söz konusu kategoriye dahil edilen özel etkinlikle görüntülenir.

    > [!NOTE]
    > Araç kutusu sıfırlandığında, çözüm yeniden derlense bile özel etkinlikler kaldırılır. Araç kutusunu, sıfırlandıktan sonra özel etkinliklerle yeniden doldurmak için Visual Studio 'Yu yeniden başlatın.

    > [!NOTE]
    > Araç kutusu yalnızca belirli bir adın bir etkinliğini gösterebilir. Farklı derlemelerden iki etkinlik aynı sınıf adına sahip ise, yalnızca bir tane görüntülenir.

    > [!NOTE]
    > Uygulama etki alanı, düzenleyici örnekleri arasında paylaşılır; statik değişkenler kullanılırsa, bu bunlar aynı zamanda düzenleyici örnekleri arasında paylaşılır. Bu istenen davranış değilse, değişken örnekleri izlemek için bir hizmetin kullanılması gerekir. Tasarımcı içindeki hizmetleri kullanma hakkında bilgi için bkz. [Modlıdıtem Editing bağlamını kullanma](/dotnet/framework/windows-workflow-foundation/using-the-modelitem-editing-context) .

## <a name="to-add-an-activity-from-within-a-different-project"></a>Farklı bir proje içinden etkinlik eklemek için

1. En az bir iş akışı projesi ve özel etkinlik kitaplığı projesi ya da özel bir etkinliği tanımlayan başka bir iş akışı projesi içeren bir çözüm açın.

2. Her iki projeyi de derleyin. Derlemeler başarılı olduysa, **araç kutusundaki** "\<*Project Name*>" adlı yeni bir kategori, bu kategoriye dahil edilen özel etkinlikle görüntülenir.

## <a name="to-add-an-activity-to-the-toolbox-from-an-assembly"></a>Bir derlemeden araç kutusuna etkinlik eklemek için

1. Bir iş akışı çözümü açın.

2. **Araçlar** menüsünde **araç kutusu öğelerini Seç**' i seçin.

3. **Araç kutusu öğelerini Seç** iletişim kutusunda, **System. Activities bileşenleri** sekmesini seçin ve ardından Ekle ' **ye tıklayarak eklemek istediğiniz özel** etkinliği içeren derlemeye gidin.

4. Derlemeyi seçin ve **Tamam**' a tıklayın. Özel etkinlik bileşeni Bileşen listesine eklenir ve otomatik olarak seçilir.

    1. İletişim kutusunu kapatmak için **Tamam** ' ı tıklatın.

5. Araç kutusunu görüntülemek için, **Görünüm** menüsünden **araç kutusu** ' nu seçin.

6. Özel etkinlik, öğe eklenmeden önce odak edilen kategorinin altındaki **araç kutusunda** görüntülenir. Örneğin, araç kutusu öğesi eklenmeden önce **araç kutusunda** **genel** kategori seçildiyse, etkinlik **genel** kategorinin altında görüntülenir.

## <a name="see-also"></a>Ayrıca bkz.

- [İş Akışı Tasarımcısını Kullanma](developing-applications-with-the-workflow-designer.md)
