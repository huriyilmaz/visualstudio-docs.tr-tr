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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5311c9a910c3140d5a5053a42befe7ed7f5b1278
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651118"
---
# <a name="toolbox"></a>Araç Kutusu

**Araç kutusu** penceresi, Visual Studio projelerine ekleyebileceğiniz denetimleri görüntüler. Araç kutusunu açmak için **Görünüm** menüsünde **araç kutusu** ' nu seçin.

![Araç kutusu penceresi](media/toolbox.png)

Kullandığınız tasarımcı yüzeyine farklı denetimleri sürükleyip bırakabilir ve denetimleri yeniden boyutlandırabilir ve yerleştirebilirsiniz.

Araç kutusu, bir XAML dosyasının Tasarımcı görünümü gibi tasarımcı görünümleriyle birlikte görüntülenir. **Araç kutusu** yalnızca geçerli tasarımcıda kullanılabilecek denetimleri görüntüler. Görüntülenen öğeleri daha fazla filtrelemek için **araç kutusu** içinde arama yapabilirsiniz.

> [!NOTE]
> Bazı proje türleri için **araç kutusu** herhangi bir öğeyi gösteremeyebilir.

Projenizin hedeflediği .NET sürümü araç kutusu 'nda görünen denetim kümesini de etkiler. Gerekirse, projenin özellik sayfalarından hedef Framework sürümünü değiştirebilirsiniz. **Çözüm Gezgini**' de proje düğümünü seçin ve ardından menü çubuğunda **Proje**  > **ProjectName Özellikler**' i seçin. **Uygulama** sekmesinde **hedef çerçeve** açılır öğesini kullanın.

## <a name="manage-the-toolbox-window-and-its-controls"></a>Araç kutusu penceresini ve denetimlerini yönetme

Varsayılan **araç kutusu** , VISUAL Studio IDE 'nin sol tarafında daraltılır ve imleç onun üzerine taşındığında görüntülenir. İmleci taşıdığınızda açık kalması için araç **kutusunu** sabitleyebilir (araç çubuğundaki **sabitleme** simgesine tıklayarak). Ayrıca **araç kutusu** penceresini çıkarabilir ve ekranınızdaki herhangi bir yere sürükleyebilirsiniz. Araç çubuğuna sağ tıklayıp seçeneklerden birini seçerek **araç kutusunu** sabitleyebilir, çıkarabilir ve gizleyebilirsiniz.

Sağ tıklama menüsünde aşağıdaki komutları kullanarak bir **araç kutusu** sekmesindeki öğeleri yeniden düzenleyebilir veya özel sekmeler ve öğeler ekleyebilirsiniz:

- **Öğeyi yeniden adlandır** -seçili öğeyi yeniden adlandırır.

- **Tümünü göster** -tüm olası denetimleri gösterir (yalnızca geçerli Tasarımcı için geçerli olanları değil).

- **Liste görünümü** -denetimleri dikey bir listede gösterir. İşaretlenmezse, denetimler yatay olarak görüntülenir.

- **Öğeleri seç** - **araç**kutusunda görünen öğeleri belirleyebilmeniz Için **araç kutusu öğelerini Seç** iletişim kutusunu açar. Onay kutusunu seçerek veya temizleyerek bir öğeyi gösterebilir veya gizleyebilirsiniz.

- **Öğeleri alfabetik olarak Sırala** -öğeleri ada göre sıralar.

- **Araç çubuğunu Sıfırla** -varsayılan **araç kutusu** ayarlarını ve öğelerini geri yükler.

- **Sekme Ekle** -yeni bir **araç kutusu** sekmesi ekler.

- **Yukarı taşı** -seçili öğeyi yukarı taşır.

- **Aşağı taşı** -seçili öğeyi aşağı taşır.

## <a name="create-and-distribute-custom-toolbox-controls"></a>Özel araç kutusu denetimleri oluşturma ve dağıtma

[Windows Presentation Foundation](../../extensibility/creating-a-wpf-toolbox-control.md) veya [Windows Forms](../../extensibility/creating-a-windows-forms-toolbox-control.md)tabanlı bir proje şablonuyla başlayarak, özel **araç kutusu** denetimleri oluşturabilirsiniz. Daha sonra özel denetiminizi takım matları ' ne dağıtabilir veya [araç kutusu denetimleri yükleyicisini](http://download.microsoft.com/download/8/3/6/836657BD-9CCB-4ED4-B9D2-FB769473B284/TCI_whitepaper.docx)kullanarak Web 'de yayımlayabilirsiniz.

## <a name="help-on-toolbox-tabs"></a>Araç kutusu sekmelerinde yardım

Aşağıdaki konularda, kullanılabilir **araç kutusu** sekmelerinin bazıları hakkında daha fazla bilgi sağlanmaktadır:

- [Araç Kutusu, Veri Sekmesi](../../ide/reference/toolbox-data-tab.md)
- [Araç Kutusu, Bileşenler Sekmesi](../../ide/reference/toolbox-components-tab.md)
- [Araç Kutusu, HTML Sekmesi](../../ide/reference/toolbox-html-tab.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Araç kutusu öğelerini, WPF bileşenlerini seçin](choose-toolbox-items-wpf-components.md)