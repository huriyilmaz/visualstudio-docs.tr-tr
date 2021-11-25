---
title: Menüleri ve araç çubuklarını özelleştirme
description: Menüleri ve araç Visual Studio nasıl özelleştirebileceğinizi ve ayrıca menülere ve araç çubuklarına dahil edilen komutları özelleştirmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/24/2021
ms.topic: how-to
f1_keywords:
- vs.renametoolbar
- vs.customize.toolbars
- vs.buttoneditor
- vs.customize.commands
- vs.newtoolbar
helpviewer_keywords:
- captions, customizing toolbar
- custom toolbars [Visual Studio]
- command buttons, customizing toolbar
- labels, customizing toolbar
- images [Visual Studio], toolbar buttons
- buttons [Visual Studio], custom toolbars
- toolbars [Visual Studio], creating in the IDE
- icons [Visual Studio], customizing toolbar
- commands [Visual Studio], customizing environment
- customizing toolbars
- toolbars [Visual Studio], customizing
- toolbars [Visual Studio], customizing in the IDE
ms.assetid: b570ae2f-5302-45dc-9cc9-8d4d1ad50603
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 6a93698d1bbc2f7240ff43f3e81a8fcb074b96af
ms.sourcegitcommit: 5af130d3ff64b71d415819e42f4f2efb2ae36a6a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2021
ms.locfileid: "133117477"
---
# <a name="how-to-customize-menus-and-toolbars-in-visual-studio"></a>Nasıl yapabilirsiniz: Menüleri ve araç çubuklarını Visual Studio

Menü çubuğunda Visual Studio menüleri ve menüleri ekleyerek ve kaldırarak değil, aynı zamanda herhangi bir araç çubuğuna veya menüye komut ekleyerek ve kaldırarak da bu öğeleri özelleştirebilirsiniz.

