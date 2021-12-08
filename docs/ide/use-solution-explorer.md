---
title: Çözüm Gezgini hakkında bilgi edinin
description: dosyalarınızı, projelerinizi ve çözümlerinizi oluşturmak & yönetmek için Visual Studio Çözüm Gezgini araç penceresini nasıl kullanabileceğinizi öğrenin.
ms.date: 09/30/2021
ms.topic: conceptual
ms.custom: contperf-fy22q1
f1_keywords:
- vs.addnewitem
helpviewer_keywords:
- solution explorer [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 11cc124fa3f8601ffb6d3ea621ab9bb709b60246
ms.sourcegitcommit: 64d6c5cf93984bbb22812577af17128cd2239f79
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/08/2021
ms.locfileid: "134366936"
---
# <a name="learn-about-solution-explorer"></a>Çözüm Gezgini hakkında bilgi edinin

Çözüm Gezgini araç penceresini kullanarak çözümünüzü ve projelerinizi yönetebilir & yönetebilir ve kodunuzla etkileşim & görüntüleyebilirsiniz. Bu makalede, bunu yapmanıza yardımcı olan kullanıcı arabirimi (UI) seçeneklerini ayrıntılarız.

> [!NOTE]
> bu konu yalnızca Windows Visual Studio için geçerlidir.

## <a name="tool-window"></a>Araç penceresi

başlamak için, iki projenin bulunduğu açık bir C# konsol çözümüyle [Visual Studio ıde](../get-started/visual-studio-ide.md)'deki Çözüm Gezgini araç penceresine göz atalım.

[![Visual Studio Çözüm Gezgini araç penceresinin açıklamalı ekran görüntüsü.](media/solution-explorer-tool-window.png)](media/solution-explorer-tool-window.png#lightbox)

Araç penceresi aşağıdaki UI (Kullanıcı arabirimi) öğelerini içerir:

- Dosyalarınızın nasıl göründüğünü denetleyebileceğiniz **menü çubuğu**
- Belirli dosya ve dosya türlerini arayabileceğiniz **arama çubuğu**
- Dosyalarınızı, projelerinizi ve & çözümlerini görüntüleyebileceğiniz ve yönetebileceğiniz **ana pencere**
- Çözümünüzü yönetebileceğiniz **Çözüm düğümü**
- **Project**, projenizi yönetebileceğiniz bir düğüm
- Çözüm & proje bağımlılıklarınızı yönetebileceğiniz **Bağımlılıklar düğümü**
- Programınızı veya uygulamanızı görüntüleyebileceğiniz, düzenleyebileceğiniz ve yönetebileceğiniz **program düğümü**(uygulama)
- ekip ile projelerde işbirliği yapmak için Visual Studio içinde git & GitHub kullanabileceğiniz **[git değişiklikleri sekmesi](../version-control/git-with-visual-studio.md?view=vs-2019&preserve-view=true#git-changes-window-in-visual-studio-2019)**

> [!TIP]
> Çözüm Gezgini araç penceresini görmüyorsanız,   >  **Çözüm Gezgini** görünüm ' ü kullanarak veya **Ctrl** + **Alt** + **L** tuşlarına basarak Visual Studio menü çubuğundan açabilirsiniz.

## <a name="menu-bar"></a>Menü çubuğu

Devam etmek için Çözüm Gezgini menü çubuğuna daha yakından göz atalım.

![Visual Studio ' de Çözüm Gezgini menü çubuğunun açıklamalı ekran görüntüsü.](media/solution-explorer-menu-bar.png)

Menü çubuğu, soldan sağa aşağıdaki UI öğelerini içerir:

- **Geri** düğmesi, arama sonuçları arasında geçiş yapmak için
- **İleri** düğmesi, arama sonuçları arasında geçiş yapmak için
- **Ana** düğme, varsayılan görünüme geri dönmek için
- **Görünümleri Değiştir** düğmesi, çözümler ve kullanılabilir görünümler arasında geçiş yapmak için
- Bekleyen değişiklikler içeren açık dosyaları veya dosyaları görüntülemek için, **bekleyen değişiklikler filtre** düğmesi & açılan menü
- Kod düzenleyicisinden bir dosya bulmak için **etkin belge Ile Eşitle** düğmesi
- Yalnızca bir işlev veya paket gibi bir bağımlılık seçtiğinizde görüntülenen **Yenile** düğmesi
- Ana penceredeki dosya görünümünü daraltmak için **Tümünü Daralt** düğmesi
- **Tüm dosyaları göster** düğmesi, [yüklenmeyen projeler](filtered-solutions.md#toggle-unloaded-project-visibility) dahil tüm dosyaları görüntülemek için
- **Özellikler** düğmesi, belirli dosya ve bileşenlerin ayarlarını görüntülemek ve değiştirmek için
- Seçili **öğeleri Önizle** düğmesi, seçilen bir dosyayı veya bileşeni kod düzenleyicisinde görüntülemek için

## <a name="context-menu"></a>Bağlam menüsü

Çözüm Gezgini, bağlam menüsünü kullanarak etkileşime girebilmeniz için çeşitli seçenekler vardır. Bir C# uygulaması için aşağıdaki ekran görüntüsünde, **çözüm** düğümüne sağ tıkladığınızda görüntülenen bağlam menüsü seçenekleri gösterilmektedir.

:::image type="content" source="media/solution-explorer-context-menu.png" alt-text="Çözüm Gezgini ' de sağ tıklama bağlam menüsünün ekran görüntüsü.":::

**Çözüm** düğümündeki bağlam menüsünde gördükleriniz, proje türüne, programlama diline veya platforma göre de değişir. aşağıdaki ekran görüntüsünde, bir C# uygulaması için aşağıdaki ek seçenekler vurgulanmaktadır: **Project bağımlılıklar**, **Project derleme sırası**, **başlangıç projelerini ayarlama** ve bir **Git** uç menüsü. Bu ek seçenekler genellikle bir çözüme başka bir proje eklediğinizde ve sonra bir depoya eklediğinizde görüntülenir.

:::image type="content" source="media/solution-explorer-context-menu-extra-items.png" alt-text="Ek seçeneklerle Çözüm Gezgini ' de sağ tıklama bağlam menüsünün ekran görüntüsü.":::

## <a name="add-menu"></a>Menü ekle

Çözüm Gezgini bağlam menüsünde, en faydalı seçeneklerden biri, **ekleme** öncesi menü ' dir. Bundan sonra bir çözüme [başka bir proje ekleyebilirsiniz](../get-started/csharp/tutorial-console-part-2.md#add-another-project) . Ayrıca, bir projeye bir [öğe ekleyebilir](reference/add-new-item-command.md) ve daha fazlasını yapabilirsiniz.

:::image type="content" source="media/solution-explorer-context-menu-add-flyout.png" alt-text="Çözüm Gezgini ' de sağ tıklama kısayol menüsünün ekran görüntüsü.":::

**ekleme** menüsünü **çözüm** düğümünden, **Project** düğümünden veya **bağımlılıklar** düğümünden görüntüleyebilirsiniz. Seçenekler, kullandığınız düğüme göre farklılık gösterir.

Çözüm Gezgini 'daki bağlam menüsünü kullanarak öğe ve proje ekleme konusunda size yol gösteren bir öğretici için, [projelere ve çözümlere giriş](../get-started/tutorial-projects-solutions.md#add-an-item-to-the-project) sayfasına bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio çözüm ve projeler nelerdir?](solutions-and-projects-in-visual-studio.md)
- [Visual Studio 'de pencere düzenlerini özelleştirme](customizing-window-layouts-in-visual-studio.md)
