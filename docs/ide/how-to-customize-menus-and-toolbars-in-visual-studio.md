---
title: Menüleri ve araç çubuklarını özelleştirme
description: Visual Studio menülerini ve araç çubuklarını özelleştirmeyi ve ayrıca menülere ve araç çubuklarına dahil olan tüm komutları özelleştirmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 09/01/2021
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
ms.openlocfilehash: 8223dfb14ab626e6509cf0df32cba05526fc707f
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725769"
---
# <a name="how-to-customize-menus-and-toolbars-in-visual-studio"></a>Nasıl yapılır: Visual Studio menüleri ve araç çubuklarını özelleştirme

yalnızca menü çubuğuna araç çubukları ve menüler ekleyip kaldırarak değil, aynı zamanda belirli bir araç çubuğu veya menüdeki komutları ekleyerek ve kaldırarak Visual Studio özelleştirebilirsiniz.

> [!TIP]
> Araç çubuğunun nasıl kişiselleştirilmesi hakkında daha fazla bilgi edinmek için, en son blog gönderimize bakın, [**iş akışınız için araç çubuklarını En Iyi duruma**](https://devblogs.microsoft.com/visualstudio/optimizing-toolbars-for-your-workflow/)getirin.

## <a name="add-remove-or-move-a-menu-on-the-menu-bar"></a>Menü çubuğuna menü ekleme, kaldırma veya taşıma

1. Menü çubuğunda **Araçlar**  >  **Özelleştir**' i seçin.

     **Özelleştir** iletişim kutusu açılır.

2. **Komutlar** sekmesinde **menü çubuğu** seçenek düğmesini seçili bırakın, bu seçeneğin yanındaki listede bulunan **menü çubuğunu** seçili bırakın ve ardından aşağıdaki adım kümelerinden birini gerçekleştirin:

    - Bir menü eklemek için **yeni menü ekle** düğmesini seçin, **Seçimi Değiştir** düğmesini seçin ve sonra eklemek istediğiniz menüyü adlandırın.

        ![Menünün nasıl ekleneceğini gösteren iletişim kutusunu özelleştirme](../ide/media/addmenu.png)

    - Menüyü kaldırmak için, **denetimler** listesinden seçin ve ardından **Sil** düğmesini seçin.

    - Menü çubuğundaki menüyü taşımak için, **denetimler** listesinden menüyü seçin ve ardından **Yukarı taşı** veya **aşağı taşı** düğmesini seçin.

## <a name="add-remove-or-move-a-toolbar"></a>Araç çubuğunu ekleme, kaldırma veya taşıma

1. Menü çubuğunda **Araçlar**  >  **Özelleştir**' i seçin.

     **Özelleştir** iletişim kutusu açılır.

2. **Araç çubuğu** sekmesinde, aşağıdaki adım kümelerinden birini gerçekleştirin:

    - Bir araç çubuğu eklemek için **Yeni** düğmesini seçin, eklemek istediğiniz araç çubuğu için bir ad belirtin ve sonra **Tamam** düğmesini seçin.

        ![Araç çubuğunun nasıl ekleneceğini gösteren iletişim kutusunu özelleştirme](../ide/media/addtoolbar.png)

    - Özel bir araç çubuğunu kaldırmak için **araç çubukları** listesinden seçin ve ardından **Sil** düğmesini seçin.

        > [!IMPORTANT]
        > Kendi oluşturduğunuz araç çubuklarını silebilir, ancak varsayılan araç çubuklarını silemezsiniz.

    - Bir araç çubuğunu farklı bir yerleştirme konumuna taşımak için, **araç çubukları** listesinden seçin, **Seçimi Değiştir** düğmesini seçin ve açılan listeden bir konum seçin.

        Ayrıca, bir araç çubuğunu, ana yerleştirme alanında herhangi bir konuma taşımak için sol kenarından sürükleyebilirsiniz.

        > [!NOTE]
        > Araç çubuklarının kullanılabilirliğini ve erişilebilirliğini geliştirme hakkında daha fazla bilgi için bkz. [nasıl yapılır: IDE erişilebilirlik seçeneklerini ayarlama](../ide/reference/how-to-set-ide-accessibility-options.md).

## <a name=""></a><a name="customizing_menu">Menüyü veya araç çubuğunu özelleştirme</a>

> [!WARNING]
> Bir araç çubuğunu veya menüyü özelleştirdikten sonra, **Özelleştirme** iletişim kutusunda onay kutusunun seçili olmaya devam ettiğinden emin olun. Aksi takdirde, Visual Studio'yu kapatıp yeniden açtıktan sonra değişiklikleriniz kalıcı olmaz.

1. Menü çubuğunda **Araçlar**  >  **Özelleştir**' i seçin.

    **Özelleştir** iletişim kutusu açılır.

2. **Komutlar** sekmesinde, özelleştirmek istediğiniz öğe türüne ilişkin seçenek düğmesini seçin.

3. Bu öğe türüne ilişkin listede, özelleştirmek istediğiniz menü veya araç çubuğunu seçin ve sonra aşağıdaki adım gruplarından birini gerçekleştirin:

    - Bir komut eklemek için **Komut Ekle** düğmesini seçin.

        **Komut Ekle** Iletişim kutusunda **Kategoriler** listesinden bir öğe seçin, **Komutlar** listesinden bir öğe seçin ve **Tamam** düğmesini seçin.

        ![Visual Studio komut iletişim kutusu Ekle](../ide/media/addcommand.png)

    - Bir komutu silmek için, **denetimler** listesinden seçin ve ardından **Sil** düğmesini seçin.

    - Komutları yeniden sıralamak için, **denetimler** listesinde bir komut seçin ve ardından **Yukarı taşı** veya **aşağı taşı** düğmesini seçin.

    - Komutları yatay bir çizgi altında gruplandırmak için, **denetimler** listesinden ilk komutu seçin, **Seçimi Değiştir** düğmesini seçin ve açılan menüden **bir Grup Başlat** ' ı seçin.

## <a name="reset-a-menu-or-a-toolbar"></a>Menüyü veya araç çubuğunu sıfırlama

1. Menü çubuğunda **Araçlar**  >  **Özelleştir**' i seçin.

    **Özelleştir** iletişim kutusu açılır.

2. **Komutlar** sekmesinde, sıfırlamak istediğiniz öğe türüne ilişkin seçenek düğmesini seçin.

3. Bu öğe türüne ilişkin listede, sıfırlamak istediğiniz menü veya araç çubuğunu seçin.

4. **Seçimi Değiştir** düğmesini seçin ve açılan menüden **Sıfırla** ' yı seçin.

    Tümünü **Sıfırla** düğmesini seçerek de tüm menüleri ve araç çubuklarını sıfırlayabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [IDE’yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md)
- [Düzenleyiciyi özelleştirme](../ide/how-to-change-text-case-in-the-editor.md)
