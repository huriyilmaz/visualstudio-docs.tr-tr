---
title: Menüleri ve Komutları Genişletme | Microsoft Docs
description: Komutlar hakkında bilgi edinmek ve bu komutlara eylem ve Visual Studio. VSPackage proje şablonu, çok temel bir komutun nasıl uygulandığını gösterir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, common tasks
- VSPackages, menu tasks
- .vsct files, common menu tasks
ms.assetid: 7b2be4b9-e3fe-4412-874f-ae72ebc84c4b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: a9b7070b491b56c0a99e3fc6a06e4d64b0f7d4c20834fdd1a069c9b54a267deb
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121448383"
---
# <a name="extend-menus-and-commands"></a>Menüleri ve komutları genişletme
Komutlar, komutlara eylem ve işlem ekleme Visual Studio. Çoğu durumda komutlar menülerde veya araç çubuklarında görüntülenir. VSPackage proje şablonu, çok temel bir komutun nasıl uygulandığını gösterir. Biraz daha uzun ama yine de temel bir uygulama için [bkz. Menü komutuyla uzantı oluşturma.](../extensibility/creating-an-extension-with-a-menu-command.md)

 Komutlar, menüler Visual Studio araç çubukları hakkında daha fazla bilgi için bkz. [Komutlar, menüler ve araç çubukları.](../extensibility/internals/commands-menus-and-toolbars.md)

 Komutlar, menüler ve araç çubukları VSPackage projelerinin bir parçası olan *.vsct* dosyasında tanımlanır. Visual Studio IDE ve *.vsct* dosyası hakkında [bilgileri VSPackage'lar](../extensibility/internals/how-vspackages-add-user-interface-elements.md)kullanıcı arabirimi öğelerini ekleme konusunda bulabilirsiniz.

 Aşağıdaki konularda farklı türlerde komutların, menülerin ve araç çubuklarının nasıl ekli olduğu açık edilmektedir.

## <a name="in-this-section"></a>Bu bölümde
- [Yeni menü çubuğuna Visual Studio ekleme](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) Üst menü çubuğuna menü ekleme Visual Studio açıklar.

- [Menü öğelerine klavye kısayollarını bağlama](../extensibility/binding-keyboard-shortcuts-to-menu-items.md) Bir menü öğesinin klavye kısayolunu (CTRL + 3 gibi) nasıl ekley masaüstüne ekley olduğunu açıklar.

- [Menüye alt menü ekleme](../extensibility/adding-a-submenu-to-a-menu.md) Üst menüye alt menü eklemeyi açıklar.

- [Alt menüsüne en son kullanılan bir liste ekleme](../extensibility/adding-a-most-recently-used-list-to-a-submenu.md) En Son Kullanılanlar listesinin nasıl ekli olduğunu açıklar.

- [Yeniden kullanılabilir düğme grupları oluşturma](../extensibility/creating-reusable-groups-of-buttons.md) Komut öğelerinin birden çok menüye dahil edilecek şekilde nasıl gruplandır olduklarını açıklar.

- [Menü komutlarına simge ekleme](../extensibility/adding-icons-to-menu-commands.md) Hem araç çubuğunda hem de menüde bir komuta simge eklemeyi açıklar.

- [Menü komutunun metnini değiştirme](../extensibility/changing-the-text-of-a-menu-command.md) Bir menü öğesinin dinamik `TextChanges` olarak değiştirilebilir olması için bayrağının kullanımını açıklar.

- [Komutun görünümünü değiştirme](../extensibility/changing-the-appearance-of-a-command.md) Bir komutu dinamik olarak etkinleştirmeyi veya devre dışı bırakmayı açıklar.

- [Kullanıcı arabirimini güncelleştirme](../extensibility/updating-the-user-interface.md) Kullanıcı arabiriminin son değişiklikleri yansıtması için güncelleştirmenin nasıl zorlandığını açıklar.

- [Menü komutlarını yerelleştirme](../extensibility/localizing-menu-commands.md) Menü komutlarını yerelleştirmeyi açıklar.
