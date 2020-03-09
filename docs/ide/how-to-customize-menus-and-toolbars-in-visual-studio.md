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
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409737"
---
# <a name="how-to-customize-menus-and-toolbars-in-visual-studio"></a>Nasıl yapılır: menüleri ve Visual Studio araç çubuklarını özelleştirme

Visual Studio yalnızca ekleyerek ve araç çubuklarını ve menü çubuğundaki menüleri kaldırma, aynı zamanda ekleyerek ve herhangi bir araç veya menü komutları kaldırma özelleştirebilirsiniz.

> [!WARNING]
> Bir araç çubuğunu veya menüyü özelleştirdikten sonra, **Özelleştirme** iletişim kutusunda onay kutusunun seçili olmaya devam ettiğinden emin olun. Aksi takdirde, Visual Studio'yu kapatıp yeniden açtıktan sonra değişiklikleriniz kalıcı olmaz.

## <a name="add-remove-or-move-a-menu-on-the-menu-bar"></a>Eklemek, kaldırmak veya menü çubuğunda bir menü Taşı

1. Menü çubuğunda **araçlar** > **Özelleştir**' i seçin.

     **Özelleştir** iletişim kutusu açılır.

2. **Komutlar** sekmesinde **menü çubuğu** seçenek düğmesini seçili bırakın, bu seçeneğin yanındaki listede bulunan **menü çubuğunu** seçili bırakın ve ardından aşağıdaki adım kümelerinden birini gerçekleştirin:

    - Bir menü eklemek için **yeni menü ekle** düğmesini seçin, **Seçimi Değiştir** düğmesini seçin ve sonra eklemek istediğiniz menüyü adlandırın.

        ![Özelleştir iletişim kutusu gösteren bir menü ekleme](../ide/media/addmenu.png)

    - Menüyü kaldırmak için, **denetimler** listesinden seçin ve ardından **Sil** düğmesini seçin.

    - Menü çubuğundaki menüyü taşımak için, **denetimler** listesinden menüyü seçin ve ardından **Yukarı taşı** veya **aşağı taşı** düğmesini seçin.

## <a name="add-remove-or-move-a-toolbar"></a>Eklemek, kaldırmak veya araç çubuğunu taşımak

1. Menü çubuğunda **araçlar** > **Özelleştir**' i seçin.

     **Özelleştir** iletişim kutusu açılır.

2. **Araç çubuğu** sekmesinde, aşağıdaki adım kümelerinden birini gerçekleştirin:

    - Bir araç çubuğu eklemek için **Yeni** düğmesini seçin, eklemek istediğiniz araç çubuğu için bir ad belirtin ve sonra **Tamam** düğmesini seçin.

        ![Özelleştir iletişim kutusu araç çubuğu ekleme gösteriliyor](../ide/media/addtoolbar.png)

    - Özel bir araç çubuğunu kaldırmak için **araç çubukları** listesinden seçin ve ardından **Sil** düğmesini seçin.

        > [!IMPORTANT]
        > Kendi oluşturduğunuz araç çubuklarını silebilir, ancak varsayılan araç çubuklarını silemezsiniz.

    - Bir araç çubuğunu farklı bir yerleştirme konumuna taşımak için, **araç çubukları** listesinden seçin, **Seçimi Değiştir** düğmesini seçin ve açılan listeden bir konum seçin.

        Ayrıca, bir araç çubuğunu, ana yerleştirme alanında herhangi bir konuma taşımak için sol kenarından sürükleyebilirsiniz.

        > [!NOTE]
        > Araç çubuklarının kullanılabilirliğini ve erişilebilirliğini geliştirme hakkında daha fazla bilgi için bkz. [nasıl yapılır: IDE erişilebilirlik seçeneklerini ayarlama](../ide/reference/how-to-set-ide-accessibility-options.md).

## <a name="customizing_menu">Menüyü veya araç çubuğunu özelleştirme</a>

1. Menü çubuğunda **araçlar** > **Özelleştir**' i seçin.

    **Özelleştir** iletişim kutusu açılır.

2. **Komutlar** sekmesinde, özelleştirmek istediğiniz öğe türüne ilişkin seçenek düğmesini seçin.

3. Bu öğe türüne ilişkin listede, özelleştirmek istediğiniz menü veya araç çubuğunu seçin ve sonra aşağıdaki adım gruplarından birini gerçekleştirin:

    - Bir komut eklemek için **Komut Ekle** düğmesini seçin.

        **Komut Ekle** Iletişim kutusunda **Kategoriler** listesinden bir öğe seçin, **Komutlar** listesinden bir öğe seçin ve **Tamam** düğmesini seçin.

        ![Visual Studio'da Ekle komutu iletişim kutusu](../ide/media/addcommand.png)

    - Bir komutu silmek için, **denetimler** listesinden seçin ve ardından **Sil** düğmesini seçin.

    - Komutları yeniden sıralamak için, **denetimler** listesinde bir komut seçin ve ardından **Yukarı taşı** veya **aşağı taşı** düğmesini seçin.

    - Komutları yatay bir çizgi altında gruplandırmak için, **denetimler** listesinden ilk komutu seçin, **Seçimi Değiştir** düğmesini seçin ve açılan menüden **bir Grup Başlat** ' ı seçin.

## <a name="reset-a-menu-or-a-toolbar"></a>Bir menü veya araç çubuğunu sıfırlama

1. Menü çubuğunda **araçlar** > **Özelleştir**' i seçin.

    **Özelleştir** iletişim kutusu açılır.

2. **Komutlar** sekmesinde, sıfırlamak istediğiniz öğe türüne ilişkin seçenek düğmesini seçin.

3. Bu öğe türüne ilişkin listede, sıfırlamak istediğiniz menü veya araç çubuğunu seçin.

4. **Seçimi Değiştir** düğmesini seçin ve açılan menüden **Sıfırla** ' yı seçin.

    Tümünü **Sıfırla** düğmesini seçerek de tüm menüleri ve araç çubuklarını sıfırlayabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [IDE 'yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md)
- [Düzenleyiciyi özelleştirme](../ide/how-to-change-text-case-in-the-editor.md)
