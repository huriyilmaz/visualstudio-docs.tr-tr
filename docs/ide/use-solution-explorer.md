---
title: Çözüm Gezgini araç penceresi hakkında bilgi edinin
description: dosyalarınızı, projelerinizi ve çözümlerinizi oluşturmak & yönetmek için Visual Studio Çözüm Gezgini araç penceresini nasıl kullanabileceğinizi öğrenin.
ms.date: 06/29/2021
ms.topic: conceptual
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
ms.openlocfilehash: f2334abf43a240b5c187e66b4c0f3a6cc469e14f92d58ba205a3d6a08de335a0
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121317104"
---
# <a name="how-to-use-solution-explorer"></a>Çözüm Gezgini kullanma

Çözüm Gezgini araç penceresini kullanarak çözümünüzü ve projelerinizi yönetebilir & yönetebilir ve kodunuzla etkileşim & görüntüleyebilirsiniz. Bu makalede, bunu yapmanıza yardımcı olan kullanıcı arabirimi (UI) seçeneklerini ayrıntılarız.

> [!NOTE]
> bu konu yalnızca Windows Visual Studio için geçerlidir.

## <a name="solution-explorer-tool-window"></a>Çözüm Gezgini araç penceresi

başlamak için, iki projenin bulunduğu açık bir C# konsol çözümüyle [Visual Studio ıde](../get-started/visual-studio-ide.md)'deki Çözüm Gezgini araç penceresine göz atalım.

[![Visual Studio Çözüm Gezgini araç penceresi.](media/solution-explorer-tool-window.png)](media/solution-explorer-tool-window.png#lightbox)

Araç penceresi aşağıdaki UI (Kullanıcı arabirimi) öğelerini içerir:

- Dosyalarınızın nasıl göründüğünü denetleyebileceğiniz **menü çubuğu**
- Belirli dosya ve dosya türlerini arayabileceğiniz **arama çubuğu**
- Dosyalarınızı, projelerinizi ve & çözümlerini görüntüleyebileceğiniz ve yönetebileceğiniz **ana pencere**
- Çözümünüzü yönetebileceğiniz **Çözüm düğümü**
- **Project**, projenizi yönetebileceğiniz bir düğüm
- Çözüm & proje bağımlılıklarınızı yönetebileceğiniz **Bağımlılıklar düğümü**
- Programınızı veya uygulamanızı görüntüleyebileceğiniz, düzenleyebileceğiniz ve yönetebileceğiniz **program düğümü**(uygulama)
- ekip ile projelerde işbirliği yapmak için Visual Studio içinde git & GitHub kullanabileceğiniz **[git değişiklikleri sekmesi](../version-control/git-with-visual-studio.md?view=vs-2019&preserve-view=true#git-changes-window)**

> [!TIP]
> Çözüm Gezgini araç penceresini görmüyorsanız,   >  **Çözüm Gezgini** görünüm ' ü kullanarak veya **Ctrl** + **Alt** + **L** tuşlarına basarak Visual Studio menü çubuğundan açabilirsiniz.

## <a name="solution-explorer-menu-bar"></a>Çözüm Gezgini menü çubuğu

Devam etmek için Çözüm Gezgini menü çubuğuna daha yakından göz atalım.

![Visual Studio Çözüm Gezgini menü çubuğu.](media/solution-explorer-menu-bar.png)

Menü çubuğu, soldan sağa aşağıdaki UI öğelerini içerir:

- **Geri** düğmesi, arama sonuçları arasında geçiş yapmak için
- **İleri** düğmesi, arama sonuçları arasında geçiş yapmak için
- **Ana** düğme, varsayılan görünüme geri dönmek için
- **Değiştir** düğmesi, çözümler ve kullanılabilir görünümler arasında geçiş yapmak için
- Bekleyen değişiklikler içeren açık dosyaları veya dosyaları görüntülemek için, **bekleyen değişiklikler filtre** düğmesi & açılan menü
- Kod düzenleyicisinden bir dosya bulmak için **etkin belge Ile Eşitle** düğmesi
- Yalnızca bir işlev veya paket gibi bir bağımlılık seçtiğinizde görüntülenen **Yenile** düğmesi
- Ana penceredeki dosya görünümünü daraltmak için **Tümünü Daralt** düğmesi
- **Tüm dosyaları göster** düğmesi, [yüklenmeyen projeler](filtered-solutions.md#toggle-unloaded-project-visibility) dahil tüm dosyaları görüntülemek için
- **Özellikler** düğmesi, belirli dosya ve bileşenlerin ayarlarını görüntülemek ve değiştirmek için
- Seçili **öğeleri Önizle** düğmesi, seçilen bir dosyayı veya bileşeni kod düzenleyicisinde görüntülemek için

### <a name="solution-explorer-right-click-context-menu"></a>Çözüm Gezgini sağ tıklama bağlam menüsü

Çözüm Gezgini ' de, sağ tıklama bağlam menüsünü kullanarak etkileşime girebilmeniz gereken birkaç dosya özelliği vardır. Sağ tıklama bağlam menüsü seçenekleri hakkında daha fazla bilgi için, [Proje ve çözüm özelliklerini yönetme](managing-project-and-solution-properties.md) sayfasına bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio çözüm ve projeler nelerdir?](solutions-and-projects-in-visual-studio.md)
- [Visual Studio 'de pencere düzenlerini özelleştirme](customizing-window-layouts-in-visual-studio.md)
