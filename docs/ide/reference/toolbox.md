---
title: Araç kutusu penceresi
description: Araç kutusu penceresi ve Visual Studio projelerine ekleyebileceğiniz denetimleri görüntüleme hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 06/01/2020
ms.topic: reference
f1_keywords:
- vs.toolbox.general
- vs.toolbox
helpviewer_keywords:
- Toolbox [Visual Studio]
- custom controls [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 52b7eeefd157e99fc5214f29c220d94fd6e19772
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841906"
---
# <a name="toolbox"></a>Araç Kutusu

**Araç kutusu** penceresi, Visual Studio projelerine ekleyebileceğiniz denetimleri görüntüler. **Araç kutusunu** açmak için menü çubuğundan **Görünüm**  >  **araç kutusunu** seçin veya **CTRL** + **alt** + **X** tuşlarına basın.

![Kapsayıcılar bölümündeki seçenekleri gösteren araç kutusu penceresinin ekran görüntüsü.](media/vs-2019/toolbox.png "Araç kutusu penceresinin ekran görüntüsü")

Kullandığınız tasarımcı yüzeyine farklı denetimleri sürükleyip bırakabilir ve denetimleri yeniden boyutlandırabilir ve yerleştirebilirsiniz.

Araç kutusu, bir XAML dosyasının Tasarımcı görünümü veya Windows Forms bir uygulama projesi gibi tasarımcı görünümleriyle birlikte görüntülenir. **Araç kutusu** yalnızca geçerli tasarımcıda kullanılabilecek denetimleri görüntüler. Görüntülenen öğeleri daha fazla filtrelemek için **araç kutusu** içinde arama yapabilirsiniz.

> [!NOTE]
> Bazı proje türleri için **araç kutusu** herhangi bir öğeyi gösteremeyebilir.

Projenizin hedeflediği .NET sürümü araç kutusu 'nda görünen denetim kümesini de etkiler. Gerekirse, projenin özellik sayfalarından hedef Framework sürümünü değiştirebilirsiniz. **Çözüm Gezgini**' de proje düğümünü seçin ve ardından menü çubuğunda **Proje**  >  **ProjectName Özellikler**' i seçin. **Uygulama** sekmesinde **hedef çerçeve** açılır öğesini kullanın.

::: moniker range="vs-2019"

![Hedef çerçeve açılır penceresinde seçenekleri gösteren uygulama iletişim kutusunun ekran görüntüsü.](media/vs-2019/toolbox-change-dotnet-version.png ".NET sürümünü değiştirebileceğiniz iletişim kutusunun ekran görüntüsü")

::: moniker-end

## <a name="manage-the-toolbox-window-and-its-controls"></a>Araç kutusu penceresini ve denetimlerini yönetme

Varsayılan olarak, **araç kutusu** VISUAL Studio IDE 'nin sol tarafında daraltılır ve imleç onun üzerine taşındığında görüntülenir. İmleci taşıdığınızda açık kalması için araç **kutusunu** sabitleyebilir (araç çubuğundaki **sabitleme** simgesine tıklayarak). Ayrıca **araç kutusu** penceresini çıkarabilir ve ekranınızdaki herhangi bir yere sürükleyebilirsiniz. Araç çubuğuna sağ tıklayıp seçeneklerden birini seçerek **araç kutusunu** sabitleyebilir, çıkarabilir ve gizleyebilirsiniz.

> [!TIP]
> Araç kutusu artık Visual Studio IDE 'nin sol tarafında daraltılamaz olarak yoksa, menü çubuğundan **pencere**  >  **sıfırlama pencere düzeni** ' ni seçerek geri ekleyebilirsiniz.

Sağ tıklama bağlam menüsünde aşağıdaki komutları kullanarak bir **araç kutusu** sekmesindeki öğeleri yeniden düzenleyebilir veya özel sekmeler ve öğeler ekleyebilirsiniz:

- **Öğeyi yeniden adlandır** -seçili öğeyi yeniden adlandırır.

- **Liste görünümü** -denetimleri dikey bir listede gösterir. İşaretlenmezse, denetimler yatay olarak görüntülenir.

- **Tümünü göster** -tüm olası denetimleri gösterir (yalnızca geçerli Tasarımcı için geçerli olanları değil).

- **Öğeleri seç** - **araç** kutusunda görünen öğeleri belirleyebilmeniz Için **araç kutusu öğelerini Seç** iletişim kutusunu açar. Onay kutusunu seçerek veya temizleyerek bir öğeyi gösterebilir veya gizleyebilirsiniz.

- **Öğeleri alfabetik olarak Sırala** -öğeleri ada göre sıralar.

- **Araç çubuğunu Sıfırla** -varsayılan **araç kutusu** ayarlarını ve öğelerini geri yükler.

- **Sekme Ekle** -yeni bir **araç kutusu** sekmesi ekler.

- **Yukarı taşı** -seçili öğeyi yukarı taşır.

- **Aşağı taşı** -seçili öğeyi aşağı taşır.

## <a name="create-and-distribute-custom-toolbox-controls"></a>Özel araç kutusu denetimleri oluşturma ve dağıtma

[Windows Presentation Foundation](../../extensibility/creating-a-wpf-toolbox-control.md) veya [Windows Forms](../../extensibility/creating-a-windows-forms-toolbox-control.md)tabanlı bir proje şablonuyla başlayarak, özel **araç kutusu** denetimleri oluşturabilirsiniz. Daha sonra özel denetiminizi takım matları ' ne dağıtabilir veya [araç kutusu denetimleri yükleyicisini](https://download.microsoft.com/download/8/3/6/836657BD-9CCB-4ED4-B9D2-FB769473B284/TCI_whitepaper.docx)kullanarak Web 'de yayımlayabilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

Per, kullanılabilir **araç kutusu** sekmeleri hakkında daha fazla bilgi edinmek için aşağıdaki bağlantıları kullanın:

- [Araç Kutusu, Veri Sekmesi](../../ide/reference/toolbox-data-tab.md)
- [Araç Kutusu, Bileşenler Sekmesi](../../ide/reference/toolbox-components-tab.md)
- [Araç Kutusu, HTML Sekmesi](../../ide/reference/toolbox-html-tab.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Araç Kutusu öğelerini, WPF bileşenlerini seçme](choose-toolbox-items-wpf-components.md)
