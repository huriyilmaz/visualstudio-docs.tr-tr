---
title: Sürüklemede oluşturularak denetimi ayarlama
description: Veri Kaynakları penceresinden WPF tasarımcısına veya Windows Forms tasarımcısına sürüklerken oluşturulacak denetimin nasıl ayar Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Data Sources Window, select controls
- Windows Forms, displaying data
- data [Visual Studio], displaying on Windows Forms
- data [Visual Studio], Data Sources window
ms.assetid: 20597ff8-0c98-43ec-8fb1-05376804ba48
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 38d43074275db57180938e20fc242ff0a1524711
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631179"
---
# <a name="set-the-control-to-be-created-when-dragging-from-the-data-sources-window"></a>Veri Kaynakları penceresinden sürüklendiğinde denetimin oluşturulmasını ayarlama

Veri Kaynakları penceresindeki öğeleri WPF  tasarımcısına sürükleyerek veya Form tasarımcısına sürükleyerek Windows denetimler oluşturabilirsiniz. Veri Kaynakları **penceresindeki her** öğe, tasarımcıya sürüklenerek oluşturulan varsayılan bir denetime sahip olur. Ancak, farklı bir denetim oluşturabilirsiniz.

## <a name="set-the-controls-to-be-created-for-data-tables-or-objects"></a>Veri tabloları veya nesneler için oluşturulacak denetimleri ayarlama

Veri Kaynakları penceresinden veri tablolarını  veya nesneleri temsil eden öğeleri sürüklemeden önce, tüm verileri tek bir denetimde görüntülemeyi veya her sütunu veya özelliği ayrı bir denetimde görüntülemeyi seçebilirsiniz.

Bu bağlamda nesne terimi *özel* bir iş nesnesine, bir varlığa (Varlık Veri Modeli) veya bir hizmet tarafından döndürülen nesneye başvurur.

### <a name="to-set-the-controls-to-be-created-for-data-tables-or-objects"></a>Veri tabloları veya nesneler için oluşturulacak denetimleri ayarlamak için

1. **WPF tasarımcısının veya** Windows **Forms tasarımcısının açık** olduğundan emin olun.

2. Veri **Kaynakları penceresinde,** ayarlamak istediğiniz veri tablosu veya nesneyi temsil eden öğeyi seçin.

   > [!TIP]
   > Veri **Kaynakları penceresi açık** yoksa Diğer Kaynakları Görüntüle'yi seçerek Windows   >    >  **açabilirsiniz.**

3. Öğenin açılan menüsüne tıklayın ve ardından menüde aşağıdaki öğelerden birini tıklatın:

    - Her veri alanını ayrı bir denetimde görüntülemek için Ayrıntılar'a **tıklayın.** Veri öğesini tasarımcıya sürüklerken, bu eylem üst veri tablosu veya nesnesinin her sütunu veya özelliği için farklı bir veriye bağlı denetim ve her denetim için etiketler oluşturur.

    - Tüm verileri tek bir denetimde görüntülemek için, bir WPF uygulamasında **DataGrid** veya **List** gibi listeden farklı bir denetim seçin veya Windows Forms uygulamasında **DataGridView** seçin.

    Kullanılabilir denetimlerin listesi açık tasarımcıya, projenizin hedeflerine hangi .NET sürümünün ve Araç Kutusuna veri bağlamayı destekleyen özel denetimler ekip **eklemenize bağlıdır.** Oluşturmak istediğiniz denetim kullanılabilir denetim listesinde yoksa, denetimi listeye ekleyebilirsiniz. Daha fazla bilgi için [Bkz. Veri Kaynakları penceresine özel denetimler ekleme.](../data-tools/add-custom-controls-to-the-data-sources-window.md)

    Veri Kaynakları penceresindeki veri tabloları veya nesneler için denetim listesine eklenilen özel bir  Windows Forms denetimi oluşturma hakkında bilgi edinmek için bkz. Karmaşık veri bağlamayı destekleyen Windows Forms kullanıcı [denetimi oluşturma.](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)

## <a name="set-the-controls-to-be-created-for-data-columns-or-properties"></a>Veri sütunları veya özellikleri için oluşturulacak denetimleri ayarlama

Veri Kaynakları penceresinden bir sütunu veya nesnenin özelliğini  temsil eden bir öğeyi tasarımcıya sürüklemeden önce, denetimi oluşturulacak şekilde ayarlayın.

### <a name="to-set-the-controls-to-be-created-for-columns-or-properties"></a>Sütunlar veya özellikler için oluşturulacak denetimleri ayarlamak için

1. **WPF tasarımcısının veya** Windows **Forms tasarımcısının açık** olduğundan emin olun.

2. Veri Kaynakları **penceresinde,** sütunlarını veya özelliklerini görüntülemek için istenen tabloyu veya nesneyi genişletin.

3. Denetimin oluşturulacak şekilde ayarlamak istediğiniz her sütunu veya özelliği seçin.

4. Sütun veya özelliğin açılan menüsüne tıklayın ve öğe tasarımcıya sürüklendikten sonra oluşturmak istediğiniz denetimi seçin.

     Kullanılabilir denetimlerin listesi hangi tasarımcıya açık olduğunu, projenizin hangi sürümünü hedefledklerine ve Araç Kutusu'nda veri bağlamayı destekleyen özel **denetimlere bağlıdır.** Oluşturmak istediğiniz denetim kullanılabilir denetimler listesinde yer alıyorsa, denetimi listeye ekleyebilirsiniz. Daha fazla bilgi için [Bkz. Veri Kaynakları penceresine özel denetimler ekleme.](../data-tools/add-custom-controls-to-the-data-sources-window.md)

     Veri Kaynakları penceresinde veri sütunları veya özellikleri için denetim listesine eklenilen  özel bir denetim oluşturma hakkında bilgi edinmek için bkz. Basit veri bağlamayı destekleyen [Windows Forms kullanıcı denetimi oluşturma.](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md)

     Sütun veya özellik için denetim oluşturmak istemiyorsanız açılan **menüden Hiçbiri'yi** seçin. Bu, üst tabloyu veya nesneyi tasarımcıya sürüklemek ancak belirli bir sütunu veya özelliği eklemek istemiyorsanız kullanışlıdır.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md)
