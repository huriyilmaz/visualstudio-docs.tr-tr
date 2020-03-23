---
title: Menüleri ve araç çubuklarını özelleştirme
ms.date: 11/04/2016
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ed425b120d5d47fb684294ce17bd7d48374c638e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79301855"
---
# <a name="how-to-customize-menus-and-toolbars-in-visual-studio"></a>Nasıl yapIlir: Visual Studio'da menüleri ve araç çubuklarını özelleştirin

Visual Studio'yu yalnızca menü çubuğuna araç çubukları ve menüler ekleyerek ve kaldırarak değil, aynı zamanda belirli bir araç çubuğuna veya menüye komutlar ekleyerek ve kaldırarak da özelleştirebilirsiniz.

> [!WARNING]
> Bir araç çubuğunu veya menüye özelleştirdikten sonra, onay kutusunun **Özelleştir** iletişim kutusunda seçili kaldığından emin olun. Aksi takdirde, Visual Studio'yu kapatıp yeniden açtıktan sonra değişiklikleriniz kalıcı olmaz.

## <a name="add-remove-or-move-a-menu-on-the-menu-bar"></a>Menü çubuğuna menü ekleme, kaldırma veya taşıma

1. Menü çubuğunda, **Araçları** > **Özelleştir'i**seçin.

     **Özelleştir** iletişim kutusu açılır.

2. **Komutlar** sekmesinde, **Menü çubuğu** seçeneği düğmesini seçili bırakın, menü **çubuğunu** bu seçeneğin yanındaki listede seçili bırakın ve ardından aşağıdaki adım kümelerinden birini gerçekleştirin:

    - Menü eklemek için **Yeni Menü Ekle** düğmesini seçin, Seçimi **Değiştir** düğmesini seçin ve eklemek istediğiniz menüye adını verin.

        ![Menü ekleme yi gösteren iletişim kutusunu özelleştirme](../ide/media/addmenu.png)

    - Bir menüyü kaldırmak **için, Denetimler** listesinde ni seçip sil **düğmesini** seçin.

    - Menü çubuğundaki menüyü taşımak için **Denetimler** listesindeki menüyü seçin ve ardından **Yukarı Veya** Aşağı **Taşı** düğmesini seçin.

## <a name="add-remove-or-move-a-toolbar"></a>Araç çubuğu ekleme, kaldırma veya taşıma

1. Menü çubuğunda, **Araçları** > **Özelleştir'i**seçin.

     **Özelleştir** iletişim kutusu açılır.

2. Araç **Çubuğu** sekmesinde aşağıdaki adım kümelerinden birini gerçekleştirin:

    - Araç çubuğu eklemek için **Yeni** düğmesini seçin, eklemek istediğiniz araç çubuğu için bir ad belirtin ve ardından **Tamam** düğmesini seçin.

        ![Araç çubuğu ekleme yi gösteren iletişim kutusunu özelleştirme](../ide/media/addtoolbar.png)

    - Özel bir araç çubuğunu kaldırmak için **Araç Çubukları** listesinde seçin ve sonra **Sil** düğmesini seçin.

        > [!IMPORTANT]
        > Kendi oluşturduğunuz araç çubuklarını silebilir, ancak varsayılan araç çubuklarını silemezsiniz.

    - Bir araç çubuğunu farklı bir yerleştirme konumuna taşımak için, **Araç Çubukları** listesinde seçin, **Seçimi Değiştir** düğmesini seçin ve ardından listede görünen bir konum seçin.

        Ayrıca, bir araç çubuğunu, ana yerleştirme alanında herhangi bir konuma taşımak için sol kenarından sürükleyebilirsiniz.

        > [!NOTE]
        > Araç çubuklarının kullanılabilirliği ve erişilebilirliği hakkında daha fazla bilgi için [bkz.](../ide/reference/how-to-set-ide-accessibility-options.md)

## <a name=""></a><a name="customizing_menu">Menüyü veya araç çubuğunü özelleştirme</a>

1. Menü çubuğunda, **Araçları** > **Özelleştir'i**seçin.

    **Özelleştir** iletişim kutusu açılır.

2. **Komutlar** sekmesinde, özelleştirmek istediğiniz öğe türü için seçenek düğmesini seçin.

3. Bu öğe türüne ilişkin listede, özelleştirmek istediğiniz menü veya araç çubuğunu seçin ve sonra aşağıdaki adım gruplarından birini gerçekleştirin:

    - Komut eklemek için **Komut Ekle** düğmesini seçin.

        Komut **Ekle** iletişim kutusunda, **Kategoriler** listesinde bir öğe seçin, **Komutlar** listesinde bir öğe seçin ve sonra **Tamam** düğmesini seçin.

        ![Visual Studio'da Komut iletişim kutusu ekle](../ide/media/addcommand.png)

    - Bir komutu silmek **için, Denetimler** listesinde seçin ve sonra **Sil** düğmesini seçin.

    - Komutları yeniden sıralamak için **Denetimler** listesinde bir komut seçin ve ardından **Yukarı Taşıy** veya Aşağı **Taşı** düğmesini seçin.

    - Komutları yatay bir çizginin altında gruplandırmak **için, Denetimler** listesindeki ilk komutu seçin, **Seçimi Değiştir** düğmesini seçin ve ardından görünen menüde Grup **Başlat'ı** seçin.

## <a name="reset-a-menu-or-a-toolbar"></a>Menüyü veya araç çubuğunü sıfırlama

1. Menü çubuğunda, **Araçları** > **Özelleştir'i**seçin.

    **Özelleştir** iletişim kutusu açılır.

2. **Komutlar** sekmesinde, sıfırlamak istediğiniz öğe türü için seçenek düğmesini seçin.

3. Bu öğe türüne ilişkin listede, sıfırlamak istediğiniz menü veya araç çubuğunu seçin.

4. Seçimi **Değiştir** düğmesini seçin ve ardından görünen menüde **Sıfırla'yı** seçin.

    Ayrıca Tüm menüleri ve araç çubuklarını **Tümlerini Sıfırla** düğmesini seçerek sıfırlayabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [IDE'yi kişiselleştirin](../ide/personalizing-the-visual-studio-ide.md)
- [Düzenleyiciyi özelleştirme](../ide/how-to-change-text-case-in-the-editor.md)
