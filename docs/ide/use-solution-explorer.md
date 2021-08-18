---
title: Çözüm Gezgini aracı penceresi hakkında bilgi
description: Dosyalarınızı, projelerinizi ve Çözüm Gezgini yönetmek üzere Visual Studio için & araç penceresini nasıl kullanabileceğinizi öğrenin.
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
ms.openlocfilehash: fe16aa384584c567e992a4d893a0bfbfac44b686
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122055893"
---
# <a name="how-to-use-solution-explorer"></a>Çözüm Gezgini

Çözüm Gezgini araç penceresini kullanarak çözümlerinizi & projelerinizi yönetmek ve kodunuzla etkileşim & görüntülemek için kullanabilirsiniz. Bu makalede, bunu yapmanıza yardımcı olacak kullanıcı arabirimi (UI) seçeneklerini ayrıntılı olarak ele aacağız.

> [!NOTE]
> Bu konu yalnızca Visual Studio için Windows.

## <a name="solution-explorer-tool-window"></a>Çözüm Gezgini aracı penceresi

Başlamak için [IDE'de](../get-started/visual-studio-ide.md)Çözüm Gezgini araç penceresine göz atarak Visual Studio projeli açık bir C# konsol çözümüne göz atacağız.

[![Çözüm Gezgini araç penceresi Visual Studio.](media/solution-explorer-tool-window.png)](media/solution-explorer-tool-window.png#lightbox)

Araç penceresi aşağıdaki kullanıcı arabirimi (kullanıcı arabirimi) öğelerini içerir:

- **Menü çubuğunda,** dosyalarınızın nasıl görüntü görüntüleyebilirsiniz?
- **Belirli dosyaları** ve dosya türlerini arayabilirsiniz arama çubuğu .
- **Dosyalarınızı,** projelerinizi, projelerinizi ve çözümlerinizi görüntüp yönetebilirsiniz & penceresi
- **Çözüm düğümünü**, burada çözümlerinizi yönetesiniz
- **Project**, burada projelerinizi yönetesiniz
- **Çözüm ve proje** bağımlılıkları için çözüm & bağımlılıklar düğümü
- **Program düğümünü**, burada program veya uygulamanızı (uygulama) görüntüleyemez, düzenleyebilir ve yönetebilirsiniz
- **[Git değişiklikleri sekmesi:](../version-control/git-with-visual-studio.md?view=vs-2019&preserve-view=true#git-changes-window)** Takımla projeler üzerinde işbirliği & GitHub için Visual Studio Git'i kullanabilirsiniz

> [!TIP]
> Çözüm Gezgini araç penceresini görmüyorsanız, Görünüm Visual Studio 'ı kullanarak veya   >   **Ctrl** Alt L tuşlarına basarak Çözüm Gezgini menü çubuğundan +  + **açabilirsiniz.**

## <a name="solution-explorer-menu-bar"></a>Çözüm Gezgini menü çubuğu

Devam etmek için, menü çubuğundaki Çözüm Gezgini bakalım.

![Çözüm Gezgini menü çubuğundaki Visual Studio.](media/solution-explorer-menu-bar.png)

Menü çubuğu, soldan sağa aşağıdaki kullanıcı arabirimi öğelerini içerir:

- **Arama** sonuçları arasında geçiş yapmak için geri düğmesi
- **İleri** düğmesi, arama sonuçları arasında geçiş yapmak için
- **Varsayılan** görünüme dönmek için Giriş düğmesi
- **Çözümler** ve kullanılabilir görünümler arasında geçiş yapmak için düğmeyi değiştirme
- **Bekleyen Değişiklikler Filtresi** düğmesi & açık dosyaları veya dosyaları görüntülemek için açılan menüyü açar
- **Kod düzenleyicisinden bir** dosyayı bulmak için Etkin Belge ile eşitleme düğmesi
- **Yenile** düğmesi; yalnızca işlev veya paket gibi bir bağımlılığı seçmenizde görüntülenir
- **Ana pencerede** dosya görünümünü daraltan Tüm Daralt düğmesi
- **Kaldırılan projeler** de dahil olmak üzere tüm dosyaları görüntülemek için [Tüm Dosyaları Göster düğmesi](filtered-solutions.md#toggle-unloaded-project-visibility)
- **Belirli** dosya ve bileşenlerin ayarlarını görüntülemek ve değiştirmek için Özellikler düğmesi
- **Kod düzenleyicisinde** seçili bir dosyayı veya bileşeni görüntülemek için Seçili Öğelerin Önizlemesini Görüntüle düğmesi

### <a name="solution-explorer-right-click-context-menu"></a>Çözüm Gezgini sağ tıklama bağlam menüsü

Bu Çözüm Gezgini, sağ tıklama bağlam menüsünü kullanarak etkileşim kurabilirsiniz çeşitli dosya özellikleri vardır. Sağ tıklama bağlam menüsü seçenekleri hakkında daha fazla bilgi için Proje ve [çözüm özelliklerini yönetme sayfasına](managing-project-and-solution-properties.md) bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Bu hizmette çözümler ve Visual Studio?](solutions-and-projects-in-visual-studio.md)
- [Visual Studio'de pencere düzenlerini özelleştirme](customizing-window-layouts-in-visual-studio.md)
