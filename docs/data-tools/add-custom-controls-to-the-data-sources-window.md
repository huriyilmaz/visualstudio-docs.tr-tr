---
title: Veri kaynakları penceresine özel denetimler ekleme
description: Visual Studio'da Veri Kaynakları penceresine özel denetimler Visual Studio. Bağlanabilir denetimler listesini özelleştirin. İlişkili denetimler ekleyin.
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.datasource.howtoaddcustomcontrol
helpviewer_keywords:
- Data Sources Window, adding controls
- controls [Visual Studio], adding to Data Sources Window
- DefaultBindingPropertyAttribute class, using
- LookupBindingPropertiesAttribute class, using
- ComplexBindingPropertiesAttribute class, using
- Data Sources Window, selecting controls
ms.assetid: 8c43e7d2-ba94-4d9b-96de-3aa971955afd
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.openlocfilehash: 2b29026eb9242dae0526f6022658f65c4a7b0a76
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631629"
---
# <a name="add-custom-controls-to-the-data-sources-window"></a>Veri kaynakları penceresine özel denetimler ekleme

Veri Kaynakları penceresinden bir öğeyi tasarım yüzeyine sürükleyerek veriye bağlı denetim oluşturabilirsiniz. Pencerenin her öğesinde, seçebilirsiniz denetimleri görüntüleyen bir açılan liste vardır. Her öğeyle ilişkili denetim kümesi, öğenin veri türüne göre belirlenir. Oluşturmak istediğiniz denetim listede görünmüyorsa bu konudaki yönergeleri izleyerek denetimi listeye ekleyebilirsiniz.

Veri Kaynakları penceresinde öğeler için oluşturulacak veriye bağlı denetimleri seçme hakkında daha fazla bilgi için bkz. Veri Kaynakları penceresinden sürüklenrken [oluşturulacak denetimi ayarlama.](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)

## <a name="customize-the-bindable-controls-list"></a>Bağlanabilir denetimler listesini özelleştirme

Veri Kaynakları penceresinde belirli bir veri türüne sahip öğeler için kullanılabilir denetimler listesinden denetim eklemek veya kaldırmak için aşağıdaki adımları gerçekleştirin.

### <a name="to-select-the-controls-to-be-listed-for-a-data-type"></a>Bir veri türü için listelene denetimleri seçmek için

1. WPF Tasarımcısı'nın veya Windows Forms Tasarımcısı'nın açık olduğundan emin olun.

2. Veri **Kaynakları penceresinde** pencereye ekley istediğiniz veri kaynağının parçası olan bir öğeye tıklayın ve ardından öğenin açılan menüsüne tıklayın.

   > [!TIP]
   > Veri Kaynakları penceresi açık değilse Diğer Veri Kaynaklarını Görüntüle'yi **seçerek**  >  **Windows**  >  **açın.**

3. Açılan menüde Özelleştir'e **tıklayın.** Aşağıdaki iletişim kutularından biri açılır:

    - Form **Windows açıksa,** Seçenekler **iletişim** kutusunun Veri Kullanıcı Arabirimi **Özelleştirme** sayfası açılır. Daha fazla bilgi için [bkz. Veri Kullanıcı Arabirimi Özelleştirme seçenekleri iletişim kutusu.](../ide/reference/options-windows-forms-designer-data-ui-customization.md)

    - **WPF Tasarımcısı açıksa** Denetim **Bağlamayı Özelleştir iletişim** kutusu açılır.

4. İletişim kutusunda, Veri türü açılan **listesinden bir veri** türü seçin.

    - Bir tablo veya nesne için denetim listesini özelleştirmek için **[Liste] öğesini seçin.**

    - Tablo veya nesnenin özelliğine ait bir sütunun denetim listesini özelleştirmek için, temel alınan veri deposuna ait sütunun veya özelliğin veri türünü seçin.

    - Kullanıcı tanımlı şekillere sahip veri nesnelerini görüntülemek için denetim listesini özelleştirmek için **[Diğer] öğesini seçin.** Örneğin, uygulamanız belirli bir nesnenin birden fazla özelliğinden verileri görüntüleyen özel bir denetime sahipse **[Diğer]** öğesini seçin.