> [!TIP]
> Araç çubuğunu size uygun hale getirebileceğiniz şekilde kişiselleştirme hakkında daha fazla bilgi edinmek için iş akışınız için araç çubuklarını iyileştirme blog [**gönderimize bakın.**](https://devblogs.microsoft.com/visualstudio/optimizing-toolbars-for-your-workflow/)

## <a name="add-remove-or-move-a-menu-on-the-menu-bar"></a>Menü çubuğunda menü ekleme, kaldırma veya taşıma

1. Menü çubuğunda Araçlar   >  **Özelleştir'i seçin.**

     Özelleştir **iletişim** kutusu açılır.

2. Komutlar **sekmesinde** Menü  çubuğu seçeneği düğmesini seçili  bırakın, menü çubuğunu bu seçeneğin yanındaki listede seçili bırakın ve ardından aşağıdaki adım kümelerinden birini gerçekleştirin:

    - Menü eklemek için Yeni Menü **Ekle** düğmesini seçin, Seçimi Değiştir **düğmesini** seçin ve ardından eklemek istediğiniz menüye bir ad girin.

        ::: moniker range="vs-2017"
        ![Menü eklemeyi gösteren Özelleştir iletişim kutusu](../ide/media/addmenu.png)
        ::: moniker-end

    - Menüyü kaldırmak için Denetimler **listesinden** seçin ve sil **düğmesini** seçin.

    - Menü çubuğundaki bir menüyü taşımak için  Denetimler listesinden menüyü seçin ve ardından Yukarı Taşı **veya** Aşağı Taşı **düğmesini** seçin.

## <a name="add-remove-or-move-a-toolbar"></a>Araç çubuğu ekleme, kaldırma veya taşıma

1. Menü çubuğunda Araçlar   >  **Özelleştir'i seçin.**

     Özelleştir **iletişim** kutusu açılır.

2. Araç **Çubuğu** sekmesinde aşağıdaki adım kümelerinden birini gerçekleştirin:

    - Araç çubuğu eklemek için Yeni **düğmesini** seçin, eklemek istediğiniz araç çubuğu için bir ad belirtin ve ardından Tamam **düğmesini** seçin.

        ::: moniker range="vs-2017"
        ![Araç çubuğu eklemeyi gösteren Özelleştirme iletişim kutusu](../ide/media/addtoolbar.png)
        ::: moniker-end

    - Özel bir araç çubuğunu kaldırmak için Araç Çubukları **listesinden bunu** seçin ve sil **düğmesini** seçin.

        > [!IMPORTANT]
        > Kendi oluşturduğunuz araç çubuklarını silebilir, ancak varsayılan araç çubuklarını silemezsiniz.

    - Bir araç çubuğunu farklı bir yerleştirme konuma taşımak  için Araç Çubukları  listesinden seçin, Seçimi Değiştir düğmesini seçin ve ardından görüntülenen listeden bir konum seçin.

        Ayrıca, bir araç çubuğunu, ana yerleştirme alanında herhangi bir konuma taşımak için sol kenarından sürükleyebilirsiniz.

        > [!NOTE]
        > Araç çubuklarının kullanılabilirliğini ve erişilebilirliğini geliştirme hakkında daha fazla bilgi için [bkz. Nasıl ayarlanır: IDE erişilebilirlik seçeneklerini ayarlama.](../ide/reference/how-to-set-ide-accessibility-options.md)

## <a name=""></a><a name="customizing_menu">Menü veya araç çubuğunu özelleştirme</a>

> [!WARNING]
> Bir araç çubuğunu veya menüyü özelleştirdikten sonra Özelleştir iletişim kutusunda onay kutusunun seçili **olduğundan** emin olun. Aksi takdirde, Visual Studio'yu kapatıp yeniden açtıktan sonra değişiklikleriniz kalıcı olmaz.

1. Menü çubuğunda Araçlar   >  **Özelleştir'i seçin.**

    Özelleştir **iletişim** kutusu açılır.

2. Komutlar  sekmesinde, özelleştirmek istediğiniz öğe türü için seçenek düğmesini seçin.

3. Bu öğe türüne ilişkin listede, özelleştirmek istediğiniz menü veya araç çubuğunu seçin ve sonra aşağıdaki adım gruplarından birini gerçekleştirin:

    - Komut eklemek için Komut Ekle **düğmesini** seçin.

        Komut **Ekle iletişim** kutusunda, Kategoriler listesinden bir öğe **seçin,** Komutlar listesinden bir **öğe seçin** ve ardından Tamam **düğmesini** seçin.

        ::: moniker range="vs-2017"
        ![Komut Ekle iletişim kutusu Visual Studio](../ide/media/addcommand.png)
        ::: moniker-end

    - Bir komutu silmek için Denetimler **listesinden** seçin ve sil **düğmesini** seçin.

    - Komutları yeniden sıralamak için Denetimler **listesinden** bir komut seçin ve ardından Yukarı Taşı **veya Aşağı** **Taşı düğmesini** seçin.

    - Yatay bir çizginin altında komutları gruplayabilirsiniz.  Denetimler listesinden ilk komutu seçin, Seçimi Değiştir düğmesini seçin ve sonra görüntülenen menüden Grup Başlat'ı seçin.  

## <a name="reset-a-menu-or-a-toolbar"></a>Menü veya araç çubuğunu sıfırlama

1. Menü çubuğunda Araçlar   >  **Özelleştir'i seçin.**

    Özelleştir **iletişim** kutusu açılır.

2. Komutlar  sekmesinde, sıfırlamak istediğiniz öğe türü için seçenek düğmesini seçin.

3. Bu öğe türüne ilişkin listede, sıfırlamak istediğiniz menü veya araç çubuğunu seçin.

4. Seçimi **Değiştir düğmesini** ve ardından görüntülenen **menüden** Sıfırla'yı seçin.

    Ayrıca, Tüm menüleri ve araç çubuklarını Sıfırla düğmesini **seçerek de sıfırlayabilirsiniz.**

## <a name="see-also"></a>Ayrıca bkz.

- [IDE’yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md)
- [Düzenleyiciyi özelleştirme](../ide/how-to-change-text-case-in-the-editor.md)
