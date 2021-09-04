---
title: Çözüm Gezgini araç penceresi hakkında bilgi
description: Dosya, proje ve Çözüm Gezgini yönetmek üzere Visual Studio için & araç penceresini nasıl kullanabileceğinizi öğrenin.
ms.date: 09/02/2021
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
ms.openlocfilehash: 6fa982d290abcc852c93369003abeed0e6363291
ms.sourcegitcommit: f71a0db01bd4f24521cee5da926b9db3571ddecd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2021
ms.locfileid: "123459146"
---
# <a name="how-to-use-solution-explorer"></a>Çözüm Gezgini'i kullanma

Çözüm Gezgini araç penceresini kullanarak çözümlerinizi & projelerinizi yönetmek ve kodunuzla etkileşime & görüntülemek için kullanabilirsiniz. Bu makalede, bu konuda size yardımcı olacak kullanıcı arabirimi (UI) seçeneklerini ayrıntılı olarak açıklaacağız.

> [!NOTE]
> Bu konu yalnızca Visual Studio için Windows.

## <a name="solution-explorer-tool-window"></a>Çözüm Gezgini aracı penceresi

Başlamak için [IDE'de](../get-started/visual-studio-ide.md)Çözüm Gezgini araç penceresine göz atarak Visual Studio projeli açık bir C# konsol çözümüne göz atacağız.

[![Çözüm Gezgini araç penceresinin açıklamalı ekran Visual Studio.](media/solution-explorer-tool-window.png)](media/solution-explorer-tool-window.png#lightbox)

Araç penceresi aşağıdaki kullanıcı arabirimi (kullanıcı arabirimi) öğelerini içerir:

- **Menü çubuğunda,** dosyalarınızın nasıl görüntülen olduğunu kontrol etmek için
- **Belirli dosyaları** ve dosya türlerini arayabilirsiniz arama çubuğu .
- **Dosyalarınızı,** projelerinizi, projelerinizi ve çözümlerinizi görüntüp yönetebilirsiniz ana & penceresi
- **Çözüm düğümünü**, burada çözümlerinizi yönetesiniz
- **Project yönet8** düğümünü seçin
- **Çözüm ve proje** bağımlılıkları için çözüm & bağımlılıklar düğümü
- **Program düğümünü**, burada program veya uygulama (uygulama) görüntüleyemez, düzenleyebilir ve yönetebilirsiniz
- **[Git değişiklikleri sekmesi:](../version-control/git-with-visual-studio.md?view=vs-2019&preserve-view=true#git-changes-window)** Takımla projeler üzerinde işbirliği & GitHub için Visual Studio Git'i kullanabilirsiniz

> [!TIP]
> Çözüm Gezgini araç penceresini görmüyorsanız, Görünüm Visual Studio 'ı kullanarak veya Ctrl Alt L tuşlarına basarak Çözüm Gezgini menü  >  çubuğundan  +  + **açabilirsiniz.**

## <a name="solution-explorer-menu-bar"></a>Çözüm Gezgini menü çubuğu

Devam etmek için, menü çubuğundaki Çözüm Gezgini bakalım.

![Visual Studio'daki Çözüm Gezgini çubuğunun açıklamalı ekran Visual Studio.](media/solution-explorer-menu-bar.png)

Menü çubuğu, soldan sağa aşağıdaki kullanıcı arabirimi öğelerini içerir:

- **Arama** sonuçları arasında geçiş yapmak için geri düğmesi
- **İleri** düğmesi, arama sonuçları arasında geçiş yapmak için
- **Varsayılan** görünüme dönmek için Giriş düğmesi
- **Çözümler** ve kullanılabilir görünümler arasında geçiş yapmak için düğmeyi değiştirme
- **Bekleyen Değişiklikler Filtresi** düğmesi & bekleyen değişikliklere sahip açık dosyaları görüntülemek için açılan menüyü açar
- **Kod düzenleyicisinden bir** dosyayı bulmak için Etkin Belge ile eşitleme düğmesi
- **Yenile** düğmesi, yalnızca işlev veya paket gibi bir bağımlılığı seçmenizde görüntülenir
- **Ana pencerede** dosya görünümünü daraltan Tüm Daralt düğmesi
- **Kaldırılan projeler** de dahil olmak üzere tüm dosyaları görüntülemek için [Tüm Dosyaları Göster düğmesi](filtered-solutions.md#toggle-unloaded-project-visibility)
- **Belirli** dosya ve bileşenlerin ayarlarını görüntülemek ve değiştirmek için Özellikler düğmesi
- **Kod düzenleyicisinde** seçili bir dosyayı veya bileşeni görüntülemek için Seçili Öğelerin Önizlemesini Görüntüle düğmesi

## <a name="solution-explorer-context-menu"></a>Çözüm Gezgini menüsü

Bu Çözüm Gezgini bağlam menüsünü kullanarak etkileşim kurabilirsiniz. C# uygulamasının aşağıdaki ekran görüntüsünde, Çözüm düğümüne sağ tıklarsanız görünen bağlam menüsü **seçenekleri görüntülenir.**

:::image type="content" source="media/solution-explorer-context-menu.png" alt-text="Çözüm Gezgini'da sağ tıklama bağlam menüsünün ekran görüntüsü.":::

Çözüm düğümünden bağlam menüsünde ne **göreceğiniz proje** türüne, programlama diline veya platforma da bağlıdır. Aşağıdaki ekran görüntüsünde bir C# uygulaması için şu ek seçenekler vurgulanır: **Project** Bağımlılıklar , **Project** Derleme **Sırası,** Başlangıç Projelerini Ayarla ve **Git** açılır menüsü. Bu ek seçenekler genellikle bir çözüme başka bir proje ekler ve sonra bunu bir repoya eklerken görünür.

:::image type="content" source="media/solution-explorer-context-menu-extra-items.png" alt-text="Çözüm Gezgini seçeneklerle birlikte sağ tıklama bağlam menüsünün ekran görüntüsü.":::

## <a name="the-add-menu"></a>Ekle menüsü

Bu Çözüm Gezgini menüsünde en kullanışlı seçeneklerden biri, **Açılır** menü ekle'dir. Bu çözümden bir [çözüme başka bir](../get-started/csharp/tutorial-console-part-2.md#add-another-project) proje ekleyin. Ayrıca bir [projeye öğe ekleyebilir](reference/add-new-item-command.md) ve daha fazlasını da sebilirsiniz.

:::image type="content" source="media/solution-explorer-context-menu-add-flyout.png" alt-text="Çözüm Gezgini'da sağ tıklama bağlam menüsündeki Açılır menü ekle seçeneğinin ekran Çözüm Gezgini.":::

Ekle açılır **menüsünü** Çözüm düğümünden,  Project **düğümünden** veya **Bağımlılıklar düğümünden görüntüebilirsiniz.** Seçenekler, kullandığınız düğüme bağlı olarak değişir.

Çözüm Gezgini'de bağlam menüsünü kullanarak öğe ve proje ekleme hakkında size yol Çözüm Gezgini için Projelere ve [çözümlere giriş sayfasına](../get-started/tutorial-projects-solutions.md#add-an-item-to-the-project) bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Bu hizmette çözümler ve Visual Studio?](solutions-and-projects-in-visual-studio.md)
- [Visual Studio'de pencere düzenlerini özelleştirme](customizing-window-layouts-in-visual-studio.md)
