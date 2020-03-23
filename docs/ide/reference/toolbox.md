---
title: Araç kutusu penceresi
ms.date: 01/18/2018
ms.topic: reference
f1_keywords:
- vs.toolbox.general
- vs.toolbox
helpviewer_keywords:
- Toolbox [Visual Studio]
- custom controls [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c7decdb80cd06b1af3230b2926c4ebd37b48e422
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596456"
---
# <a name="toolbox"></a>Araç Kutusu

**Toolbox** penceresi Visual Studio projelerine ekleyebileceğiniz denetimleri görüntüler. Araç Kutusu'nu açmak için **Görünüm** menüsünde **Toolbox'ı** seçin.

![Araç kutusu penceresi](media/toolbox.png)

Farklı denetimleri kullanmakta olduğunuz tasarımcının yüzeyine sürükleyebilir ve bırakabilir ve denetimleri yeniden boyutlandırıp konumlandırabilirsiniz.

Araç kutusu, XAML dosyasının tasarımcı görünümü gibi tasarımcı görünümleriyle birlikte görünür. **Araç kutusu** yalnızca geçerli tasarımcıda kullanılabilecek denetimleri görüntüler. Görünen öğeleri daha fazla filtrelemek için **Toolbox** içinde arama yapabilirsiniz.

> [!NOTE]
> Bazı proje türleri için **Araç Kutusu** herhangi bir öğe göstermeyebilir.

Projenizin hedeflenebildiğin .NET sürümü, Toolbox'ta görünen denetim kümesini de etkiler. Gerekirse hedef çerçeve sürümünü projenin özellik sayfalarından değiştirebilirsiniz. **Çözüm Gezgini'nde**proje düğümünü seçin ve ardından menü çubuğunda **Project** > **projectname Properties'i**seçin. **Uygulama** sekmesinde, **Hedef çerçeve** açılır kullanın.

## <a name="manage-the-toolbox-window-and-its-controls"></a>Araç Kutusu penceresini ve denetimlerini yönetme

Varsayılan olarak **Toolbox** Visual Studio IDE'nin sol tarafında daraltılır ve imleç üzerinde hareket ettirildiğinde görüntülenir. İmleci hareket ettirdiğinizde açık kalması için **Araç Kutusu'nu** (araç çubuğundaki **Pin** simgesine tıklayarak) sabitleyebilirsiniz. Ayrıca **Araç Kutusu** penceresini kullanabilirsiniz ve ekranınızda herhangi bir yere sürükleyin. Araç çubuğunu sağ tıklayarak ve seçeneklerden birini seçerek **Araç Kutusunu** sabitleyebilir, açabilir ve gizleyebilirsiniz.

**Araç Kutusu** sekmesindeki öğeleri yeniden düzenleyebilir veya sağ tıklama menüsünde aşağıdaki komutları kullanarak özel sekmeler ve öğeler ekleyebilirsiniz:

- **Öğeyi yeniden adlandır** - Seçili öğeyi yeniden adlandırır.

- **Tümünü Göster** - Tüm olası denetimleri gösterir (yalnızca geçerli tasarımcıiçin geçerli olanları değil).

- **Liste Görünümü** - Dikey listedeki denetimleri gösterir. İşaretlenmemişse, denetimler yatay olarak görüntülenir.

- **Öğeleri Seçin** - **Araç**Kutusu'nda görünen öğeleri belirtebilmeniz için Araç **Kutusu Öğelerini Seç** iletişim kutusunu açar. Bir öğeyi onay kutusunu seçerek veya temizleyerek gösterebilir veya gizleyebilirsiniz.

- **Öğeleri alfabetik olarak sıralayın** - Öğeleri ada göre sıralayın.

- **Araç Çubuğunu Sıfırla** - Varsayılan **Araç Kutusu** ayarlarını ve öğelerini geri yükler.

- **Sekme Ekle** - Yeni bir **Araç Kutusu** sekmesi ekler.

- **Yukarı Taşı** - Seçili öğeyi yukarı taşır.

- **Aşağı Taşı** - Seçili öğeyi aşağı taşır.

## <a name="create-and-distribute-custom-toolbox-controls"></a>Özel Araç Kutusu denetimleri oluşturma ve dağıtma

Windows Sunu Temeli'ni temel alan bir proje şablonundan veya [Windows](../../extensibility/creating-a-wpf-toolbox-control.md) Formlar'dan başlayarak özel **Araç Kutusu** [denetimleri](../../extensibility/creating-a-windows-forms-toolbox-control.md)oluşturabilirsiniz. Daha sonra özel denetiminizi takım arkadaşlarınıza dağıtabilir veya [Toolbox Controls Installer'ı](https://download.microsoft.com/download/8/3/6/836657BD-9CCB-4ED4-B9D2-FB769473B284/TCI_whitepaper.docx)kullanarak web'de yayınlayabilirsiniz.

## <a name="help-on-toolbox-tabs"></a>Araç Kutusu sekmelerinde yardım

Aşağıdaki konular, kullanılabilir **Araç Kutusu** sekmelerinden bazıları hakkında daha fazla bilgi sağlar:

- [Araç Kutusu, Veri Sekmesi](../../ide/reference/toolbox-data-tab.md)
- [Araç Kutusu, Bileşenler Sekmesi](../../ide/reference/toolbox-components-tab.md)
- [Araç Kutusu, HTML Sekmesi](../../ide/reference/toolbox-html-tab.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Toolbox öğelerini, WPF bileşenlerini seçin](choose-toolbox-items-wpf-components.md)
