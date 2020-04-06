---
title: Menüleri ve Komutları Genişletme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, common tasks
- VSPackages, menu tasks
- .vsct files, common menu tasks
ms.assetid: 7b2be4b9-e3fe-4412-874f-ae72ebc84c4b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dfcedd3f1b4cb48631541f1726556dab766402ab
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711807"
---
# <a name="extend-menus-and-commands"></a>Menüleri ve komutları genişletme
Komutlar, Visual Studio'ya eylem ve işlem ekleme şeklinizdir. Çoğu durumda komutlar menülerde veya araç çubuklarında görüntülenir. VSPackage proje şablonu çok temel bir komutun nasıl uygulanacağını gösterir. Biraz daha uzun ama yine de temel bir uygulama için, [bkz.](../extensibility/creating-an-extension-with-a-menu-command.md)

 Visual Studio komutları, menüler ve araç çubukları hakkında daha fazla bilgi için [Komutlar, menüler ve araç çubuklarına](../extensibility/internals/commands-menus-and-toolbars.md)bakın.

 Komutlar, menüler ve araç çubukları VSPackage projelerinin bir parçası olan *.vsct* dosyasında tanımlanır. Visual Studio IDE ve *.vsct* dosyası hakkında bilgileri [VSPackages'ın kullanıcı arabirimi öğelerini nasıl ekleyeceğini zedelebilirsiniz.](../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 Aşağıdaki konular, farklı komut türlerinin, menülerin ve araç çubuklarının nasıl ekleyeceğini açıklayınız.

## <a name="in-this-section"></a>Bu bölümde
- [Visual Studio menü çubuğuna menü ekleme](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) En üst teki Visual Studio menü çubuğuna menü nasıl ekleyeceğiniaçıklar.

- [Klavye kısayollarını menü öğelerine bağlama](../extensibility/binding-keyboard-shortcuts-to-menu-items.md) Menü öğesine klavye kısayolu (CTRL + 3 gibi) nasıl ekleyeceğiniaçıklar.

- [Menüye alt menü ekleme](../extensibility/adding-a-submenu-to-a-menu.md) Üst menüye alt menünün nasıl ekleyeceğini açıklar.

- [Alt menüye en son kullanılan liste ekleme](../extensibility/adding-a-most-recently-used-list-to-a-submenu.md) En Son Kullanılanlar listesinin nasıl ekleyeceğini açıklar.

- [Yeniden kullanılabilir düğme grupları oluşturma](../extensibility/creating-reusable-groups-of-buttons.md) Komut öğelerinin birden çok menüye eklenebilecek şekilde nasıl gruplandırılabildiğini açıklar.

- [Menü komutlarına simge ekleme](../extensibility/adding-icons-to-menu-commands.md) Hem araç çubuğunda hem de menüde komuta simge nin nasıl ekleyeceğini açıklar.

- [Menü komutunun metnini değiştirme](../extensibility/changing-the-text-of-a-menu-command.md) Bir menü öğesinin `TextChanges` dinamik olarak değiştirilmesini sağlamak için bayrağın kullanımını açıklar.

- [Komutun görünümünü değiştirme](../extensibility/changing-the-appearance-of-a-command.md) Bir komutu dinamik olarak nasıl etkinleştirin veya devre dışı kılabilir açıklar.

- [Kullanıcı arabirimini güncelleştirme](../extensibility/updating-the-user-interface.md) Kullanıcı arabiriminin güncelleştirmesini son değişiklikleri yansıtacak şekilde nasıl zorlayacağını açıklar.

- [Menü komutlarını yerelleştir](../extensibility/localizing-menu-commands.md) Menü komutlarının nasıl yerelleştirilebildiğini açıklar.
