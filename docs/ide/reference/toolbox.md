---
title: Araç kutusu penceresi
description: Araç Kutusu penceresi hakkında bilgi edinmek ve bu pencerenin projelerde ek olarak ek Visual Studio öğrenin.
ms.custom: SEO-VS-2020
ms.date: 06/01/2020
ms.topic: reference
f1_keywords:
- vs.toolbox.general
helpviewer_keywords:
- Toolbox [Visual Studio]
- custom controls [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 068cfa548f2421791e79e9a79f56eb530b9b06aa9cdb3a7951433c2cc3b36e89
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121371911"
---
# <a name="toolbox"></a>Araç Kutusu

Araç **Kutusu penceresinde,** projelerinize ek olarak Visual Studio görüntülenir. Araç Kutusunu **açmak için** menü **çubuğundan Araç** Kutusunu  >  **Görüntüle'yi** seçin veya Ctrl Alt X  + **tuşlarına** + **basın.**

![Kapsayıcılar bölümündeki seçenekleri gösteren Araç Kutusu penceresinin ekran görüntüsü.](media/vs-2019/toolbox.png "Araç Kutusu penceresinin ekran görüntüsü")

Farklı denetimleri kullanmakta olduğu tasarımcının yüzeyine sürükleyip bırakın ve denetimleri yeniden boyutlandırın ve konumlara getirin.

Araç kutusu, XAML dosyasının tasarımcı görünümü veya Windows Forms Uygulaması projesi gibi tasarımcı görünümleriyle birlikte görünür. **Araç kutusu** yalnızca geçerli tasarımcıda kullanılan denetimleri görüntüler. Görünen öğeleri daha **fazla filtrelemek** için Araç Kutusu içinde arama edebilirsiniz.

> [!NOTE]
> Bazı proje türleri için **Araç Kutusu** herhangi bir öğe gösterebildi.

Projenizin hedeflediği .NET sürümü, Araç Kutusu'nda görünen denetim kümelerini de etkiler. Gerekirse projenin özellik sayfalarından hedef çerçeve sürümünü değiştirebilirsiniz. proje adı **Özellikleri'Çözüm Gezgini** proje düğümünü seçin ve ardından menü **çubuğunda proje Project**  >  **seçin.** Uygulama **sekmesinde** Hedef çerçeve **açılan** listesinden seçim yapın.

::: moniker range=">=vs-2019"

![Hedef çerçeve açılan listesinde seçenekleri gösteren Uygulama iletişim kutusunun ekran görüntüsü.](media/vs-2019/toolbox-change-dotnet-version.png ".NET sürümünü değiştirebilirsiniz iletişim kutusunun ekran görüntüsü")

::: moniker-end

## <a name="manage-the-toolbox-window-and-its-controls"></a>Araç Kutusu penceresini ve denetimlerini yönetme

Varsayılan olarak Araç **Kutusu,** IDE'nin sol Visual Studio daraltılmış ve imlecin üzerine taşındığında görünür. Araç Kutusunu **sabitleyebilirsiniz** (araç çubuğundaki Sabitle **simgesine** tıklayarak), imleci taşısanız açık kalması için. Ayrıca Araç Kutusu penceresini **çıkararak** ekran üzerinde herhangi bir yere sürükleyebilirsiniz. Araç çubuğuna sağ tıklar ve **seçeneklerden** birini seçerek Araç Kutusunu yerleştirebilirsiniz, çıkarabilirsiniz ve gizleyebilirsiniz.

> [!TIP]
> Araç Kutusu artık IDE'nin sol tarafında daraltılmış Visual Studio, menü çubuğundan Pencere Sıfırlama Penceresi Düzeni'yi seçerek geri  >   ekleyebilirsiniz.

Sağ tıklama bağlam menüsünde aşağıdaki **komutları kullanarak** Bir Araç Kutusu sekmesindeki öğeleri yeniden düzenleyebilir veya özel sekmeler ve öğeler ekleyebilirsiniz:

- **Öğeyi Yeniden Adlandır** - Seçili öğeyi yeniden adlandırın.

- **Liste Görünümü** - Dikey bir listede denetimleri gösterir. Denetlenmeyen denetimler yatay olarak görünür.

- **Hepsini Göster** - Tüm olası denetimleri (yalnızca geçerli tasarımcı için geçerli olanları değil) gösterir.

- **Öğeleri Seç** - **Araç Kutusunda görünen öğeleri** belirtebilirsiniz. Araç Kutusu Öğelerini Seç iletişim kutusunu **açar.** Bir öğeyi onay kutusunu seçerek veya temizerek gösterebilir veya gizleyebilirsiniz.

- **Öğeleri Alfabetik Olarak Sırala** - Öğeleri adlarına göre sıralar.

- **Araç Çubuğunu** Sıfırla - Varsayılan Araç Kutusu **ayarlarını ve** öğelerini geri yükleme.

- **Sekme Ekle** - Yeni bir **Araç Kutusu sekmesi** ekler.

- **Yukarı Taşı** - Seçili öğeyi yukarı taşır.

- **Aşağı Taşı** - Seçili öğeyi aşağı taşır.

## <a name="create-and-distribute-custom-toolbox-controls"></a>Özel Araç Kutusu denetimleri oluşturma ve dağıtma

Windows Presentation Foundation tabanlı **bir** proje şablonuyla başlayarak veya [Windows](../../extensibility/creating-a-wpf-toolbox-control.md) [Forms'da özel araç kutusu denetimleri oluşturabilirsiniz.](../../extensibility/creating-a-windows-forms-toolbox-control.md) Daha sonra özel denetiminizi ekip arkadaşlarınıza dağıtabilirsiniz veya Araç Kutusu Denetimleri Yükleyicisi'nı [kullanarak web'de yayımlayın.](https://download.microsoft.com/download/8/3/6/836657BD-9CCB-4ED4-B9D2-FB769473B284/TCI_whitepaper.docx)

## <a name="next-steps"></a>Sonraki adımlar

Kullanılabilir Araç Kutusu sekmelerinin bazıları hakkında daha fazla bilgi edinmek için **aşağıdaki bağlantıları** kullanın:

- [Araç Kutusu, Veri Sekmesi](../../ide/reference/toolbox-data-tab.md)
- [Araç Kutusu, Bileşenler Sekmesi](../../ide/reference/toolbox-components-tab.md)
- [Araç Kutusu, HTML Sekmesi](../../ide/reference/toolbox-html-tab.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Araç Kutusu öğelerini, WPF bileşenlerini seçme](choose-toolbox-items-wpf-components.md)
