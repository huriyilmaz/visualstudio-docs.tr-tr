---
title: 'Nasıl Yapılır: Menüleri ve Araç Çubuklarını Özelleştirme'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
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
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 500debe6faa62079c6a93185bac409e7a3bf2813
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667999"
---
# <a name="how-to-customize-menus-and-toolbars-in-visual-studio"></a>Nasıl Yapılır: Visual Studio'da Menüleri ve Araç Çubuklarını Özelleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Araç çubuklarını ve menü çubuğundaki menüleri ekleyip kaldırmanın yanı sıra herhangi bir araç çubuğundaki veya menüdeki komutları ekleyip kaldırmak suretiyle de Visual Studio'yu özelleştirebilirsiniz.

> [!WARNING]
> Bir araç çubuğunu veya menüyü özelleştirdikten sonra, **Özelleştirme** iletişim kutusunda onay kutusunun seçili olmaya devam ettiğinden emin olun. Aksi takdirde, Visual Studio'yu kapatıp yeniden açtıktan sonra değişiklikleriniz kalıcı olmaz.

 **Bu konuda:**

- [Menü çubuğuna menü ekleme, kaldırma veya taşıma](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md#bkmk_addmenu)

- [Araç çubuğunu ekleme, kaldırma veya taşıma](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md#bkmk_addtoolbar)

- [Menüyü veya araç çubuğunu özelleştirme](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md#bkmk_customize)

- [Menüyü veya araç çubuğunu sıfırlama](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md#bkmk_reset)

## <a name="adding-removing-or-moving-a-menu-on-the-menu-bar"></a><a name="bkmk_addmenu"></a> Menü çubuğuna menü ekleme, kaldırma veya taşıma

1. Menü çubuğunda **Araçlar**, **Özelleştir**' i seçin.

     **Özelleştir** iletişim kutusu açılır.

2. **Komutlar** sekmesinde **menü çubuğu** seçenek düğmesini seçili bırakın, bu seçeneğin yanındaki listede bulunan **menü çubuğunu** seçili bırakın ve ardından aşağıdaki adım kümelerinden birini gerçekleştirin:

    - Bir menü eklemek için **yeni menü ekle** düğmesini seçin, **Seçimi Değiştir** düğmesini seçin ve sonra eklemek istediğiniz menüyü adlandırın.

         ![Menünün nasıl ekleneceğini gösteren iletişim kutusunu özelleştirme](../ide/media/addmenu.png "Eyleminin")

    - Menüyü kaldırmak için, **denetimler** listesinden seçin ve ardından **Sil** düğmesini seçin.

    - Menü çubuğundaki menüyü taşımak için, **denetimler** listesinden menüyü seçin ve ardından **Yukarı taşı** veya **aşağı taşı** düğmesini seçin.

## <a name="adding-removing-or-moving-a-toolbar"></a><a name="bkmk_addtoolbar"></a> Araç çubuğunu ekleme, kaldırma veya taşıma

1. Menü çubuğunda **Araçlar**, **Özelleştir**' i seçin.

     **Özelleştir** iletişim kutusu açılır.

2. **Araç çubuğu** sekmesinde, aşağıdaki adım kümelerinden birini gerçekleştirin:

    - Bir araç çubuğu eklemek için **Yeni** düğmesini seçin, eklemek istediğiniz araç çubuğu için bir ad belirtin ve sonra **Tamam** düğmesini seçin.

         ![Araç çubuğunun nasıl ekleneceğini gösteren iletişim kutusunu özelleştirme](../ide/media/addtoolbar.png "AddToolbar")

    - Özel bir araç çubuğunu kaldırmak için **araç çubukları** listesinden seçin ve ardından **Sil** düğmesini seçin.

        > [!IMPORTANT]
        > Kendi oluşturduğunuz araç çubuklarını silebilir, ancak varsayılan araç çubuklarını silemezsiniz.

    - Bir araç çubuğunu farklı bir yerleştirme konumuna taşımak için, **araç çubukları** listesinden seçin, **Seçimi Değiştir** düğmesini seçin ve açılan listeden bir konum seçin.

         Ayrıca, bir araç çubuğunu, ana yerleştirme alanında herhangi bir konuma taşımak için sol kenarından sürükleyebilirsiniz.

        > [!NOTE]
        > Araç çubuklarının kullanılabilirliğini ve erişilebilirliğini geliştirme hakkında daha fazla bilgi için bkz. [nasıl yapılır: IDE erişilebilirlik seçeneklerini ayarlama](../ide/reference/how-to-set-ide-accessibility-options.md).

## <a name="customizing-a-menu-or-a-toolbar"></a><a name="bkmk_customize"></a> Menüyü veya araç çubuğunu özelleştirme

1. Menü çubuğunda **Araçlar**, **Özelleştir**' i seçin.

     **Özelleştir** iletişim kutusu açılır.

2. **Komutlar** sekmesinde, özelleştirmek istediğiniz öğe türüne ilişkin seçenek düğmesini seçin.

3. Bu öğe türüne ilişkin listede, özelleştirmek istediğiniz menü veya araç çubuğunu seçin ve sonra aşağıdaki adım gruplarından birini gerçekleştirin:

    - Bir komut eklemek için **Komut Ekle** düğmesini seçin.

         **Komut Ekle** Iletişim kutusunda **Kategoriler** listesinden bir öğe seçin, **Komutlar** listesinden bir öğe seçin ve **Tamam** düğmesini seçin.

         ![Visual Studio 'da komut Ekle iletişim kutusu](../ide/media/addcommand.png "AddCommand 'i")

    - Bir komutu silmek için, **denetimler** listesinden seçin ve ardından **Sil** düğmesini seçin.

    - Komutları yeniden sıralamak için, **denetimler** listesinde bir komut seçin ve ardından **Yukarı taşı** veya **aşağı taşı** düğmesini seçin.

    - Komutları gruplara ayırmak için, **denetimler** listesinde bir komut seçin, **Seçimi Değiştir** düğmesini seçin ve açılan menüden **bir Grup Başlat** ' ı seçin.

## <a name="resetting-a-menu-or-a-toolbar"></a><a name="bkmk_reset"></a> Menüyü veya araç çubuğunu sıfırlama

1. Menü çubuğunda **Araçlar**, **Özelleştir**' i seçin.

     **Özelleştir** iletişim kutusu açılır.

2. **Komutlar** sekmesinde, sıfırlamak istediğiniz öğe türüne ilişkin seçenek düğmesini seçin.

3. Bu öğe türüne ilişkin listede, sıfırlamak istediğiniz menü veya araç çubuğunu seçin.

4. **Seçimi Değiştir** düğmesini seçin ve açılan menüden **Sıfırla** ' yı seçin.

     Tümünü **Sıfırla** düğmesini seçerek de tüm menüleri ve araç çubuklarını sıfırlayabilirsiniz.