5. İlişkili **denetimler** kutusunda, seçili veri türü için kullanılabilir olması istediğiniz her denetimi seçin veya listeden kaldırmak istediğiniz denetimlerin seçimini temizleyin.

    > [!NOTE]
    > Seçmek istediğiniz denetim İlişkili denetimler **kutusunda** görünmüyorsa, denetimi listeye eklemeniz gerekir. Daha fazla bilgi için [bkz. İlişkili denetimler ekleme.](#add-associated-controls)

6. **Tamam**'a tıklayın.

7. Veri **Kaynakları penceresinde,** az önce bir veya daha fazla denetimi ilişkilendirilmiş veri türüne sahip bir öğeye tıklayın ve ardından öğenin açılan menüsüne tıklayın.

     İlişkili denetimler **kutusunda seçtiğiniz** denetimler artık öğenin açılan menüsünde görünür.

## <a name="add-associated-controls"></a>İlişkili denetimler ekleme

Bir denetimi bir veri türüyle ilişkilendirmek istiyorsanız ancak denetim İlişkili **denetimler kutusunda** görünmüyorsa, denetimi listeye eklemeniz gerekir. Denetimin geçerli çözümde veya başvurulan bir derlemede yer alıyor olması gerekir. Araç Kutusunda da kullanılabilir olması **ve denetimin** veri bağlama davranışını belirten bir özniteliği olması gerekir.

İlişkili denetimler listesine denetim eklemek için:

1. Araç Kutusuna sağ tıklar **ve Öğeleri Seç'i** seçerek **istenen** denetimi Araç Kutusuna **ekleyin.**

     Denetimin aşağıdaki özniteliklerden biri olması gerekir:

    |Öznitelik|Açıklama|
    |---------------|-----------------|
    |<xref:System.ComponentModel.DefaultBindingPropertyAttribute>|Bu özniteliği, bir gibi verilerin tek sütununu (veya özelliğini) görüntülemek için basit denetimler üzerinde <xref:System.Windows.Forms.TextBox> gerçekleştirin.|
    |<xref:System.ComponentModel.ComplexBindingPropertiesAttribute>|Bu özniteliği, bir gibi veri listelerini (veya tablolarını) görüntüleme denetimlerinde <xref:System.Windows.Forms.DataGridView> gerçekleştirin.|
    |<xref:System.ComponentModel.LookupBindingPropertiesAttribute>|Bu özniteliği veri listelerini (veya tablolarını) görüntülemeye yönelik denetimler üzerinde uygulama, ancak aynı zamanda gibi tek bir sütun veya özellik sun ihtiyacı <xref:System.Windows.Forms.ComboBox> vardır.|

2. Form Windows için Seçenekler **iletişim** kutusunda Veri Kullanıcı Arabirimi Özelleştirme **sayfasını** açın. Veya WPF için Denetim Bağlamayı **Özelleştir iletişim** kutusunu açın. Daha fazla bilgi için [bkz. Veri türü için bağlanabilir denetimler listesini özelleştirme.](#customize-the-bindable-controls-list)

3. İlişkili **denetimler** kutusunda, Araç Kutusuna yeni ekley istediğiniz **denetim artık** görüntüleniyor.

    > [!NOTE]
    > Yalnızca geçerli çözüm içinde veya başvurulan bir derlemede bulunan denetimler ilişkili denetimler listesine eklenebilir. (Denetimler ayrıca önceki tablodaki veri bağlama özniteliklerinden birini de uygulamalı.) Verileri Veri Kaynakları penceresinde mevcut olan özel bir denetime bağlamak için denetimi **Araç** Kutusundan tasarım yüzeyine sürükleyin ve  ardından veri kaynakları penceresinden bağlanıp bağlanıp denetime sürükleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Veri Kullanıcı Arabirimi Özelleştirme seçenekleri iletişim kutusu](../ide/reference/options-windows-forms-designer-data-ui-customization.md)
